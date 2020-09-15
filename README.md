# DADA2 workflow

This repository contains the workflow/pipeline for DADA2 to process raw sequence data from Illumina paired-end sequencing runs.
In the given workflow, we process reads sequenced for the V4 region of the 16S rRNA.

In brief, the workflow was largely inspired by the [official DADA2 tutorials](https://benjjneb.github.io/dada2/tutorial.html). Our pipeline is mainly designed for big-data, however, it is similarly applicable to smaller datasets. 

We start by renaming sample file names, to simplify the names returned by our sequencing service. Followed by removing the primers using `cutadapt`.
After quality checking, the samples are run through the `dada` step on a plate basis with 'pseudo-pooling' enabled to ensure the retention of singleton reads within samples. Pooling only removes singletons within sampling campaigns. We cluster our amplicon sequence variants (ASVs) into 100% OTUs with `collapseNoMismatch`, as we are dealing with both DNA and RNA. The level of resolution of ASVs are believed to be too high to be able to match potential DNA and RNA reads of the same organism.

The original workflow was designed for samples that were split in several folders by years (e.g. 2015, 2016, 2017) and thus makes use of list frequently.
If your dataset's samples are all in one folder, please make use of the `single-folder version` that is provided for almost every step. They are not being evaluated by default, thus remove the `#` infront of the relevant lines.

---

This workflow was created in 2018 and has been in use for the following projects:

* La Romaine, Canada (responsible author: Masumi Stadler)
* L-Care, Canada (responsible author: Masumi Stadler)
* Pampean Lakes, Argentina (responsible author: Sofia Baliña)

---

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
