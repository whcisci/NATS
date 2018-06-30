# Text summarization

- Neural Abstractive Summarization with Sequence-to-Sequence models
- Bug report tshi at vt dot edu.
- Previous version with python2.7 can be found [here](https://github.com/tshi04/textsum/tree/master/tools/codes_python2.7). 

## Requirements

- Python 3.5.2
- glob
- argparse
- shutil
- pytorch 0.4.0

Use following scripts to setup
- [Tesla K80](https://github.com/tshi04/textsum/tree/master/tools/config_server)
- [Tesla V100](https://github.com/tshi04/SetEC2)
- [pyrouge and ROUGE-1.5.5](https://github.com/tshi04/textsum/tree/master/tools/rouge_package)

## Usuage

#### Dataset

- [CNN/Daily Mail](https://github.com/abisee/pointer-generator)
- [newsroom](https://github.com/tshi04/textsum/tree/master/tools/newsroom_process)

Note: Please set bool type parameters in the main.py file.

#### Training
```
python main.py 
```
#### Validate
```
python main.py --task validate --batch_size 10
```
#### Test
```
python main.py --task beam --batch_size 4
```
#### Rouge
```
python main.py --task rouge
run cal_rouge.ipynb to calculate the rouge score using pyrouge and ROUGE-1.5.5
```

## Problems and Todos

- The following combinations failed during the training after several epochs.
```
concat + temporal
concat + temporal + attn_decoder
```
- We have tried to optimize the memory usage, but we are still not quite happy with it.
- Merge the LSTM and GRU decoders.
- The src_hidden_dim and tar_hidden_dim have not been correctly implemented, they must be the same currently.
- The n_layers for the decoder does not work, remove it and use the single layer only.
