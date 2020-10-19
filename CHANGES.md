# Modifications

### Non-Gcloud modifications:
Since localization_optional attribute doesn't work on all backends, pipeline fails due to missing indices (once on BAM and once on VCF stage). Since cromwell is smart and can pair the inidices as long as they are staged, it is solved by including indices in the inputs (but without using them in the command).

### Optional contamination check :
For small targeted panels contamination checking loci might be missed altogether. The contamination subsetting task fails with no output intervals. This can be avoided by setting the added GenerateSubsettedContaminationResources.pipefail to false. Since this is an edgecase, this parameter defaults to true to catch unexpected errors.
