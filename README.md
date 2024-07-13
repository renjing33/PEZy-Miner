# PEZy-Miner: An artificial intelligence driven approach for the discovery of plastic-degrading enzyme candidates

This is the official repository for the paper [*PEZy-Miner: An artificial intelligence driven approach for the discovery of plastic-degrading enzyme candidates*](a http link will be added once the manuscript is published).

To use PEZy-Miner to mine any customized dataset for the top-ranked enzyme/plastic pairs, you will need everything in this repository. 

## 1. Prepare your data

The experimental dataset used in the paper can be found in `/data/20231214_strong_labels.csv`. No need to change this unless you would like to train your own model on your own training data.

The prescreened homologous dataset used in the paper can be found in `/data/prescreen_hs_with_weak_label.csv`. To discover top-ranked enzyme/plastic pairs from your own dataset, replace this homologous dataset with your own dataset but use the name filename. Make sure your dataset is in the following format.

```

Look up how to display a spreadsheet, and then add the first 5 lines of our homologous dataset here.

```

## 2. Run the ProtBERT_MLP model or the ProtBERT_proto model

### 2.1. Select the model, ProtBERT_MLP or ProtBERT_proto

In the `/code` directory, open the `test_protbert.py` script. In line 60, you will find

```

parser.add_argument('-classifier', type=str, default='proto', help='classifier')

```

This defines the model you would like to use. To use ProtBERT_MLP, set default to `default='mlp'`. To use ProtBERT_proto, set default to `default='proto'`.

### 2.2. Run the model

a. Run `test_protbert.py`. This could take a couple of minutes or several hours. The time depends on your device and the size of your customed dataset.

b. Repeat part a 5 times by changing the random seeds defined in line 32

```

parser.add_argument('-seed', type=int, default=42, help='random seed')

```

c. The 5 output files will be generated as `/code/prediction_results_test_ProtBERT_seedXXX.csv`.

## 3. Get your top list

Once you obtained the output files, copy and paste them in the `/get top list/mlp/` or `/get top list/proto/` directory.

Next, open the `result_analysis.ipynb` script, and go through the script to define your own variables, such as random seeds, classifier, top percentile, which are clearly marked in the beginning of every cell.

After you run the .ipynb file, the top list will be generated as `result_analysis/toplist_XXX.csv`.

