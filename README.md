# Genre Classification

This is a Reproducible Machine Learning Project to classify music genre. This project built around MLFlow, Hydra, wandb with scientific libraries like Scikit Learn, Scipy, pandas, numpy etc. You can see the run on wandb [here](https://wandb.ai/gustiwinata/exercise_14)

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
