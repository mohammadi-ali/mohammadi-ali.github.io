# README: Definition Integration & Knowledge Conflict Experiments

## Overview
This repository follows the structure of our research paper, focusing on two key research questions:

1. Definition Integration – Exploring how different definitions impact model performance.
2. Knowledge Conflict – Analyzing the effects of contradictory definitions.

The repository is structured accordingly, with separate folders for each experiment and results stored in an organized manner.

## Repository Structure

```
Definition_Integration/
 ├── llama/
 ├── gpt/
 ├── mistral/
 ├── phi/
 ├── results/

Knowledge_Conflict/
 ├── correct_wrong_slightlywrong_experiments/
 │   ├── llama/
 │   ├── gpt/
 │   ├── mistral/
 │   ├── phi/
 │   ├── results/
 ├── permutation_experiments/ (TBD)

metrics/
requirements.txt
```

## Definition Integration: Experimental Setups
The Definition Integration experiments investigate the role of definitions in model performance. These experiments are conducted across:

- Datasets: e-SNLI, WellXplain, HateXplain
- Models: GPT-4, LLaMA-3, Mistral, Phi-3

### Experimental Configurations
| Experiment Type               | Definition          | Few-shot Learning | Description |
|--------------------------------|---------------------|-------------------|-------------|
| Vanilla                        | No                 | No                | Only classification prompt (Baseline) |
| Fixed Definition               | Yes (Predefined)   | No                | Fixed definition included in prompt |
| Adjusted Definition            | Yes (LLM-Generated)| Yes               | LLM generates definitions dynamically; few-shot included |
| Descriptive Few-shot           | No                 | Yes               | Few-shot with descriptive labels, no definition |
| Numerical Few-shot             | No                 | Yes               | Few-shot with numerical labels only |
| Fixed Definition + Few-shot    | Yes (Predefined)   | Yes               | Uses a fixed definition + few-shot examples |

### File Naming Conventions
Each experiment follows a consistent file naming format:
- `Vanilla_with_definition.py`: Classification prompt with a fixed definition (Fixed Definition)
- `Vanilla_without_definition.py`: Classification prompt only, without any definition (Vanilla)
- `Few_shot_with_LLM_generated_Definitions_K_value_X.py`: Few-shot classification with LLM-generated definitions, where `X` is the number of shots
- `Few_shot_without_definitions_K_value_X.py`: Few-shot classification without definitions
- `Few_Shot_Only_Numerical_Labels_K_value_X.py`: Few-shot with numerical labels only
- `Few_Shot_with_predefined_definitions_K_value_X.py`: Few-shot with predefined definitions

## Knowledge Conflict: Experimental Setups
The Knowledge Conflict experiments analyze how models handle contradictory information. Two sets of experiments are performed:

1. Correct, Wrong, Slightly Wrong Definitions
2. Permutation Experiments (TBD)

The Correct, Wrong, Slightly Wrong experiments maintain the same folder structure as Definition Integration:
- Each model folder contains subfolders for e-SNLI, WellXplain, and HateXplain.
- Corresponding results are stored in `correct_wrong_slightlywrong_experiments/results/`.

## Installation & Running Instructions

### 1. Clone the Repository
```
git clone https://github.com/your-repo-name.git
cd your-repo-name
```

### 2. Install Dependencies
```
pip install -r requirements.txt
```

### 3. Download Datasets
| Dataset      | Source |
|-------------|--------|
| e-SNLI      | https://huggingface.co/datasets/esnli/esnli |
| HateXplain  | https://huggingface.co/datasets/Hate-speech-CNERG/hatexplain |
| WellXplain  | https://github.com/drmuskangarg/WellnessDimensions/blob/main/dataset_wellnessdimensions.csv |

For WellXplain, download the CSV manually and adjust the `k` value in the script before running.

### 4. Running Experiments
Run the script for the specific model and dataset as follows:
```
python Definition_Integration/gpt/e-SNLI/Vanilla_with_definition.py
```
To test on fewer samples, adjust the `samples` variable in the script.

## Results & Metrics
- All experiment results are stored in CSV format under respective `results/` folders.
- Additional evaluation metrics are available in the `metrics/` folder.

## Future Updates: Permutation Experiments
