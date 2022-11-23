# Automatic Explanation Generation For Climate Science Claims
This repository contains the source code for our ALTA 2022 paper: Automatic Explanation Generation For Climate Science Claims.

Climate change is an existential threat to humanity, the proliferation of unsubstantiated claims relating to climate science is manipulating public perception, motivating the need for fact-checking in climate science. In this work, we draw on recent work that uses retrieval-augmented generation for veracity prediction and explanation generation, in framing explanation generation as a query-focused multi-document summarization task. We adapt PRIMERA to the climate science domain by adding additional global attention on claims. Through automatic evaluation and qualitative analysis, we demonstrate that our method is effective at generating explanations.

## Requirements
Recommend proceed with creating a conda environment:
```
conda create --name <env_name> --file requirements.txt
```

## Data
There are two key data components in our task: 
- An external knowledge source from which we retrieve documents; 
- Paired claim–explanation data, to serve as the input (claim) and output (explanation)
### PubMed and IPCC reports
- Pubmed data can be downloaded from: https://pubmed.ncbi.nlm.nih.gov/
- IPCC reports data can be downloaded from: https://www.ipcc.ch/

### Climate-Fever(Paired Data)
Climate Fever dataset can be downloaded from: https://github.com/tdiggelm/climate-fever-dataset

Climate-Fever data example:
```json
{
   "claim_id":"108",
   "claim":"sea-level rise is not accelerating.",
   "claim_label":"REFUTES",
   "evidences":[
      {
         "evidence_id":"Sea level rise:2",
         "evidence_label":"NOT_ENOUGH_INFO",
         "article":"Sea level rise",
         "evidence":"More precise data gathered from satellite radar measurements reveal an accelerating rise of 7.5\u00a0cm (3.0\u00a0in) from 1993 to 2017, which is a trend of roughly 30\u00a0cm (12\u00a0in) per century.",
         "entropy":1.0986122886681096,
         "votes":[
            "SUPPORTS",
            "REFUTES",
            "NOT_ENOUGH_INFO",
            null,
            null
         ]
      },
      {
         "evidence_id":"Sea level rise:405",
         "evidence_label":"REFUTES",
         "article":"Sea level rise",
         "evidence":"\"Climate-change\u2013driven accelerated sea-level rise detected in the altimeter era\".",
         "entropy":0.0,
         "votes":[
            "REFUTES",
            "REFUTES",
            "REFUTES",
            null,
            null
         ]
      },
      {
         "evidence_id":"Sea level rise:492",
         "evidence_label":"REFUTES",
         "article":"Sea level rise",
         "evidence":"\"Antarctica ice melt has accelerated by 280% in the last 4 decades\".",
         "entropy":0.0,
         "votes":[
            "REFUTES",
            "REFUTES",
            "REFUTES",
            null,
            null
         ]
      },
      {
         "evidence_id":"Sea level rise:5",
         "evidence_label":"NOT_ENOUGH_INFO",
         "article":"Sea level rise",
         "evidence":"Climate scientists expect the rate to further accelerate during the 21st century.",
         "entropy":0.6365141682948128,
         "votes":[
            "NOT_ENOUGH_INFO",
            "REFUTES",
            "NOT_ENOUGH_INFO",
            null,
            null
         ]
      },
      {
         "evidence_id":"Sea level rise:65",
         "evidence_label":"REFUTES",
         "article":"Sea level rise",
         "evidence":"However scientists have found that ice is being lost, and at an accelerating rate.",
         "entropy":0.0,
         "votes":[
            "REFUTES",
            "REFUTES",
            "REFUTES",
            null,
            null
         ]
      }
   ]
}
```


## Training
coming soon...

## Evaluation
coming soon...

## Citation
coming soon...
