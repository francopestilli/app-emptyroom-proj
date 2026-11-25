# Compute SSP from raw data (emptyroom)

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Computes signal-space projection (SSP) vectors from empty-room MEG with MNE-Python compute_proj_raw and saves the projectors with a plot.**

Runs mne.compute_proj_raw on continuous data (designed for empty-room recordings) to capture environmental noise, with configurable vector counts per sensor type and time window. Apply the resulting projectors to subject recordings to remove that noise.

| | |
|---|---|
| 📥 **Inputs** | `neuro/meg/fif` |
| 📤 **Outputs** | `neuro/meeg/mne/projection` · `raw` |
| 🐳 **Container** | `brainlife/mne:0.23dev` |
| ⚙️ **Resources** | 8 CPUs |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.645](https://doi.org/10.25663/brainlife.app.645) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `raw01` | `neuro/meg/fif` | yes | Continuous MEG recording (FIF), typically empty room. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `out_dir` | `neuro/meeg/mne/projection` | Emptyroom projector |
| `out_figs` | `raw` | Plot of the empty-room projectors (PNG). |

<details>
<summary><b>⚙️ Parameters</b> (10)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `start` | number | `0` | Time (in sec) to start computing SSP. |
| `stop` | number |  | Time (in sec) to stop computing SSP. Default (empty): None -> will go to the end of the file. |
| `duration` | number | `1` | Duration (in sec) to chunk data into for SSP If duration is None, data will not be chunked. |
| `n_grad` | number | `2` | Number of vectors for gradiometers. |
| `n_mag` | number | `2` | Number of vectors for magnetometers. |
| `n_eeg` | number | `0` | Number of vectors for EEG channels. |
| `reject` | string |  | Epoch rejection configuration (see Epochs). |
| `flat` | string |  | Epoch flat configuration (see Epochs). |
| `n_jobs` | number | `1` | The number of jobs to run in parallel. If -1, it is set to the number of CPU cores. Requires the joblib package. None (default) is a marker for ‘unset’ that will be interpreted as n_jobs=1 (sequential execution) unless the call is performed under a joblib.parallel_backend() context manager that sets another value for n_jobs. Number of jobs to use to compute covariance. |
| `meg` | enum | `separate` | Can be ‘separate’ (default) or ‘combined’ to compute projectors for magnetometers and gradiometers separately or jointly. If ‘combined’, n_mag == n_grad is required and the number of projectors computed for MEG will be n_mag. Options: `separate`, `combined`. |

</details>

📚 **References used by this App:**
- Avesani P, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. Sci Data 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)
- Gramfort A, et al. MEG and EEG data analysis with MNE-Python. Front Neurosci 7:267 (2013). [doi:10.3389/fnins.2013.00267](https://doi.org/10.3389/fnins.2013.00267)

<!-- brainlife-app:end -->

[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-bl.app.584-blue.svg)](https://doi.org/10.25663/brainlife.app.584)

Brainlife App to compute SSP (signal-space projection) vectors on continuous data using MNE-Python function `mne.compute_proj_raw` 
Specially thought to identify emptyroom noise.

## Authors
- Guiomar Niso (guiomar.niso@ctb.upm.es)
- Saeed Zahran (saeedzahran@hotmail.com)

## Citations
We kindly ask that you cite the following articles when publishing papers and code using this code. 

*- brainlife.io Publishing and Apps:*

Avesani, P., McPherson, B., Hayashi, S. et al. **The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services**. Sci Data 6, 69 (2019). https://doi.org/10.1038/s41597-019-0073-y

*- MNE-Python package:*

Gramfort A, Luessi M, Larson E, Engemann DA, Strohmeier D, Brodbeck C, Goj R, Jas M, Brooks T, Parkkonen L, and Hämäläinen MS. **MEG and EEG data analysis with MNE-Python**. Frontiers in Neuroscience, 7(267):1–13, 2013. https://doi.org/10.3389/fnins.2013.00267

## Funding Acknowledgement
brainlife.io is publicly funded and for the sustainability of the project it is helpful to Acknowledge the use of the platform. We kindly ask that you acknowledge the funding below in your publications and code reusing this code.

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://grantome.com/grant/NIH/R01-EB030896-01)

#### MIT Copyright (c) 2021 brainlife.io The University of Texas at Austin and Indiana University
