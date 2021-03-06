## HCNN
Hybrid Convolutional Neural Network for sentiment strength prediction

## Running the program
Run the baseline model:

    python baseline.py PA PB
    
PA, PB represent model name and dataset name respectively. PA is `CNN` or `LSTM`, where the former is the **CNN-non-static** proposed in [Kim's paper](http://www.aclweb.org/anthology/D14-1181) and the latter is the basic **LSTM** model using the last hidden state as the sentence representation.

Run HCNN:
 
    python model.py
   
If GPU and CUDA toolkit are available on your machine, Keras will use GPU in default case. To accelerate the execution, you can add theano flags `lib.cnmem=1` if your GPU is in idle state (Note: it only works on theano backend):

    THEANO_FLAGS="lib.cnmem=1" python model.py
    
To run experiment over multiple datasets, execute fast_run.py with `mode` parameter:
 
    python fast_run.py mode
    
value of `mode` can be *baseline*, *HCNN* or *HCNN_ablation*, which means runing baseline, HCNN or doing ablation experiment on HCNN respectively.
    
## Parameter Settings
* `Word embedding`: [GloVe](http://nlp.stanford.edu/projects/glove/) (twitter.27B.200d)
* `dim_w`: 200
* `n_k`: 80 (number of convolutional kernels)
* `n_pos`: 2 (number of convolutional kernels for POS tags)
* `dim_d`: 100 (dimension of sentence or document)

## Environments
* OS: REHL Server 6.4 (Santiago)
* GPU: GeForce GTX Titan Black
* CUDA: 7.0
* Python: Interpreter (2.7.12), Keras(1.0.1), Theano(0.8.2), scikit-learn(0.17.1), nltk(3.1), numpy(1.11.0)

Note: the code is only tested on the above environment

