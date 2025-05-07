# DICOM-BIDS Analysis
Comprehensive MRI DICOM and BIDS data analyses 


## 📂 MRI Data Overview

```text
MRI Data
├── 1. Structural (Anatomical) Scans
│   ├── T1-weighted (T1w)
│   │   ├── (2 - T1w_MPR): Initial T1w scan
│   │   └── 3 - T1w_MPR: Normalized, convert this one
│   ├── T2-weighted (T2w)
│   │   ├── (4 - T2w_SPC): Initial T2w scan
│   │   └── 5 - T2w_SPC: Normalized, convert this one
│   ├── High-Resolution T2w for Hippocampus
│   │   ├── (6 - TSE_HiResHp): Raw HiRes scan
│   │   └── 7 - TSE_HiResHp: Normalized, convert this one
│   └── FLAIR (Fluid-Attenuated Inversion Recovery)
│       ├── (27 - 32_FLAIR_1mm_ipat2_ORIG): Raw series
│       └── 28 - 32_FLAIR_1mm_ipat2: Normalized, convert this one
│
├── 2. Functional MRI (fMRI)
│   ├── Language Task: Sentence Completion
│   │   ├── (8 - Sentence_Completion_SBRef): Structural reference for motion correction
│   │   └── 9 - Sentence_Completion: Main functional run (~100 volumes)
│   │   └── (10 - PhysioLog): Physiological recording, not converted to BIDS
│   ├── Language Task: Word Generation
│   │   ├── (11,13 - Other scans): Auxiliary
│   │   └── 12 - Word_Generation: Main functional run
│   └── Fieldmaps (for fMRI distortion correction)
│       ├── 14 - SpinEchoFieldMap_AP
│       └── 15 - SpinEchoFieldMap_PA
│
├── 3. Diffusion MRI (dMRI)
│   ├── Phase Encoding Direction: AP
│   │   ├── (16 - dMRI_dir98_AP_SBref): Structural reference
│   │   └── 17 - dMRI_dir98_AP: Main diffusion run (~99 volumes)
│   │   └── (18 - PhysioLog): Not required
│   ├── Phase Encoding Direction: PA
│   │   ├── (19,21 - Others): Auxiliary
│   │   └── 20 - dMRI_dir99_PA: Second diffusion run (~100 volumes)
│   └── (22-26 - Processed): Skip
│
├── 4. Perfusion (ASL)
│   ├── (29-33 - Localizer): Not required
│   ├── 34 - mbPCASLhr_PA: Main ASL sequence (includes M0 image)
│   └── Fieldmaps (for ASL distortion correction)
│       ├── 35 - SpinEchoFieldMap_AP
│       └── 36 - SpinEchoFieldMap_PA
│
└── (1 - Localizer): Planning scan, not required

