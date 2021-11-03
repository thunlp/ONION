# ONION
Official implementation of the EMNLP 2021 paper "[ONION: A Simple and Effective Defense Against Textual Backdoor Attacks](https://arxiv.org/abs/2011.10369)". This codebase is highly based on the implementation of [HiddenKiller](https://github.com/thunlp/HiddenKiller).

The `data` folder contains some of our experimented clean data and rare words based poisoned data (BadNets). The poisoning rate is 5%. 

## Train a Poisoned Victim Model

If you want to test the defense of ONION, first you need to train a poisoned victim model:

```bash
CUDA_VISIBLE_DEVICES=0 python run_poison_bert.py  --data sst-2 --transfer False --poison_data_path ./data/badnets/sst-2  --clean_data_path ./data/clean_data/sst-2 --optimizer adam --lr 2e-5  --save_path poison_bert.pkl
```



## Test the Defense Effectiveness of ONION 

To test ONION defense on SST-2 against BadNets, please run

```bash
CUDA_VISIBLE_DEVICES=0 python test_defense.py  --data sst-2 --model_path poison_bert.pkl  --poison_data_path ./data/badnets/sst-2/test.tsv  --clean_data_path ./data/clean_data/sst-2/dev.tsv
```

Here, `--model_path` is the `--save_path` in `run_poison_bert.py` that assigns the path to the saved poisoned victim model. 



If you want to conduct experiments on other datasets, just follow the file structures, and go over the above procedure. 

## Citation

Please kindly cite our paper:

```
@article{qi2020onion,
  title={Onion: A simple and effective defense against textual backdoor attacks},
  author={Qi, Fanchao and Chen, Yangyi and Li, Mukai and Yao, Yuan and Liu, Zhiyuan and Sun, Maosong},
  journal={arXiv preprint arXiv:2011.10369},
  year={2020}
}
```



