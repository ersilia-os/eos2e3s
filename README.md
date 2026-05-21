# Antimicrobial activity prediction against Pseudomonas aeruginosa from public ChEMBL data

Bioactivity prediction of growth inhibition in Pseudomonas aeruginosa, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (percent inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.



## Information
### Identifiers
- **Ersilia Identifier:** `eos2e3s`
- **Slug:** `antimicrobial-activity-paeruginosa`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Antimicrobial resistance`, `Pneumonia`
- **Target Organism:** `Pseudomonas aeruginosa`
- **Tags:** `Gram-negative bacteria`, `ESKAPE`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `22`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Pseudomonas aeruginosa from 21 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 21 sub-models. Recommended threshold: 0.943. |
| individual_mic | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4296187 (MIC; cutoff 20 uM; n=1034). Recommended threshold: 0.881. |
| merged_mic_decoys_a | float | high | Probability from sub-model trained on MIC measurements merged across 9 ChEMBL assays (cutoff 10 uM; n=2300 incl. decoys). Recommended threshold: 0.876. |
| merged_inhibition_decoys | float | high | Probability from sub-model trained on inhibition % measurements merged across 8 ChEMBL assays (cutoff 25 %; n=1100 incl. decoys). Recommended threshold: 0.811. |
| merged_ic50_decoys | float | high | Probability from sub-model trained on IC50 measurements merged across 3 ChEMBL assays (cutoff 20 uM; n=1080 incl. decoys). Recommended threshold: 0.836. |
| merged_mic_decoys_d | float | high | Probability from sub-model trained on MIC measurements merged across 4 ChEMBL assays (cutoff 10 uM; n=1010 incl. decoys). Recommended threshold: 0.890. |
| merged_iz_decoys_a | float | high | Probability from sub-model trained on IZ measurements merged across 7 ChEMBL assays (cutoff 10 mm; n=920 incl. decoys). Recommended threshold: 0.885. |
| merged_mic_decoys_c | float | high | Probability from sub-model trained on MIC measurements merged across 5 ChEMBL assays (cutoff 10 uM; n=830 incl. decoys). Recommended threshold: 0.861. |
| merged_mic_decoys_b | float | high | Probability from sub-model trained on MIC measurements merged across 9 ChEMBL assays (cutoff 20 uM; n=660 incl. decoys). Recommended threshold: 0.817. |
| merged_activity_decoys | float | high | Probability from sub-model trained on single-point % activity measurements merged across 8 ChEMBL assays (cutoff 50 %; n=590 incl. decoys). Recommended threshold: 0.861. |

_10 of 22 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`

### Resource Consumption


### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos2e3s
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos2e3s
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
