title: Full_lengther_NEXT v0.0.8 database setup and run
link: https://lufuhao.wordpress.com/2015/11/13/full_lengther_next-v0-0-8-database-setup-and-run/
author: lufuhao
description: 
post_id: 1369
created: 2015/11/13 02:27:22
created_gmt: 2015/11/12 17:27:22
comment_status: open
post_name: full_lengther_next-v0-0-8-database-setup-and-run
status: publish
post_type: post

# Full_lengther_NEXT v0.0.8 database setup and run

Full_lengther_next is an excellent program to test if you EST assembly are full-length or not, or test how much percentage it can get.

for the 1st step of analysis, you probably needs a database for the program to blast+. the built-in script ‘download_fln_dbs.rb’ is designed to setup the database for you. Basically, the script would download taxonomy database from [uniprot](ftp://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/taxonomic_divisions/), splice database from uniprot, and non-coding RNA database from [SCBI](http://www.scbi.uma.es/downloads/FLNDB/ncrna_fln_100.fasta.zip), filter out the non-full-length sequences, and make BLAST+ database for BLAST+ program. Unfortunately, the script would report NET::FTP or gzip problems. 

I ran ‘download_fln_dbs.rb’, and got error like: 

> 550 Permission denied. (Net::FTPPermError)

This is probably duo to errors either from ruby NET::FTP and uniprot FTP sever. (Sorry I am a PERLer, NOT a RUBYer).

and if you get a gzip error,

> gzip *.gz not found

probably you need to change you environment variable BLASTDB in ~/.bashrc to a format like: 

> BLASTDB=/path/to/your/blastdb/

The last letter ‘/’is needed to find /path/to/your/blastdb/*.gz files downloaded from uniprot, or else if will find /path/to/your/blastdb*.gz files.

 

OK, let’s start to setup half-manually:

 

**1\. Setup environment variable BLASTDB if you did NOT do this**

to test if you already had one:

> $ echo $BLASTDB

If it returns a path like /path/to/your/blastdb, ignore this step

> $ vim ~/.bashrc
> 
> #add one more line at the end of file
> 
> #press letter i or a
> 
> #NOTE: change /path/to/your/blastDB/ to a specified path depending on your machine, like: $HOME/blastdb
> 
> export BLASTDB=/path/to/your/blastDB/
> 
> #Esc and :wq in vim to save the changes
> 
> #log out-and-in or use source ~/.bashrc to take effect
> 
> #It seems no effect just using shell ‘export BLASTDB=/path/to/blastdb, no idea why. I knew it will detect $ENV[‘BLASTDB’], but it still  shows the path in ./.bashrc

** 2\. Download necessary files from uniprot:**

> $ mkdir –p $BLASTDB
> 
> $ cd $BLASTDB
> 
> $ wget ftp://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/taxonomic_divisions/uniprot_trembl_plants.dat.gz
> 
> $ wget <ftp://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/taxonomic_divisions/uniprot_sprot_plants.dat.gz>
> 
> $ wget <ftp://ftp.uniprot.org//pub/databases/uniprot/current_release/knowledgebase/complete/uniprot_sprot_varsplic.fasta.gz>
> 
>  
> 
> #setup non-coding database
> 
> $ mkdir $BLASTDB/nc_rna_db
> 
> $ cd $BLASTDB/nc_rna_db
> 
> $ wget <http://www.scbi.uma.es/downloads/FLNDB/ncrna_fln_100.fasta.zip>
> 
> $ unzip ncrna_fln_100.fasta.zip 
> 
> $ mv ncrna_fln_100.fasta ncrna_fln_100.fasta.oldID 
> 
> #change seqids 
> 
> $ perl -ne 'BEGIN {$seqid=ncrna0000000001;} if (/^>/) {chomp; s/^>//; $_=">".$seqid." ".$_; print $_, "\n";$seqid++;}else {print;}' ncrna_fln_100.fasta.oldID > ncrna_fln_100.fasta 
> 
> # make blast DB 
> 
> $ makeblastdb -in ncrna_fln_100.fasta -dbtype nucl -parse_seqids

3\. find download_fln_dbs.rb  and edit:

> # The script should not be detected using which cmd
> 
> #it either locates in /var/lib/gems/*/gems/full_lengther_next-0.0.8/bin/ or $HOME/.gem/ruby/*/gems/full_lengther_next-0.0.8/bin/
> 
> #open it with editor:
> 
> #go to line 202
> 
> my_array = ["human","fungi","invertebrates","mammals","plants","rodents","vertebrates"]
> 
> #Add # from left, to make it inactive
> 
> #my_array = ["human","fungi","invertebrates","mammals","plants","rodents","vertebrates"]
> 
> #and edit the following line:
> 
> # my_array = ["plants","human"]
> 
> #Remove # and unnecessary species, like:
> 
> my_array = ["plants"