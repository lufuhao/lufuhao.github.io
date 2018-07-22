title: Tips for sequencing DNA
link: https://lufuhao.wordpress.com/2011/05/26/tips-for-sequencing-dna/
author: lufuhao
description: 
post_id: 603
created: 2011/05/26 00:15:42
created_gmt: 2011/05/25 15:15:42
comment_status: open
post_name: tips-for-sequencing-dna
status: publish
post_type: post

# Tips for sequencing DNA

##### Use clean DNA

The **cleanliness of the DNA is the most important factor in the success of automated DNA sequencing.** The DNA should be free of proteins, RNA, polysaccharides and genomic DNA. This can best be achieved by using either a commercial plasmid miniprep kit, or by sequencing a PCR amplified fragment. 

###### Use small sequencing reaction volumes

The high expense of the [DNA sequencing](http://www.nucleics.com/DNA_sequencing_tools/DNA_sequencing_tools.html) chemistries (BigDye) has encouraged many researchers to reduce the amount used from that recommended by ABI (ie 8 µl in a 20 µl reaction volume). The most common approach used is to dilute the sequencing chemistry. This unfortunately has the side effect of causing substrate limitations the DNA polymerase (ie the nucleotide concentration falls below the Km of the DNA polymerase), leading to short reads and "ski sloped" traces (ie traces which show a very rapid drop in raw channel signal intensity). If you wish to save on BigDye then it **is much better to reduce the reaction volume rather than BigDye concentration**. 

For more information on how you can reduce BigDye usage without dilution please visit our [dLUTE SEQ DNA sequencing reagent](http://www.nucleics.com/DNA_sequencing_tools/DNA-sequencing-dlute-seq.html) page. 

###### Don't use too much DNA in the sequencing reaction 

This is one of the most common mistakes made. You should aim to use no more than **25 ng of template times the length of the template in kilo bases.** For example, if you are sequencing a 3 kb plasmid with a 2 kb insert, you should aim to use 25ng x (3kb + 2kb) = 125 ng in total. 

###### Improving plasmid miniprep kits template quality 

The **sequence quality** obtainable from most commercial plasmid miniprep preparation kits can be **increased by performing a final ethanol precipitation of the purified plasmid DNA**. Using this step can remove leftover salts and wash buffer that may not have been removed fully during the kit DNA purification process. 

###### Sequence PCR products rather than plasmid templates

**Polymerase chain reaction templates tend to suffer less from sequencing problems than plasmids do. **There are a number of reasons for this. Firstly, PCR products are less likely to contain DNA polymerase inhibitors than plasmid DNA – after all if a DNA sample contains DNA polymerase inhibitors then it will not yield a PCR product. Secondly, PCR products are linear so that they are much easier to denature fully without template "snap back" occurring. The avoidance of template snap back can be a great help with high G+C templates and PCR products can be purified for sequencing very easily using [ExoI/SAP treatment](http://www.nucleics.com/DNA_sequencing_support/exonucleaseI-SAP-PCR-protocol.html). Finally, PCR allows modified nucleotides to be incorporated into the PCR template during amplification which can help to [overcome secondary structure problems](http://www.nucleics.com/DNA_sequencing_support/DNA-sequencing-hard-stops.html). 

###### Dry the template DNA before sequencing

One of the **simplest ways of reducing the volume** of a sequencing reaction is to **dry the DNA template down in the sequencing wells** before adding the sequencing chemistry and primers. Drying will not effect the DNA, and it allows the reaction volume to be significantly reduced, saving money and improving the quality of the resulting sequencing reaction. 

The easiest way to accomplish this is to put the DNA in the tube or tray and then place in a PCR machine set to 80˚C with the lid open. The DNA should dry in around 10 minutes. You can also add the primer at the same time and dry it down with the DNA. Just remember not to dry down large volumes containing reaction inhibitors like EDTA! 

###### Linearize high G+C plasmids before sequencing

High G+C (>60%) plasmids can be very difficult to sequence because the supercoiled template can rehybridize (the "snap back" problem) before the [sequencing DNA](http://www.nucleics.com/DNA_sequencing_tools/DNA_sequencing_tools.html) polymerase can complete the full extension. **Digestion of the plasmid template with a restriction enzyme before sequencing **can help over come this - just remember to not select a restriction enzyme that cuts between the [sequencing primer](http://www.nucleics.com/genome_sequencing_services/genome_sequencing_services.html) binding site and the region you want to sequence! 

###### Use a different sequencing clean-up protocol

A common cause of sequencing problems in the reaction clean-up. While many users are able to successfully clean up their reactions by ethanol precipitation, it is also the cause of many problems. Clean-ups by ethanol precipitation requires very precise ethanol concentrations and centrifugation times are used. If the ethanol concentration is too high then the left over sequencing chemistry (BigDye) is precipitated along with the sequencing products, resulting in [dye blobs at the start of the trace](http://www.nucleics.com/DNA_sequencing_support/DNA-sequencing-dye-blobs.html). If the ethanol concentration is too low then a [failed reaction (no signal)](http://www.nucleics.com/DNA_sequencing_support/DNA-sequencing-failed-reaction.html) results. The leeway between these two outcomes is only 2.5%! 

If you are having difficulties with your sequencing reaction clean-up you may want to consider trying the [phenol/butanol sequencing clean-up method](http://www.nucleics.com/DNA_sequencing_support/dna-sequencing-cleanup-protocol.html) or purchasing a commercial clean-up kit. 

###### Increase the number of sequencing thermo cycles

The intensity of sequencing signal is proportional to the number of thermo cycles performed. If you are finding that your signal intensity is just under the acceptable level, then increase your number of cycles can help. For example, if your current protocol use 25 cycles try using 35 or even 45 cycles. You can use up to 99 cycles without any problems. This is very a simple way of increasing signal strength. 

If you generally cycle your sequencing reaction overnight then this will not impact on the time required (ie rather than sitting at 4˚C for hours the reaction will be generating more template).