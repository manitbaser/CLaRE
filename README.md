# CLaRE

This repository contains the data for CLaRE (Critical Layer Representation Entanglement), a lightweight, representation-level technique designed to identify and predict ripple effects in Large Language Model editing.

## 📂 Repository Structure
data.json: The curated corpus of 11,427 facts used for analysis.

entanglement_results_GPT2-XL.json: Entanglement metrics computed for the GPT2-XL (1.5B) model.

entanglement_results_gpt_J.json: Entanglement metrics computed for the GPT-J (6B) model.

entanglement_results_Llama3.json: Entanglement metrics computed for the Llama3 (8B) model.


## 📊 Data Format
### Input Data (data.json)

The source facts are stored as a list of JSON objects containing the prompt template, the subject, and the target answer.

```
[
  {
    "prompt": "The type of music that {} plays is",
    "subject": "P. G. Wodehouse",
    "target": "comedy"
  },
  ...
]
```


### Result Files (Entanglement graphs: entanglement_results_[model].json)

The results files contain two main sections:

1. **Triplets**: A list of facts mapped to a unique key (UUID), including the formatted string.

2. **Entanglement Metrics**: A dictionary where keys are pairs of fact UUIDs, and the value is the Cosine Similarity of their hidden representations at the critical layer.

```
{
  "triplets": [
    {
      "key": "9bdc7eaa829f405df1bd8e56cd67223e",
      "prompt": "The type of music that {} plays is",
      "subject": "P. G. Wodehouse",
      "answer": "comedy",
      "formatted": "The type of music that P. G. Wodehouse plays is -> comedy"
    },
    ...
  ],
  "entanglement_metrics": {
    "key1:key2": {
      "value": {
        "cosine_sim": 0.6061649331686906
      }
    }
    ...
  }
}
```

GPT2-XL result file: https://drive.google.com/file/d/1LeiJT7H-b8IYz8e4krgrikNC1FloXR_q/view?usp=sharing

GPT-J result file: https://drive.google.com/file/d/1ugsakJbe4bYWp1uEXTEvBCYhbHH0TJMR/view?usp=sharing

Llama3 result file: https://drive.google.com/file/d/1_E8ijhbt4pwDgzLZMDqSHMGodmDwaYxk/view?usp=sharing
