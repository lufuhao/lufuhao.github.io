title: RPKM(Reads Per Kilobase of exon model per Million mapped reads)简介
link: https://lufuhao.wordpress.com/2012/06/27/rpkmreads-per-kilobase-of-exon-model-per-million-mapped-reads%e7%ae%80%e4%bb%8b/
author: lufuhao
description: 
post_id: 1123
created: 2012/06/27 16:15:47
created_gmt: 2012/06/27 07:15:47
comment_status: open
post_name: rpkmreads-per-kilobase-of-exon-model-per-million-mapped-reads%e7%ae%80%e4%bb%8b
status: publish
post_type: post

# RPKM(Reads Per Kilobase of exon model per Million mapped reads)简介

##### Definition of RPKM

RPKM, Reads Per Kilobase of exon model per Million mapped reads, is defined in this way [[Mortazavi et al., 2008](http://www.clcbio.com/index.php?id=1330&manual=Bibliography.html#Mortazavi2008)]: ![$ \\emph{RPKM} = \\frac{\\emph{total exon reads}}{\\emph{mapped reads\(millions\)} \\times \\emph{exon length \(KB\)}}$](http://www.clcbio.com/manual/genomics/img79.gif) .

**Total exon reads**
    This is the number in the column with header **Total exon reads**in the row for the gene. This is the number of reads that have been mapped to a region in which an exon is annotated for the gene or across the boundaries of two exons or an intron and an exon for an annotated transcript of the gene. For eukaryotes, exons and their internal relationships are defined by annotations of type mRNA.
**Exon length**
    This is the number in the column with the header **Exon length**in the row for the gene, divided by 1000. This is calculated as the sum of the lengths of all exons annotated for the gene. Each exon is included only once in this sum, even if it is present in more annotated transcripts for the gene. Partly overlapping exons will count with their full length, even though they share the same region.
**Mapped reads**
    The sum of all the numbers in the column with header **Total gene reads**. The **Total gene reads** for a gene is the total number of reads that after mapping have been mapped to the region of the gene. Thus this includes all the reads uniquely mapped to the region of the gene as well as those of the reads which match in more places (below the limit set in the dialog in figure [18.127](http://www.clcbio.com/index.php?id=1330&manual=Defining_reference_genome_mapping_settings.html#fig:mrna_seq_step2)) that have been allocated to this gene's region. A gene's region is that comprised of the flanking regions (if it was specified in figure [18.127](http://www.clcbio.com/index.php?id=1330&manual=Defining_reference_genome_mapping_settings.html#fig:mrna_seq_step2)), the exons, the introns and across exon-exon boundaries of all transcripts annotated for the gene. Thus, the sum of the total gene reads numbers is the number of mapped reads for the sample. This number can be found in the RNA-seq report's table 3.1, in the 'Total' entry of the row 'Counted fragments'. (The term 'fragment' is used in place of the term 'read', because if you analyze paired reads and have chosen the 'Default counting scheme' it is 'fragments' that is counted, rather than reads (two reads in a pair will be counted as one fragment).
    

from [CLCBIO](http://www.clcbio.com/manual/genomics/Definition_RPKM.html)

\------------------------------------------------------------------------------------------------------------------------------------------------------------- RNA-seq是透过次世代定序的技术来侦测基因表现量的方法，在衡量基因表现量时，若是单纯以map到的read数来计算基因的表现量，在统计上是一件相当不合理事，因为在随机抽样的情况下，序列较长的基因被抽到的机率本来就会比序列短的基因较高，如此一来，序列长的基因永远会被认为表现量较高，而错估基因真正的表现量，所以Ali Mortazavi等人在2008年提出以RPKM在估计基因的表现量。 RPKM是将map到基因的read数除以map到genome的所有read数(以million为单位)与RNA的长度(以KB为单位)。 其公式为: 

![](http://lufuhao.files.wordpress.com/2012/06/01.png?w=300)

其中，total exon reads / mapped reads (millions) 可以视为所有read 数中有百分之多少是map 到这个基因，然后再除以基因长度，就可以某基因得到单位长度有百分之多少的total mapped read 有表现。 以下就用一个简化的例子来说明RPKM的运用方式与概念: 假设一基因体只有两个基因，一个9 KB，一个1 KB，如今有一sample，其map 到9 KB 的read 有18 million 个，map 到1 KB 的有2 million 个，如下图所示。 

![](http://lufuhao.files.wordpress.com/2012/06/02.png?w=300)

对于9 KB 的基因而言， Total exon reads=18 million Mapped reads=18+2=20 million Exon length=9 KB RPKM =18/(20*9)=0.1 对于1 KB 的基因而言， Total exon reads=2 million Mapped reads=18+2=20 million Exon length=1 KB RPKM =2/(20*1)=0.1 由此我们可以知道这两个基因表现量没有差别。 假设此时我们有另一个sample，其表现如下图所示: ![](http://lufuhao.files.wordpress.com/2012/06/03.png?w=300) 我们可以发现此sample中9 KB基因的read数明显比上一个sample少，如果我们计算RPKM可以得到RPKM = 9/((9+1)*9)=0.1，却与上一个sample相同，这可能是因为cDNA浓度较低或是其他sample备制过程的问题，造成整体read变少，但是对9 KB基因而言，其read数占所有read数的比例并没有发生改变，所以其表现量会和上一个sample相同。 

from [Public Library of Bioinformatics](http://www.plob.org/2011/10/24/294.html)