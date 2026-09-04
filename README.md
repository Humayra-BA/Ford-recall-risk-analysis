# Ford Recall & Warranty Risk Analysis
## Overview
Ford Motor Company has faced a sustained recall and warranty cost crisis — approximately $1.9 billion in excess warranty costs in 2023 alone, plus a $165 million NHTSA civil penalty for recall compliance failures. This consultancy-style project investigates whether Ford's recall risk is randomly distributed or structurally concentrated, using 2015–2025 recall data from the National Highway Traffic Safety Administration (NHTSA).
## Approach
Analysis was conducted under the **COSO Enterprise Risk Management (ERM) framework**, reframing recall activity as an enterprise governance risk rather than isolated technical failures. A severity-weighted **Risk Index** was constructed (affected vehicle volume × severity weight) to shift focus from recall *frequency* to enterprise *exposure*.
Two predictive models were built:

**1. Binary Logistic Regression** (R — tidyverse, caret, pROC, ggplot2)
- Classified recall events as High Impact / Not High Impact using engineered recurrence and severity features
- Trained on 6,009 cleaned recall records (80/20 split)
- Result: AUC 0.644, accuracy 0.669 — identified platform recurrence and platform–component interaction as the strongest drivers of high-impact escalation

**2. Random Forest Classification** (Python — scikit-learn, pandas, numpy, matplotlib, seaborn)
- Predicted failed component category from recall text (summary, consequence, remedy) using TF-IDF text preprocessing
- Trained on 2,005 filtered recall records (80/20 split)
- **Result: 95.5% classification accuracy**
## Key Findings
- Recall risk is heavy-tailed: ~70–80% of severity-weighted exposure is driven by a limited number of platform–component clusters
- Software, sensing systems, airbags, and transmissions are persistent high-risk subsystems
- Risk is structural and recurring, not evenly distributed across Ford's fleet

## Recommendation
A **Hotspot-Focused Quality Risk Reduction Program** — concentrating engineering, supplier oversight, and governance resources on the highest-risk platform/component clusters — is proposed as an 18-month phased implementation, with an estimated $95M–$150M+ in annual savings depending on exposure reduction achieved.

## Data Source
Publicly available recall data from the NHTSA API (`api.nhtsa.gov`) — de-identified, government-published data with no personal or confidential information.

## Tools
R (tidyverse, caret, pROC, ggplot2) · Python (scikit-learn, pandas, numpy, matplotlib, seaborn) · COSO ERM framework
