# [Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge](https://github.com/Luke-J-Miller/Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge/tree/main)

## [raw data](https://github.com/Luke-J-Miller/Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge/tree/main/raw_data)
Raw datasets contains 4 datasets, 3 simulated and 1 real.  The 3 simulated datasets contain 4 files each: causal.npy, alarm.csv, topology.npy, and rca_prior.csv, but RCA_prior and topology files are for informational purposes.

## [processed data](https://github.com/Luke-J-Miller/Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge/tree/main/processed_data)
Contains the four datasets, but they have been converted with data_cleanining_and_compression.ipynb to a sparse format in which the x-axis is a list of unique alarm_id mapped to the final column that is the causal information for that alarm_id.  The columns between alarm_id and causal are timestamps at one second intervals.  Each location contains an array of unique device id's indicating if that device is indicating that alarm at that time.

This dataset is very sparse which makes it easier to use with a variety of models; however, that sparsity makes the files much larger.  In data_cleanining_and_compression.ipynb, csr is used to compress zero values to bring the size of the files to a manageable level.  It also subdivides the datasets into 1024 slices to cover the approsimately 2 million second time window.  These datasets can be decompressed using csl-processed-data-unpacker.ipynb.  As they are used in models, slices may be concatenated as desired.

## [src](https://github.com/Luke-J-Miller/Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge/tree/main/src)
Currently contains 3 files
- ### [csl-data-exploration-r.r](https://github.com/Luke-J-Miller/Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge/blob/main/src/csl-data-exploration-r.r)
  - Just an introductory look at the data to understand its structure.

- ### [data_cleanining_and_compression.ipynb](https://github.com/Luke-J-Miller/Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge/blob/main/src/data-cleaning-and-compression.ipynb)
  - Converts the data to a sparse, consistently sized matrix.  Slices the times into 1024 chunks, and compresses the data using csr and pickle for easy transfer.

- ### [csl-processed-data-unpacker.ipynb](https://github.com/Luke-J-Miller/Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge/blob/main/src/csl-processed-data-unpacker.ipynb)
  - A simple notebook that unpickles and converts from csr format to a sparsedataset.

## [results](https://github.com/Luke-J-Miller/Causal-Structure-Learning-from-Event-Sequences-and-Prior-Knowledge/tree/main/results)
Currently empty.  Hopefully, there's something here soon.
