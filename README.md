# Automatic Explanation Generation For Climate Science Claims
This repository contains the source code for our ALTA 2022 [paper](https://aclanthology.org/2022.alta-1.16/): Automatic Explanation Generation For Climate Science Claims.

## Abstract
Climate change is an existential threat to humanity, the proliferation of unsubstantiated claims relating to climate science is manipulating public perception, motivating the need for fact-checking in climate science. In this work, we draw on recent work that uses retrieval-augmented generation for veracity prediction and explanation generation, in framing explanation generation as a query-focused multi-document summarization task. We adapt PRIMERA to the climate science domain by adding additional global attention on claims. Through automatic evaluation and qualitative analysis, we demonstrate that our method is effective at generating explanations.

## Requirements
Recommend proceed with creating a conda environment:
```
conda create --name <env_name> --file requirements.txt
```

## Data
There are two key data components in our task: 
- An external knowledge source from which we retrieve documents, here we use [Pubmed data](https://pubmed.ncbi.nlm.nih.gov/) and [IPCC reports data](https://www.ipcc.ch/).
- Paired claim–explanation data, to serve as the input (claim) and output (explanation). We use [Climate Fever](https://github.com/tdiggelm/climate-fever-dataset).
- After retrieval process via [Binary Passage Retriever](https://github.com/studio-ousia/bpr), the final data is used directly for model training and evaluation. Please feel free to download data from here().

### Data format
Each instance in JSON file contains the following columns:
- id - the unique identifier for the instance
- ctxs - retrieved passages relating to the claim
  - title: the title of the passage
  - text: the content of the passage
- question - the claim that needs to be fact-checked
- answers - a list of evidences to support/refute the claim, they are extracted from original [Climate Fever](https://github.com/tdiggelm/climate-fever-dataset)
- target_lab - claim label, 0 - SUPPORTS, 1 - REFUTES, 2 - NOT_ENOUGH_INFO
- task - not used, specific format for T5

### Data example
```json
{'id': 1411,
 'ctxs': [
   {
      'title': 'ipcc gw ch6',
      'text': 'set too low or too high (Loock et al., 2013)1192. Commitment strategies where people make a pledge to engage in climate actions can encourage mitigation behaviour...'},
      {'title': '...', 'text': '...'} // Other evidence passages
      ],
      'question': 'The Independent Climate Change Email Review found the CRU scientists were unhelpful and unsympathetic to information requesters and at times broke FoI laws.',
      'answers': ['The Science and Technology Select Committee report blamed the university for mishandling Freedom of Information requests and said it had "found ways to support the culture at CRU of resisting disclosure of information to climate change sceptics".'],
      'target_lab': 0,
      'task': 'evidence'
}
```

## Citation
```bibtex
@inproceedings{xing-etal-2022-automatic,
    title = "Automatic Explanation Generation For Climate Science Claims",
    author = "Xing, Rui  and
      Bhatia, Shraey  and
      Baldwin, Timothy  and
      Lau, Jey Han",
    booktitle = "Proceedings of the The 20th Annual Workshop of the Australasian Language Technology Association",
    month = dec,
    year = "2022",
    address = "Adelaide, Australia",
    publisher = "Australasian Language Technology Association",
    url = "https://aclanthology.org/2022.alta-1.16",
    pages = "122--129",
    abstract = "Climate change is an existential threat to humanity, the proliferation of unsubstantiated claims relating to climate science is manipulating public perception, motivating the need for fact-checking in climate science. In this work, we draw on recent work that uses retrieval-augmented generation for veracity prediction and explanation generation, in framing explanation generation as a query-focused multi-document summarization task. We adapt PRIMERA to the climate science domain by adding additional global attention on claims. Through automatic evaluation and qualitative analysis, we demonstrate that our method is effective at generating explanations.",
}
```
