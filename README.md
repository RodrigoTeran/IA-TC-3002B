### Rodrigo Terán Hernández A01704108
> Última versión: 6/04/2025

# Contexto
## Objetivo
El objetivo del proyecto es predecir el precio de un carro usado.

## Set de datos
Estos datos están en un CSV <a href="cardekho.csv">cardekho.csv</a> y estas son las columnas:

Columnas y tipo de dato:

- `name`: string
- `year`: number
- `km_driven`: number
- `fuel`: ['Petrol', 'LPG', 'Diesel', 'CNG’]
- `seller_type`: ['Individual', 'Dealer', 'Trustmark Dealer’]
- `transmission`: ['Automatic', 'Manual’]
- `owner`: ['Second Owner', 'Third Owner', 'First Owner', 'Fourth & Above Owner’]
- `mileage (km/ltr/kg)`: number
- `engine`: number
- `max_power`: number
- `seats`: number
- `selling_price`: number

La columna `selling_price` es la que queremos predecir cuando tengamos los otros datos disponibles. En otras palabras, `selling_price` es por cuánto se vende un carro usado.

# Avance 6/04/2025
## Preprocesamiento
Se limpió el set de datos original al:

- remover valores nulos
- filas incompletas
- filas que los tipos de datos no coincidían

## Separación
Y se separó en un set de entrenamiento y prueba. Además de separar los "features” y el "target”.

En este caso la única columna "target” es `selling_price`. Y las "features” son todas las demás columnas.

Datos separados:

Entrenamiento:

- "train_features.csv"
- "train_target.csv"

Prueba:

- "test_features.csv"
- "test_target.csv"

## Escalamiento
### Variables numéricas
Se uso `MinMaxScaler` para las variables numéricas para que se encuentren en un rango de 0 a 1.

### Variables categóricas
Esto convierte los textos como "Diesel", "Manual", "Dealer", etc. en números para que el modelo pueda entenderlos.

Se usó `OneHotEncoder`, que convierte cada categoría en una columna binaria (0 o 1).

### Variables omitidas
Por el momento se omitió la variable de `name`. Ya que no se encontró que podría representar relevancia para entrenar el modelo.

## Entrenar modelo
Se usó `RandomForestRegressor` para entrenar el modelo con los datos procesados.

## Resultado obtenidos

> Hay que tener en cuenta que los precios están en "Indian rupees":

### Mean Absolute Error 
- En Indian rupees: 61,865.10​ ₹
- En MXN: 61,865.10 × 0.2389 ≈ 14,789.47 MXN​

Este valor representa el error promedio en las predicciones.

### Mean Squared Error
- Indian rupees: 13,664,439,025.37 ₹²
- MXN: 61,865.10 × 0.2389 ≈ 3,264,434,483.16 MXN​²

Este valor es como el MAE, pero eleva al cuadrado cada error antes de hacer el promedio.

### R2
- R2 Score: 0.9781

Esto indica qué tan bien el modelo explica la variación en los precios de los carros.

### Mean Absolute Percentage Error
- MAPE: 14.40%

Este valor nos dice el error promedio en porcentaje en relación al valor real.