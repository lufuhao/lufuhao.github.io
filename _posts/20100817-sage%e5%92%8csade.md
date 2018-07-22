title: SAGE和SADE
link: https://lufuhao.wordpress.com/2010/08/17/sage%e5%92%8csade/
author: lufuhao
description: 
post_id: 63
created: 2010/08/17 08:44:43
created_gmt: 2010/08/17 08:44:43
comment_status: open
post_name: sage%e5%92%8csade
status: publish
post_type: post

# SAGE和SADE

**基因表达系列分析（Serial Analysis of Gene Expression，SAGE）**

基因表达系列分析（Serial Analysis of Gene Expression，SAGE）技术在理论上来说可以检测到一个细胞内所有转录体的表达，而且可以给每一个转录体定量，不管它是低丰度还是高丰度。 SAGE和基因芯片技术一样，具有高通量、平行性检测细胞内基因表达谱的特点。但SAGE可在未知任何基因或EST序列的情况下对靶细胞进行研究，这一点是基因芯片技术所不具备的。 

基因表达系列分析（Serial Analysis of Gene Expression，SAGE）是1995年Velculescu提出的，是近几年来发展起来的一种快速分析基因表达信息的技术。它通过快速和详细分析成千上万个EST来寻找出表达丰度不同的SAGE标签序列，从而接近完整地获得基因组的表达信息。它的显著特点是能够大量获取基因组范围基因表达的类别与丰度。SAGE技术已成功地应用于特异组织或细胞的转录组研究和mRNA群体间差异表达基因的鉴定。基因表达系列分析（SAGE）以构建能独特代表基因转录本序列的标签（tag）为宗旨，标签长度约9～12 bp，同一tag 在某组织中出现的频度反应了该tag 所代表基因在这种组织中的表达丰度。目前，NCBI 通过Internet 操作平台提供了多种来源的肿瘤组织、细胞系及相应正常组织近100个SAGE 文库数据，为能找到代表性SAGEtag 的基因进行多组织与细胞间表达谱量化分析、比较、甚至功能推测提供了良好的“实验”材料和环境。 

SAGE技术的理论基础：①一段来自于任一转录本特定区域的“标签”（Tag），即长度仅9-14bp的短核苷酸序列，就已包含足够的信息以特异性地确定该转录本。例如：一个9碱基的序列能有四的9次方，即262144种不同的排列组合，而人类基因组据估计仅编码80000种转录本，因此在理论上每一个9碱基标签就能够代表一种转录本的特征序列。②如果将短片段标签相互连接、集中形成长的DNA分子，则对该克隆进行测序将得到大量连续的单个标签，并能以连续的数据形式进行处理，这样就可对数以千计的mRNA转录本进行批量分析。③各转录本的表达水平可以用特定标签被测得的次数定量。 

SAGE区别于差异显示、消减杂交等其它技术的主要特点是可用于寻找那些较低丰度的转录物，最大限度地收集基因组的基因表达信息，这使之成为从总体上全面研究基因表达、构建基因表达图谱的首选策略。并可在此基础上，发现新的基因。 

SAGE还可用于在不同环境、不同生理状态及不同生长阶段的细胞和组织表达图谱构建，对不同状态下基因表达水平的定量或 

**SADE: a microassay for serial analysis of gene expression**

**High-throughput methods for quantitative analysis of gene expression**

Several methods are now available for monitoring gene expression on a genomic scale. These include DNA microarrays and macroarrays, expressed sequence tag (EST) determination, and the serial analysis of gene method. Such methods have been designed, and are still used, for analyzing macroamounts of biological material (1-5 µg of poly(A) mRNAs, i.e. -107 cells). However, mammalian tissues consist of several different cell types with specific physiological functions and gene expression patterns. Obviously, this makes intricate the interpretation of large-scale expression data in higher organisms. It is therefore most desirable to set out methods suitable for the analysis of defined cell populations. 

**Protocol outline**

SAGE was first described by Velcuescu et al. in 1995, and rest on three principles which have now been all corroborated experimentally: (i) short nucleotide sequence tags (10 bp) are long enough to be specific of a transcript, especially if they are isolated from a defined portion of each transcript; (ii) concatenation of several tags within a single DNA molecule greatly increases the throughput of data acquisition; (iii) the quantitative recovery of transcript-specific tags allows to establish representative gene expression profiles. 

Figure1. modified from the original studies of Velcuescu et al., summarizes the different steps of SADE, a Sage Adaptation for Downsized Extracts. Briefly, mRNAs are extracted using oligo(dT)25 covalently bound to paramagnetic beads. Double strands (ds) cDNA is synthesized from mRNA using oligo(dT)25 as primer for the first strand synthesis. The cDNA is then cleaved using a restriction endonuclease (anchoring enzyme: SAu3AI) with a 4-bp recognition site. As such an enzyme cleaves DNA molecules every 256 bp (44) on average, virtually all cDNA are predicted to be cleaved at least once. The 3′ end of each cDNA is isolated using the property of the paramagnetic beads and divided in half. Each of the two aliquots is ligated via the anchoring enzyme restriction site to one of the two linkers containing a type IIS recognition site (tagging enzyme: BsmFI) and a priming site for PCR amplification. Type IIS restriction endonucleases display recognition and cleavage sites separated by a defined length (14 bp for BsmFI), irrespective of the the intercalated sequence. Digestion with the type IIS restriction enzyme thus releases linkers with an anchored short piece of cDNA, corresponding to a transcript-specific tag. After blunt ending of tags, the two aliquots are linked together and amplified by PCR. As all targets are of the same length (110 bp) and are amplified with the same primers, potential distortions introduced by PCR are greatly reduced. Furthermore, these distortions can be evaluated, and the data corrected accordingly. Ditags present in the PCR products are recovered through digestion with the anchoring enzyme and gel purification, then concatenated and cloned. 

![](http://img.blog.163.com/photo/oJGYIS0F98FcdcvExLGv4g==/438819488693434051.jpg)

**Differences between SAGE and SADE**

In the SAGE method, mRNAs are isolated using conventional methods, then hybridized to biotinylated oligo(dT) for cDNA synthesis. After cleavage with the anchoring enzyme, the biotinylated cDNA fraction (3′ end) is purified by binding to streptavidin beads. In the SADE method, mRNAs are directly isolated from the tissue lysate through hybridization to oligo(dT) covalently bond to magnetic beads. Then, all steps of the experiment (until step 3 of protocol 5) are performed on magnetic beads. This procedure saves time for the initial part of the experiment and, more importantly, provides better recovery. Quantitative analysis of the cDNA amounts available for library construction revealed dramtic differences between SAGE and SADE. With the SAGE method, starting from 500 mg tissue we obtained 1.7 µg of cDNA, and only 4 ng were able to bind to streptavidin beads after _Sau_3AI digestion. With the SADE method, strarting from 250 mg of tissue, 3.2 µg of cDNA were synthesized on beads, and 0.5 µg remained bound after _Sau_3AI cleavage. The increased yield of SADE (×250) explains our success in constructing libaries from as few as 30000 cells. Using either biotinylated oligo(dT) designed by us or obtained from mRNA purification kits, we always get poor cDNA recoveries. This may be explained by the fact that the binding of biotinylated DNA can be altered by several parameters, such as the amount of free biotin and the presence of phenol, the length and composition of the biotinylated DNA fragments, and the length of the spacer between the oligo(dT) and the biotin molecule. 

Another important difference between SAGE and SADE concerns the selected anchoring enzyme. Although any restriction enzyme with a 4-bp restriction site could serve as an anchoring enzyme, _Sau_3AI was preferred to NlaIII (7-10) or other enzymes in our studies. Several cDNA libraries used for large-scale sequencing are constructed by vector priming, followed by cDNA cleavage with MboI (an isoschizomer of _Sau_3AI which does not cut the vector (methylated) DNA), and circularization. SADE tags therefore correspond to the cDNAs 5′ end of these libraries, which enables to use more efficiently EST databases to analyse our data.