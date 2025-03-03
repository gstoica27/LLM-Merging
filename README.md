<div align="center">


<h1>LLM-Merging: Building LLMs Efficiently through Merging </h1>

[![](https://img.shields.io/badge/Documentation-online-green)](https://llm-merging.readthedocs.io)
[![](https://img.shields.io/badge/Website-online-green)](https://llm-merging.github.io)
[![](https://img.shields.io/badge/License-MIT-blue)](#License)
</div>

This includes the starter code for the LLM-Merging competition. 

## Setup Environment 

The library was tested on CUDA 10.1 on an A6000. 

```
conda env create -f environment.yml --name llm-merging
conda activate llm-merging 
export PYTHONPATH=`pwd`
```

Authentication tokens are requied for certain models like Llama2 which require user agreeing to some terms. 
The authentication token can be found [here](https://huggingface.co/settings/tokens)

```
export HF_AUTH_TOKEN=""
```

## Developing New Merging Methods 

Do not modify any files other than the new file created and `setup.py`. Doing so can result in the grounds for invalidating your submission. If there is any code in the other files you need to change, feel free to open a pull request to change it. 

1. To add a new merging method, create a new file in `llm_merging/merging`. 
    This file should implement `__init__.py` and `merge.py` functions and extend `llm_merging/merging/Merges`. 
    See `llm_merging/merging/FlanT5Avg.py` or `llm_merging/merging/LlamaAvg.py` for examples.  

2. Modify `setup.py` and add an entry with the merging method in`llm_merging.merging.Merges`. 
   
   For example, the entry `llama_avg = llm_merging.merging.LlamaAvg:LlamaAvg` indicates the method is called `llama_avg` and the file is at `llm_merging/merging/LlamaAvg` 

## Evaluate Method 

```
python llm_merging/setup.py install 
python llm_merging/main.py -m {merging_method}
```


## Submissions

After modifying the file, zip the file in a tarball and send to ``. 