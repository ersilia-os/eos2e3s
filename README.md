# Antimicrobial activity prediction against Pseudomonas aeruginosa from public ChEMBL data

Bioactivity prediction of growth inhibition in Pseudomonas aeruginosa, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (Inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-07-22.

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
- **Output Dimension:** `15`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Pseudomonas aeruginosa from 14 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 14 sub-models. Recommended threshold: 0.848. |
| chembl_single_point_0 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 185 assays (2222 compounds). Recommended threshold: 0.851. |
| chembl_single_point_1 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 61 assays (859 compounds). Recommended threshold: 0.631. |
| chembl_single_point_2 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 86 assays (852 compounds). Recommended threshold: 0.734. |
| chembl_single_point_3 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 56 assays (815 compounds). Recommended threshold: 0.656. |
| chembl_single_point_4 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 63 assays (739 compounds). Recommended threshold: 0.587. |
| chembl_single_point_5 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 29 assays (418 compounds). Recommended threshold: 0.594. |
| chembl_dose_response_0 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 902 assays (10556 compounds). Recommended threshold: 0.838. |
| chembl_dose_response_1 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 753 assays (9559 compounds). Recommended threshold: 0.745. |
| chembl_dose_response_2 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 486 assays (5179 compounds). Recommended threshold: 0.701. |

_10 of 15 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos2e3s](https://hub.docker.com/r/ersiliaos/eos2e3s)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos2e3s.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos2e3s.zip)

### Resource Consumption
- **Model Size (Mb):** `248`
- **Environment Size (Mb):** `7208`
- **Image Size (Mb):** `7467.75`

**Computational Performance (seconds):**
- 10 inputs: `57.6`
- 100 inputs: `57.37`
- 10000 inputs: `1607.66`

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
