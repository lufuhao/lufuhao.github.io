title: Mummerplot running errors and solutions
link: https://lufuhao.wordpress.com/2017/09/13/mummerplot-running-errors-and-solutions/
author: lufuhao
description: 
post_id: 1405
created: 2017/09/13 00:25:27
created_gmt: 2017/09/12 15:25:27
comment_status: open
post_name: mummerplot-running-errors-and-solutions
status: publish
post_type: post

# Mummerplot running errors and solutions

Mummerplot is a excellent program and it has been a long time since last version 3.23 Here are some trouble-shooting:

  1. For large reference genome (>536,870,908 bp) 

Error: mummer: suffix tree construction failed: textlen=ddddddd larger than maximal textlen=536870908 **1.1 compile** Explanation: default compiled x86 version only support small genome (less than 536,870,908bp). If you have a larger one, you need to enable x64 version. So compile mummerplot again using **        $ make CPPFLAGS=" -O3 -DSIXTYFOURBITS"** **1.2 modify nucmer** And if you still get that error, you need to modify nucmer program, here is how-to     1. open 'nucmer' file using text editor like 'gedit'     2. jump to line 336-343

open(ALGO_PIPE, "$algo_path $algo $mdir -l $size -n $pfx.ntref $qry_file |")

                or $tigr->bail ("ERROR: could not open $algo_path output pipe $!");

open(CLUS_PIPE, "| $mgaps_path -l $clus -s $gap -d $ddiff -f $dfrac > $pfx.mgaps")

                or $tigr->bail ("ERROR: could not open $mgaps_path input pipe $!");

while ( <ALGO_PIPE> ) {

                print CLUS_PIPE

                or $tigr->bail ("ERROR: could not write to $mgaps_path pipe $!");

}

$err[0] = close(ALGO_FILE);

$err[1] = close(CLUS_PIPE);

** **   3. replace them with

    $err[0] = $tigr->runCommand ("$algo_path $algo $mdir -l $size -n $pfx.ntref $qry_file > $pfx.mummmer");

    if ( $err[0] != 0 ) {

        $tigr->bail("ERROR: Error: mummer output error\n");

    }

    unless (-s "$pfx.mummmer") {

        die "Error: mummer output error\n";

    }

    open(ALGO_FILE, "< $pfx.mummmer")

                or $tigr->bail ("ERROR: could not open $algo_path output file: $pfx.mummmer");

    open(CLUS_PIPE, "| $mgaps_path -l $clus -s $gap -d $ddiff -f $dfrac > $pfx.mgaps")

                or $tigr->bail ("ERROR: could not open $mgaps_path input pipe $!");

    while ( <ALGO_FILE> ) {

                print CLUS_PIPE

                or $tigr->bail ("ERROR: could not write to $mgaps_path pipe $!");

    }

    $err[0] = close(ALGO_FILE);

    $err[1] = close(CLUS_PIPE);

**  **  4.So use nucmer2 instead of nucmer      Explanation: nucmer use pipe to tranfer mummer output to feed mgaps as input. some times that is problematic. better to separate them. In this case there will be another output file: $prefix.mummer 1.3 replace mummer with e-mem [[[ OPTIONAL with care ]]]     IF IF IF IF you still have some problem, trying to use multi-thread version of mummer: E-MEM. But do it carefully.     5. install [e-mem](http://www.csd.uwo.ca/~ilie/E-MEM/), E-mem was reported to use multithreads and run in low memory requirements     6. create a file 'emem' in the same path as nucmer2/nucmer/mummerplot, and this is the content

> #!/bin/bash numthreads=1 ### edit this number to use multithreads /path/to/e-mem -t $numthreads "$@"