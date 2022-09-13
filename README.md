# Genre Classification

This is a Reproducible Machine Learning Project to classify music genre. This project built around MLFlow, Hydra, wandb with scientific libraries like Scikit Learn, Scipy, pandas, numpy etc. You can see the run on wandb [here](https://wandb.ai/gustiwinata/genre_classification_prod)

## How to run

First of all, install conda, wandb and MLFlow on your client. Make sure to login on wandb cli too, then clone this repo and:

```bash
> mlflow run .
```

Or if you wanted to run a specific pipeline, you can take a look of this example and suit it with your needs.

```bash
> mlflow run . -P hydra_options="main.execute_steps='random_forest'"

or to run multiple pipelines

> mlflow run . -P hydra_options="main.execute_steps='download,preprocess'"
```

or if you don't want to clone this repo but still wanted to run this project as well you can run:

```bash
> mlflow run https://github.com/sanggusti/genre_classification
```

## Command lists

Download model artifact

```bash
> wandb artifact get genre_classification_prod/model_export:prod --root model
```

Run Sweeps of parameters

```bash
mlflow run . \
  -P hydra_options="-m main.execute_steps='random_forest' \
                    random_forest_pipeline.random_forest.max_depth=range(10,50,3) \
                    random_forest_pipeline.tfidf.max_features=range(50,200,50) \
                    hydra/launcher=joblib"
```

Batch(Offline) Inference

```bash
> mlflow models predict \
                -t csv \
                -i ./artifacts/data_test.csv:v0/data_test.csv \
                -m model
```

Realtime Inference

```bash
> mlflow models serve -m model &
```

> (note that we run in the background by using & so that the REST API stays active) We can now perform inference using our model, for example using Python.

Docker Deployment

```bash
> mlflow models build-docker -m model -n "genre_classification"
```
