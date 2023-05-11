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

activate base

2. En este ambiente instale mlflow

conda install -c conda-forge mlflow

3. En este ambiente instale sklearn

conda install -c conda-forge scikit-learn
En una terminal aparte lance la interfaz gráfica de MLflow con el comando

mlflow ui
Tome un pantallazo de la salida de la terminal e inclúyalo en su reporte.

La interfaz web debe quedar disponible a través del navegador en el puerto 5000. Abra la ubicación http://localhost:5000 y compruebe que funciona.

Ahora ejecute el notebook mlflow-diab que encontrará en Bloque Neón. Estudie con cuidado el código y describa en su reporte qué hace.

Modifique alguno de los parámetros del modelo y vuelva a correr el modelo.

Ahora visite la interfaz web de MLflow e identifique el experimento y las dos corridas realizadas. Compare los dos modelos en términos de MSE (mean squared error) usando las funciones de la interfaz. Incluya un pantallazo de la comparación en su reporte.

MLflow en Databricks
Inicie creando una cuenta en Databricks Community Edition https://www.databricks.com/try-databricks#account

Provea sus datos y un correo.

En la sección Choose a cloud provider en la parte inferior seleccione Get started with Community Edition.

Valide su correo y genere su contraseña.

Una vez haya creado la cuenta, ingrese con sus credenciales y familiarícese con la consola principal.

En el primer ítem del menú de la izquiera seleccione Data Science and Engineering.

Luego de click en Create - Cluster.

Asigne un nombre al cluster, seleccione un Runtime de ML, en su versión más reciente.

Click en crear cluster y espere a que el cluster se haya creado. Incluya un pantallazo de su clúster operando en su reporte.

En el primer ítem del menú de la izquierda seleccione Machine Learning.

En el menú de la izquierda click en Create - Notebook.

Asigne un nombre al notebook, con lenguaje python por defecto y asígnelo al cluster que acaba de crear.

Con el notebook abierto, copie las instrucciones del notebook mlflow-diab que encontrará en Bloque Neón.

Revise y comprenda las instrucciones de cada celda.

Ejecute cada celda y explore los resultados.

En el menú de la izquierda seleccione Experiments.

Seleccione el experimento realizado y navegue la documentación asociada (versión del modelo, librerías, python).

Cambie los parámetros del entrenamiento del modelo y ejecute un nuevo experimento.

Revise los resultados en Experiments, genere gráficas comparativas. Incluya un pantallazo de las gráficas en su reporte.

Repita este procedimiento varias veces.

Repita este procedimiento con el notebook mlflow-mnist que encontrará en Bloque Neón. Incluya un pantallazo de las gráficas en su reporte.

En su reporte explique en qué consiste este último notebook y los modelos que allí se entrenan. Documente alguna observación sobre sus resultados.