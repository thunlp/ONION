# ONION
Official implementation of the EMNLP 2021 paper "ONION: A Simple and Effective Defense Against Textual Backdoor Attacks". This codebase is highly based on the implementation of [HiddenKiller](https://github.com/thunlp/HiddenKiller).

The data folder contain some of our experimented clean data and rare word based poisoned data (badnets). The poison rate is 5%. 





## Train a Poison Model

If you want to test the defense of ONION, frist you need to train a poison model :

```bash
CUDA_VISIBLE_DEVICES=0 python run_poison_bert.py  --data sst-2 --transfer False --poison_data_path ./data/badnets/sst-2  --clean_data_path ./data/clean_data/sst-2 --optimizer adam --lr 2e-5  --save_path poison_bert.pkl
```





## Test ONION defense

To test ONION defense on SST-2 against badnets:

```bash
CUDA_VISIBLE_DEVICES=0 python test_defense.py  --data sst-2 --model_path poison_bert.pkl  --poison_data_path ./data/badnets/sst-2/test.tsv  --clean_data_path ./data/clean_data/sst-2/dev.tsv
```

Here, --model_path is the --save_path in run_poison_bert.py to assign the path to saved backdoor model. 





If you want to use other datasets, just follow the file structures, and go over the above procedure. 



