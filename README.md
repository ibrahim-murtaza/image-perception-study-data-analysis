# Image Perception Study - Data Analysis

This repository contains the data analysis code for the research paper:

**"User Perception of AI Generated Images"**  
*Authors: Ibrahim Murtaza, Khadija Imran, Xeerak Azhar, Momina Sajid*  
*Institution: Lahore University of Management Sciences (LUMS)*  
*Course: CS 6303 - Topics in Large Language Models*

## Overview

This study investigates how content labels ("AI-Generated" vs "Human-Created") affect user perception, even when labels are incorrect. We conducted a within-subjects experiment with 117 participants who each rated 4 images across all combinations of true origin and label accuracy.

**Key Finding**: Labels completely override visual perception—images labeled "AI-Generated" receive lower ratings regardless of actual origin, while those labeled "Human-Created" are rated higher, even when AI-generated.

## Repository Structure

```
├── merged_data.csv                     # Primary dataset (468 observations)
├── image_perception_analysis.ipynb     # Main statistical analysis script
├── figures/                            # Generated visualizations
│   ├── all_conditions_comparison.png
│   ├── interaction_plot.png
│   ├── image_level_effects.png
│   ├── dv_distributions.png
│   ├── effort_sharing_correlation.png
│   ├── image_origin_effect.png
│   ├── gender_moderation.png
│   └── familiarity_moderation.png
├── summary_statistics.csv       # Descriptive statistics by condition
└── results_summary.txt          # Complete analysis output
```

## Dataset Description

**File**: `merged_data.csv`

- **Observations**: 468 (117 participants × 4 images each)
- **Design**: Within-subjects (each participant saw all 4 conditions)

### Key Variables

| Variable | Description | Values |
|----------|-------------|--------|
| `email` | Participant identifier (anonymized) | String |
| `trial_num` | Image sequence number | 1-4 |
| `image_name` | Specific image shown | e.g., "stars", "trump", "flood" |
| `true_origin` | Actual image source | AI, Real |
| `label_shown` | Label displayed to participant | "AI-Generated", "Human-Created" |
| `label_correct` | Whether label matched origin | True, False |
| `condition_code` | Experimental condition | TP, TN, FP, FN |
| `effort_rating` | Perceived effort (1-7 scale) | 1 = Very little, 7 = Very high |
| `sharing_rating` | Sharing intent (1-7 scale) | 1 = Very unlikely, 7 = Very likely |
| `ai_familiarity` | AI tool familiarity (1-7) | 1 = Not familiar, 7 = Very familiar |
| `age` | Age range | "18-20", "21-23", "24-26", "27 or above" |
| `gender` | Gender | Male, Female, Other |

### Experimental Conditions

- **TP (True Positive)**: AI image + "AI-Generated" label ✓
- **TN (True Negative)**: Real image + "Human-Created" label ✓
- **FP (False Positive)**: Real image + "AI-Generated" label ✗
- **FN (False Negative)**: AI image + "Human-Created" label ✗

## Installation

### Requirements

```bash
pip install pandas numpy scipy statsmodels pingouin matplotlib seaborn
```

### Python Version
- Python 3.8+

## Usage

This notebook performs:
1. Sample characteristics summary
2. Condition distribution checks (design balance)
3. Descriptive statistics (means, SDs, correlations)
4. Paired t-tests (correctly labelled AI vs Real)
5. Repeated measures ANOVA (4 conditions)
6. Linear Mixed Models (Origin × Label interaction)
7. Heterogeneity analyses (gender, AI familiarity)
8. Image-level mislabel effects
9. Figure generation (8 publication-ready plots)

### Output Files

- **Console**: Full statistical output with interpretations
- **`summary_statistics.csv`**: Condition means/SDs
- **`results_summary.txt`**: Complete findings summary
- **`figures/*.png`**: All visualizations

## Key Statistical Results

### Primary Finding: Crossover Interaction

**Linear Mixed Model (Effort Rating)**:
```
Origin × Label Interaction: β = 1.932, SE = 0.288, p < 0.0001
```

**Estimated Marginal Means**:
- TP (AI+AI label): 3.85/7
- TN (Real+Real label): 4.91/7
- **FP (Real+AI label): 3.94/7** ← Real image devalued
- **FN (AI+Real label): 4.80/7** ← AI image elevated

### Effect Interpretation

Labels dominate perception:
- Correctly labeled Real (TN): 4.91/7
- Correctly labeled AI (TP): 3.85/7
- **Mislabeled as AI (FP): 3.94/7** - catastrophic devaluation of real content
- **Mislabeled as Human (FN): 4.80/7** - complete elevation to real content level

### No Moderation Effects

- **Gender**: 3-way interaction p = 0.98 (effort), p = 0.55 (sharing)
- **AI Familiarity**: r = -0.09, p = 0.32 (no protective effect of expertise)

## Citation

If you use this data or code, please cite:

```bibtex
@unpublished{Murtaza2025ImagePerception,
  title={User Perception of AI Generated Images},
  author={Murtaza, Ibrahim and Imran, Khadija and Azhar, Xeerak and Sadjid, Momina},
  year={2025},
  institution={Lahore University of Management Sciences},
  note={CS 6303 Final Project - Randomisation Interface}
}
```

## Related Repository

- **Image Generation Interface**: https://github.com/ibrahim-murtaza/image-perception-study

## License

This dataset is released for academic research purposes. Please contact authors for commercial use.
