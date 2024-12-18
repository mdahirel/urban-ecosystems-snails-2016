[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.14508705.svg)](https://doi.org/10.5281/zenodo.14508705)

This is a repository containing the raw data for the 2016 paper:  "Dispersal-related traits of the snail _Cornu aspersum_ along an urbanisation gradient: maintenance of mobility across life stages despite high costs" (<https://doi.org/10.1007/s11252-016-0564-y>), as well as a 2024 re-appraisal/re-analysis of these data.

## A few notes
 
 The impetus for archiving these more than 8 years after the fact came from a data request email. Looking through my old files to fulfill this request was sobering, as I had to face the fact that my data management practices during my PhD thesis were sub-par, to say the least (on the positive side, I definitely learned _a lot_ since then).
 I was still able to relocate the original messy spreadsheets, tidy them and re-run the analyses, recovering the model results relatively easily.
 
 Nonetheless, some explanations/remarks to those who would look through these data and have questions in some places:

### No individual ID?

Exploring the data, you might see that there are no individual snail ID connecting the `data/exploration.csv`, `data/perception.csv` and `data/dissection.csv` files. This is in retrospect a massive blunder, as connecting exploration to morphology could be useful in future analyses, and this would have helped clarify some of the inconsistencies described below. Contemporary side notes suggest we did mark them, but many marks were lost/faded too fast to carry over from one experiment to the next (plausible, as we as a research group only landed on a method that was both individualised, **fast** and with limited mark loss later), so even surviving marks were thought not worth noting.
  
### Life stages reveal slight inconsistencies with published methods

Based on the description of the Methods in the published paper, the `data/dissection.csv` file should be the one containing all the snails, and the other two should be subsets/samples of it, but there are inconsistencies/mismatches (they can be explored using e.g. the `table()` function in R to summarise datasets by site, stage or both):

- the `exploration` dataset has sites where it has more individuals, overall or of one life stage, than the `dissection` dataset
  
- one site is present from the `exploration` dataset and not the other two

- in some sites, while the overall numbers are consistent, there are more adults and less subadults is `dissection` that there should be based on the other two datasets

**Each dataset accurately reflects the work that was done at each step and is consistent with the paper as originally published, the re-analysis further confirms that**, but the complications arise when attempting to match them with each other (especially in the absence of individual marks, see above). From memories and fragmentary notes (including the draft version of the article in my PhD thesis), the best explanation is as far as I can tell is as follows: 

- An original set of 148 snails was collected; these are the ones from the `exploration` dataset, as seen in the corresponding draft chapter included in my PhD thesis (https://theses.fr/2014REN1S068), which is directly derived from co-first author Alice Séguret's Master thesis

- A small number of snails died between experiments, and some newly captured ones were added. The net balance was 10 snails, leading to the 158 snails in the `dissection` dataset. The clearest support for that is one site that has one snail in `exploration` (chronologically the earliest experiment), but is absent from subsequent datasets.

- Mismatches in stage arise from two sources. First, snails' stages were rescored for each experiment, and there might be some assignment error/disagreements, especially in snails close to maturity. Second, some snails became adults _during_ the study; many "inconsistencies" between datasets are sites with less subadults in the final `dissection` dataset than the previous ones

This means that the "total" number of snails (and their average shell size by stage) in the Methods of the published paper refers only to the `dissection` dataset, and may not be an accurate reflection of all the snails that were actually used. While I expect the discrepancies to be minor, I nonetheless apologize for that on behalf of all authors.

### Re-running the analyses

For the `R/analysis.qmd` code in this repository, I re-ran the **exact same models** as in my original messy, ugly code. I was therefore able to recover the exact same model results. For the post-hoc plots though, I used the benefits of 8 years of knowledge to get confidence intervals in simpler and more accurate ways (if only because my original code was badly stitched together and barely readable). As a results, plots and confidence intervals may look slightly different than the original paper (besides the switch to `ggplot`); conclusions are nonetheless the same.

I did run some new models _in addition_ to the original ones for the perceptual range; see the notes in the `R/analysis.qmd` files for details.

See also the notes in `R/analysis.qmd` for an overview of the variables in each data file.
