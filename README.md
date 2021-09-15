# ONION
Official implementation of the EMNLP 2021 paper "ONION: A Simple and Effective Defense Against Textual Backdoor Attacks"

The data folder contain clean data and rare word-based poisoned data (badnets). 



First, train a badnets-poisoned model:

```bash
python run_poison_bert.py --gpu_id 0 --data sst-2 --poison_data ../data/badnets/sst-2 --clean_data_path ../data/clean_data/sst-2   --poison_rate 5    --save_path trained_poisoned_model_PATH
```



To test ONION defense on SST-2 against badnets :

```bash
python test_defense.py --gpu_id 0 --data sst-2 --clean_data_path ../data/clean_data/sst-2/test.tsv --poison_data_path ../data/scpn/20/sst-2/test.tsv --model_path trained_poisoned_model_PATH
```

