# Taller 12

### Versionamiento de modelos - MLflow

##### Analítica Computacional para la Toma de Decisiones

---

|     Nombres      |      Apellidos       |     Login     |  Codigo   |
| :--------------: | :------------------: | :-----------: | :-------: |
|     Santiago     | Gonzalez Montealegre | s.gonzalez35  | 202012274 |
| Juliana Carolina |  Cardenas Barragan   | jc.cardenasb1 | 202011683 |

---

---

## Pre-requisitos

---

**Nota:** defina un nombre para su grupo, defínalo claramente en reporte y use este nombre como parte inicial de todos los recursos que cree.

**Nota 2:** la entrega de este taller consiste en un reporte y unos archivos de soporte. Cree el archivo de su reporte como un documento de texto en el que pueda fácilmente incorporar capturas de pantalla, textos y similares. Puede ser un archivo de word, libre office, markdown, entre otros.

---

## Instale y pruebe MLflow localmente

1. En su ambiente local active un ambiente de python. Por ejemplo, usando Anaconda en consola puede activar el ambiente base con el comando

```
activate base
```

2.. En este ambiente instale mlflow

```
conda install -c conda-forge mlflow
```

3. En este ambiente instale sklearn

```
conda install -c conda-forge scikit-learn
```

4. En una terminal aparte lance la interfaz gráfica de MLflow con el comando

```
mlflow ui
```

Tome un pantallazo de la salida de la terminal e inclúyalo en su reporte.

![Salida Termina](/Image/1.4.png)

5. La interfaz web debe quedar disponible a través del navegador en el puerto 5000. Abra la ubicación http://localhost:5000 y compruebe que funciona.

6. Ahora ejecute el notebook mlflow-diab que encontrará en Bloque Neón. Estudie con cuidado el código y describa en su reporte qué hace.

```
# Importe el conjunto de datos de diabetes y divídalo en entrenamiento y prueba usando scikit-learn
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_diabetes

db = load_diabetes()
X = db.data
y = db.target
X_train, X_test, y_train, y_test = train_test_split(X, y)
```

En la primera parte del código se importa el conjunto de datos de diabetes y se divide en conjuntos de entrenamiento y prueba utilizando la biblioteca ``scikit-learn``.

Luego asigna las características (X) y la variable de interes (y) de la base de datos y realiza la división utilizando la función ``train_test_split()``.

Los conjuntos resultantes son ``X_train, X_test, y_train, `` y ``y_test``, que se utilizarán para entrenar y evaluar modelos de aprendizaje automático.

```
#Importe MLFlow para registrar los experimentos, el regresor de bosques aleatorios y la métrica de error cuadrático medio
import mlflow
import mlflow.sklearn
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error

# defina el servidor para llevar el registro de modelos y artefactos
mlflow.set_tracking_uri('http://localhost:5000')
# registre el experimento
experiment = mlflow.set_experiment("sklearn-diab")

# Aquí se ejecuta MLflow sin especificar un nombre o id del experimento. MLflow los crea un experimento para este cuaderno por defecto y guarda las características del experimento y las métricas definidas. 
# Para ver el resultado de las corridas haga click en Experimentos en el menú izquierdo. 
with mlflow.start_run(experiment_id=experiment.experiment_id):
    # defina los parámetros del modelo
    n_estimators = 200 
    max_depth = 6
    max_features = 4
    # Cree el modelo con los parámetros definidos y entrénelo
    rf = RandomForestRegressor(n_estimators = n_estimators, max_depth = max_depth, max_features = max_features)
    rf.fit(X_train, y_train)
    # Realice predicciones de prueba
    predictions = rf.predict(X_test)
  
    # Registre los parámetros
    mlflow.log_param("num_trees", n_estimators)
    mlflow.log_param("maxdepth", max_depth)
    mlflow.log_param("max_feat", max_features)
  
    # Registre el modelo
    mlflow.sklearn.log_model(rf, "random-forest-model")
  
    # Cree y registre la métrica de interés
    mse = mean_squared_error(y_test, predictions)
    mlflow.log_metric("mse", mse)
    print(mse)
```
En la segunda parte del código se comienza importando las bibliotecas MLflow para registrar experimentos y métricas, el regresor de bosques aleatorios y la métrica de error cuadrático medio.

Luego se establece la URI de seguimiento de MLflow para especificar el servidor donde se registrarán los modelos y los artefactos y se registra un nuevo experimento llamado ``"sklearn-diab"`` en MLflow.

Se inicia una nueva ejecución de MLflow dentro del experimento especificado. Se definen los parámetros del modelo de bosques aleatorios, como el número de estimadores, la profundidad máxima y el número máximo de características, a partir de estos se crea un modelo de bosques aleatorios y se entrena utilizando los conjuntos de entrenamiento.

Se realizan las predicciones utilizando el modelo entrenado en los datos de prueba. Se registran los parámetros y el modelo de bosques aleatorios en MLflow. Se calcula el error cuadrático medio entre las predicciones y los valores reales de prueba. Registrando este valor en MLflow y imprimiendolo en la consola.

7. Modifique alguno de los parámetros del modelo y vuelva a correr el modelo.

8. Ahora visite la interfaz web de MLflow e identifique el experimento y las dos corridas realizadas. Compare los dos modelos en términos de MSE (mean squared error) usando las funciones de la interfaz. Incluya un pantallazo de la comparación en su reporte.

Los dos experimentos realizados se muestran a continuación:
![Experimentos](/Image/1.81.png)

Comparación MSE entre los experimentos realizados:
![Comparación](/Image/1.82.png)

**Experimento 1:**

![E1](/Image/1.83.png)

**Experimento 2:**
![E2](/Image/1.84.png)

## MLflow en Databricks

1. Inicie creando una cuenta en Databricks Community Edition https://www.databricks.com/try-databricks#account

2. Provea sus datos y un correo.

3. En la sección **Choose a cloud provider** en la parte inferior seleccione **Get started with Community Edition.**

4. Valide su correo y genere su contraseña.

5. Una vez haya creado la cuenta, ingrese con sus credenciales y familiarícese con la consola principal.

6. En el primer ítem del menú de la izquiera seleccione Data Science and Engineering.

7. Luego de click en Create - Cluster.

8. Asigne un nombre al cluster, seleccione un Runtime de ML, en su versión más reciente.

10. Click en crear cluster y espere a que el cluster se haya creado. Incluya un pantallazo de su clúster operando en su reporte.

![Cluster](/Image/2.10.png)

11.  En el primer ítem del menú de la izquierda seleccione Machine Learning.

12.  En el menú de la izquierda click en Create - Notebook.

13.  Asigne un nombre al notebook, con lenguaje python por defecto y asígnelo al cluster que acaba de crear.

14.  Con el notebook abierto, copie las instrucciones del notebook mlflow-diab que encontrará en Bloque Neón.

15.  Revise y comprenda las instrucciones de cada celda.

16. Ejecute cada celda y explore los resultados.

17. En el menú de la izquierda seleccione Experiments.

18. Seleccione el experimento realizado y navegue la documentación asociada (versión del modelo, librerías, python).

19. Cambie los parámetros del entrenamiento del modelo y ejecute un nuevo experimento.

20. Revise los resultados en Experiments, genere gráficas comparativas. Incluya un pantallazo de las gráficas en su reporte.



21. Repita este procedimiento varias veces.

22. Repita este procedimiento con el notebook mlflow-mnist que encontrará en Bloque Neón. Incluya un pantallazo de las gráficas en su reporte.

23. En su reporte explique en qué consiste este último notebook y los modelos que allí se entrenan. Documente alguna observación sobre sus resultados.