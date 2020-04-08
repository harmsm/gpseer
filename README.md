# GPSeer
*Simple software for inferring missing data in sparsely measured genotype-phenotype maps*

![GPSeer tests](https://github.com/harmslab/gpseer/workflows/GPSeer%20tests/badge.svg)

## Basic Usage

Install gpseer using pip:
```bash
pip install gpseer
```

The simplest use-case is to call `gpseer` on an input `.csv` file containing genotype-phenotype data.

### Downloading the example

To get started, use GPSeer's `fetch-example` command to download an example from its Github repo.

Download the gpseer example and explore the example input data:
```bash
# fetch
> gpseer fetch-example
[GPSeer] Downloading files to /examples...
[GPSeer] └──>: 100%|██████████████████| 3/3 [00:00<00:00,  9.16it/s]
[GPSeer] └──> Done!

# Change into the example directory and checkout the files that were downloaded
> cd example/
> ls
example-full.csv  example-test.csv  example-train.csv
```

### Predicting missing data using ML model.

Estimate the maximum likelihood additive model on the training set and predict all missing genotypes. The predictions will be written to a file named `"predictions.csv"`.

```bash
> gpseer estimate-ml example-train.csv

[GPSeer] Reading data from example-train.csv...
[GPSeer] └──> Done reading data.
[GPSeer] Constructing a model...
[GPSeer] └──> Done constructing model.
[GPSeer] Fitting data...
[GPSeer] └──> Done fitting data.
[GPSeer] Predicting missing data...
[GPSeer] └──> Done predicting.
[GPSeer] Writing phenotypes to predictions.csv...
[GPSeer] └──> Done writing predictions!
[GPSeer] GPSeer finished!
```

### Compute the "goodness-of-fit"

Estimate how well your model is predicting data using the "goodness-of-fit" subcommand.
Try the example below where we generate 10 subsets from the data and comput our prediction scores. The output can be found in the `"scores.csv"` file.

```bash
> gpseer goodness-of-fit example-full.csv 10

[GPSeer] Reading data from example-full.csv...
[GPSeer] └──> Done reading data.
[GPSeer] Sampling the data...
[GPSeer] └──>: 100%|████████████████| 10/10 [00:00<00:00, 37.77it/s]
[GPSeer] └──> Done sampling data.
[GPSeer] Writing scores to scores.csv...
[GPSeer] └──> Done writing data.
[GPSeer] GPSeer finished!
```


##