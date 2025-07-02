# Motif Enrichment Analysis Plots

This directory contains all the plots generated from the motif enrichment analysis on mononucleosomes for the OSKM transcription factors (OCT4, SOX2, KLF4, cMYC).


---

## Plot Descriptions

### Heatmaps (`heatmaps/`)

**Purpose:**  
Visualize motif enrichment patterns around nucleosome dyads for each transcription factor in open and closed chromatin.

**File Naming Convention:**  
`{TF}_{chromatin_state}_nearest_merged_nucs_{motif}_{match_percent}_ATAC_sorted.ps/png`

#### Available Heatmaps:

| File Name                                                                 | TF    | Chromatin State | Motif   | Match Threshold | Description                                                        |
|---------------------------------------------------------------------------|-------|-----------------|---------|-----------------|--------------------------------------------------------------------|
| OSKM48hrOCT4_open20_nearest_merged_nucs_TGWATD_85percent_match_ATAC_sorted | OCT4  | Open            | TGWATD  | 85%             | OCT4 motif enrichment around nucleosomes in open chromatin         |
| OSKM48hrOCT4_closed20_nearest_merged_nucs_TGWATD_85percent_match_ATAC_sorted | OCT4  | Closed          | TGWATD  | 85%             | OCT4 motif enrichment around nucleosomes in closed chromatin       |
| OSKM48hrSOX2_open20_nearest_merged_nucs_HTTTRT_95percent_match_ATAC_sorted | SOX2  | Open            | HTTTRT  | 95%             | SOX2 motif enrichment around nucleosomes in open chromatin         |
| OSKM48hrSOX2_closed20_nearest_merged_nucs_HTTTRT_95percent_match_ATAC_sorted | SOX2  | Closed          | HTTTRT  | 95%             | SOX2 motif enrichment around nucleosomes in closed chromatin       |
| OSKM48hrKLF4_open20_nearest_merged_nucs_GGGYGK_85percent_match_ATAC_sorted | KLF4  | Open            | GGGYGK  | 85%             | KLF4 motif enrichment around nucleosomes in open chromatin         |
| OSKM48hrKLF4_closed20_nearest_merged_nucs_GGGYGK_85percent_match_ATAC_sorted | KLF4  | Closed          | GGGYGK  | 85%             | KLF4 motif enrichment around nucleosomes in closed chromatin       |

**How to Read Heatmaps?**
- **X-axis:** Position relative to nucleosome dyad (±500 bp)
- **Y-axis:** Nucleosome regions sorted by ATAC-seq signal (highest to lowest)
- **Color Scale:** Blue (low motif score) to Red (high motif score)
- **White:** No motif match

---

### Profiles (`profiles/`)

**Purpose:**  
Show average motif occurrence profiles around nucleosome dyads for specific TF binding sites.

**File Naming Convention:**  
`OSKM48hrallOSKM_{chromatin_state}_O_nucs_{motif}_{match_percent}matchmotif_{window}bp_window.ps/png`

#### Available Profiles:

| File Name                                                                 | TF    | Chromatin State | Motif   | Match Threshold | Window | Description                                                        |
|---------------------------------------------------------------------------|-------|-----------------|---------|-----------------|--------|--------------------------------------------------------------------|
| OSKM48hrallOSKM_open20_O_nucs_TGWATD_85percentmatchmotif_400bp_window     | OCT4  | Open            | TGWATD  | 85%             | ±200bp | Motif profile for OCT4 alone-bound nucleosomes in open chromatin   |
| OSKM48hrallOSKM_closed20_O_nucs_TGWATD_85percentmatchmotif_400bp_window   | OCT4  | Closed          | TGWATD  | 85%             | ±200bp | Motif profile for OCT4 alone-bound nucleosomes in closed chromatin |

**How to read Profiles?**
- **X-axis:** Position relative to nucleosome dyad (±200 bp)
- **Y-axis:** Average motif occurrence score
- **Red line:** Positive strand motif matches
- **Blue line:** Negative strand motif matches
- **Peaks:** Indicate preferred motif positions relative to nucleosome dyad

---

## Technical Details

- **Nucleosomes** within 80bp of TF binding sites were analyzed.
- **ATAC-seq signal threshold** of 20 was used to classify open vs closed chromatin.
- **Motif matrices** were derived from MEME/DREME analysis.
- **Reverse complement motifs** were used for negative strand analysis.

---

# Convert to PNG
```
gs -dNOPAUSE -dBATCH -sDEVICE=pngalpha -r600 -sOutputFile="output.png" "input.ps"
```