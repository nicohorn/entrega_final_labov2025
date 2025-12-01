# Prediccion de Fuga de Clientes

Workflow para predecir fuga de clientes bancarios usando LightGBM.

Competencia Kaggle: `laboi-2025-virtual-gerencial`

## Ejecucion

1. Abrir `610_gerencial_nicolas_horn_v8.ipynb` en Google Colab
2. Ejecutar celdas 1-3 con Runtime Python (setup + descarga de datos)
3. Cambiar Runtime a R
4. Ejecutar el resto del notebook

## Envios a Kaggle

Los envios se hacen manualmente. Esto es intencional para evitar hacer envios automaticos constantemente durante el desarrollo y debugging.

Una vez ejecutado el notebook, los CSVs quedan en:

```
/content/buckets/b1/exp/WF*/kaggle/
```

Para enviar manualmente desde Colab:

```bash
kaggle competitions submit -c laboi-2025-virtual-gerencial -f archivo.csv -m "mensaje"
```

O descargar los CSVs y subirlos desde la web de Kaggle.

## Tecnicas

- Catastrophe Analysis: Variables anomalas de 202006 -> NA
- Data Drifting: Deflactacion por IPC
- Feature Engineering: lags(1-3), deltas(1-3), trends(3,6)
- Exclusion de variables leaky: numero_de_cliente, foto_mes

## Hiperparametros

Optimizados con Bayesian Optimization (250 iteraciones):

- num_leaves: 289
- min_data_in_leaf: 279
- max_depth: 10
- lambda_l1: 0.529
- lambda_l2: 3.062
- num_iterations: 463

## Autor

Nicolas Horn - Universidad Austral
