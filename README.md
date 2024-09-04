# Reto: Titanic - Machine Learning from Disaster
<p align="center">
  <img src="Image/titanic.png" alt="Titanic Disaster">
</p>
<div style="text-align: center;">
  <img src="Image/titanic.png" alt="Titanic Disaster">
</div>

![Titanic Disaster](Image/titanic.png)

## Equipo 5
### Integrantes de equipo:
- [María Lynne Camacho Padilla](mailto:a01423135@tec.mx)
- [Emiliano Ferreira Guadarrama](mailto:a01654418@tec.mx)
- [Humberto Alejandro Rosas Téllez](mailto:a01659823@tec.mx)
- [Victoria Estefanía Vázquez Morales](mailto:a01654095@tec.mx)  
## Propuesta de solución resumida
Nuestra propuesta comienza con el preprocesamiento de los datos, donde consideramos las siguientes características:
- **Clase del Pasajero**: Analizamos cómo la clase del pasajero afecta a las tasas de supervivencia.
- **Edad del Pasajero**: Investigamos la relación entre la edad del pasajero y su supervivencia.
- **Cantidad de Hermanos y Cónyuges a Bordo**: Exploramos cómo la presencia de hermanos y cónyuges afecta las posibilidades de supervivencia.
- **Cantidad de Padres/Madres e Hijos a Bordo**: Estudiamos el impacto de tener padres/madres e hijos a bordo en las tasas de supervivencia.
- **Tarifa Pagada por el Boleto**: Analizamos la relación entre la tarifa pagada y la supervivencia de los pasajeros.
- **Sexo del Pasajero**: Consideramos cómo el género del pasajero influye en su probabilidad de supervivencia.
- **Puerto de Embarcación**: Exploramos si el puerto de embarque tiene algún efecto en las tasas de supervivencia.
  
|       Criterio                | Descripción                                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Discretización de la Columna "Sex"**         | Realizamos una discretización de la columna "Sex" para que cada valor corresponda a un entero, facilitando su uso en el modelo.                   |
| **One Hot Encoding para "Embarked"** | Aplicamos One Hot Encoding para separar la característica 'Embarked' en características dummies, permitiendo que el modelo maneje esta información de manera efectiva.   |
| **Imputación de Datos Faltantes**            | Para abordar los datos faltantes, recomendamos utilizar el algoritmo KNN con un parámetro k=4. Esto nos ayudará a imputar valores faltantes de manera precisa. |
| **Estandarización de Puntuación Z**        | Recomendamos realizar una estandarización de puntuación z a los datos, asegurando que todas las características estén en la misma escala y facilitando la interpretación del modelo. |

#### Modelo Propuesto: Random Forest
Para la construcción del modelo, proponemos un Random Forest con los siguientes parámetros:
- Número de Árboles: 100
- Criterio de División: Gini
- Mínimo de Observaciones por División: 2
- Mínimo de Observaciones por Hoja: 2
  
Este modelo se seleccionó debido a su capacidad para manejar datos faltantes y categóricos, así como su robustez frente al sobreajuste.
## Problemas y soluciones
### 1. Exploración
| Problema | Solución |
| :--: | :--: |
| Encontrar features que tuvieran valor para entrenar el modelo | Investigamos datos generales del dataset Titanic, basándonos en hechos históricos sobre cómo se decidió el abordaje los botes, según su clase, edad y sexo. También hicimos una matriz de correlación para comprobar que las features tuvieran alta relación |
| Crear nuevas features de valor | Creamos nuevas columnas basándonos en el pronombre de los pasajeros, y encontramos que Miss y Mrs sobrevivieron más que los demás, también creamos una columna del tamaño de las familias, así nos dimos cuenta de que las familias de 4 tenían más probabilidad de sobrevivir |
| Tratar con datos vacíos | Eliminamos las columnas que tenían muchos datos vacíos, como Cabin |
### 2. Pre procesamiento 
| Problema | Solución |
| :--: | :--: |
| Columnas poco relevantes | Se tomó la decisión de eliminar las columnas de PassengerId, Name, Cabin y Ticket; debido a que, según el análisis de correlación, no influían lo suficiente para determinar si alguien sobrevivió o no |
| Columnas categóricas | Se discretizó la columna de Sex, para que fuese 0 y 1. También la columna de Embarked tenía tres categorías: Q, C, S; según el puerto desde donde subió el pasajero al Titanic, por lo que se agregaron 3 columnas adicionales, una por cada categoría, con One Hot Encoder. |
| Imputación de datos | Se utilizó KNN imputer para imputar datos en la columna de Age. El k seleccionado fue 4, debido a que tuvo una distribución más acercada a la real de los datos existentes. |
|Estandarización| Se realizó la estandarización de todos los datos en el _dataframe_, para tener todos los valores en una misma escala.  
### 3. Selección de modelo 
Con la finalidad de tratar de obtener la mayor exactitud y precisión en la predicción de las personas que sobrevivieron o no al desastre en el Titanic, se seleccionaron tres distintos modelos de Machine Learning para realizar esta clasificación, los cuales se describen a continuación:

| Modelo | Justificación de uso |
| :--: | :--: |
| Random Forest Classifier | Útil cuando se tiene la presencia de valores faltantes y categóricos, además de, tener una gran capacidad para el manejo de clasificaciones binarias y de ser robusto ante el overfitting. |
| SVM Kernel RBF | Resistente frente a los Outliers y de gran utilidad cuando se tiene datos no linealmente separables (modelos no lineales). |
| KNeighborsClassifier| Es simple de implementar, no requiere parámetros como otros modelos y permite un control entre el balanceo entre el sesgo y varianza que pudieran tener los datos debido a que se puede ajustar el número de vecinos (su complejidad) |
### 4. Resultados 
| Problema | Solución |
| :--: | :--: |
| Posibles datos con _overfitting_ en nuestro mejor modelo: Random Forest | En las métricas se notó que podría existir un _overfitting_ de los datos en Random Forest, pero al ser un modelo flexible pudimos confiar en la solución 
## Enlaces Útiles
- #### [Link al Colab (solo profesores)](https://colab.research.google.com/drive/1Nw_dUGjtbyqSekWWKl9ucUqSrzp3orcj?usp=sharing)
- #### [Ver la presentación del proyecto](E5_RetoTitanic.pdf)
