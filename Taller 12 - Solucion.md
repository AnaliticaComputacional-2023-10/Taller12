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

4. En una terminal aparte lance la interfaz gráfica de MLflow con el comando

mlflow ui

Tome un pantallazo de la salida de la terminal e inclúyalo en su reporte.

5. La interfaz web debe quedar disponible a través del navegador en el puerto 5000. Abra la ubicación http://localhost:5000 y compruebe que funciona.

6. Ahora ejecute el notebook mlflow-diab que encontrará en Bloque Neón. Estudie con cuidado el código y describa en su reporte qué hace.

7. Modifique alguno de los parámetros del modelo y vuelva a correr el modelo.

8. Ahora visite la interfaz web de MLflow e identifique el experimento y las dos corridas realizadas. Compare los dos modelos en términos de MSE (mean squared error) usando las funciones de la interfaz. Incluya un pantallazo de la comparación en su reporte.

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



11. En el primer ítem del menú de la izquierda seleccione Machine Learning.

12. En el menú de la izquierda click en Create - Notebook.

13. Asigne un nombre al notebook, con lenguaje python por defecto y asígnelo al cluster que acaba de crear.

14. Con el notebook abierto, copie las instrucciones del notebook mlflow-diab que encontrará en Bloque Neón.

15. Revise y comprenda las instrucciones de cada celda.

16. Ejecute cada celda y explore los resultados.

17. En el menú de la izquierda seleccione Experiments.

18. Seleccione el experimento realizado y navegue la documentación asociada (versión del modelo, librerías, python).

19. Cambie los parámetros del entrenamiento del modelo y ejecute un nuevo experimento.

20. Revise los resultados en Experiments, genere gráficas comparativas. Incluya un pantallazo de las gráficas en su reporte.

21. Repita este procedimiento varias veces.

22. Repita este procedimiento con el notebook mlflow-mnist que encontrará en Bloque Neón. Incluya un pantallazo de las gráficas en su reporte.

23. En su reporte explique en qué consiste este último notebook y los modelos que allí se entrenan. Documente alguna observación sobre sus resultados.