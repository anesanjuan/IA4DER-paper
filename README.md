# IA4DER-paper
# README

This repository contains the scripts used in the study on short-term load forecasting for residential electricity users. It evaluates local, global, and hybrid forecasting methods (particularly FFORMA).

Below is a brief description of each script and its purpose:

## 1_PrediccionDemanda

- **short.R**: Main script to run local forecasts for each individual time series. Trains multiple models per series and saves predictions and error metrics (MAPE, RMSE, etc.).

## 2_Preparar

- **PrepararDatosErrorNuevo.R**: Merges all local predictions, calculates MAPE and RMSE, and joins the results with metadata. Prepares the dataset used to predict model errors.

## 3_PredError

- **PredErrorModelosNuevos_dia.R**: Predicts the error (MAPE) of each base model using metadata. Trains models like Random Forest, XGBoost, and kNN to estimate expected errors per model and day.
- *(There are also versions by hour and by day+hour)*

## 4_FFORMA

- **FformaAne.R**: Custom FFORMA implementation. Combines base model forecasts using weights derived from predicted errors. Computes several variants: per-model FFORMA, historical, ex-ante, and ensemble.

## 5_predError and FFORMA orig

- **FFORMA_model.R**: Analysis of the original FFORMA model. Loads prediction/error results from an RDS file and generates boxplots and summary statistics.
- **Fforma_modeloNuevo.R**: Trains the original FFORMA using the official `fforma` R package with automatic feature extraction. Outputs forecasts and evaluation metrics.
- **errors.R**: Calculates MAPE and RMSE for global models and FFORMA. Performs statistical comparisons using Friedman and Nemenyi tests.

## 6_Conclusiones

- **DataCreation_group0.R / group1.R**: Scripts to generate synthetic datasets for controlled experiments that test FFORMA’s behavior in extreme scenarios.
- **fforma_nuestro_trampeado.R**: Tests FFORMA using manipulated data to check its sensitivity to informative vs. random features.
- **friedman.R**: Runs statistical tests on model performance.
- **modelosBase.R**: Generates forecasts from baseline models for comparison in synthetic experiments.

## 7_Graficos

- **GraficosBaseModels.R**: Plots results of baseline (local) models.
- **GraficosConclusiones.R**: Visualizes results from synthetic experiments.
- **GraficosDataUnderstanding.R**: Exploratory data analysis plots.
- **GraficosEnsembles.R**: Compares ensemble performance (FFORMA, median, etc.).
- **GraficosModelosGlobales.R**: Plots results of global models (Chronos, Bolt, etc.).
- **GraficosPredError.R**: Visualizes the accuracy of error prediction models.
- **GraficosTODO.R**: Miscellaneous plots (under development).

