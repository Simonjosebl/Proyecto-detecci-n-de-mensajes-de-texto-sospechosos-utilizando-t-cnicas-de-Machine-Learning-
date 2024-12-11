# Proyecto detección de mensajes de texto sospechosos utilizando técnicas de Machine-Learning

Método automático para la detección de mensajes de texto sospechosos utilizando​  técnicas de Machine Learning.​

Descripción General

Este proyecto se desarrolló con el objetivo de crear un modelo de Machine Learning que permita clasificar mensajes de texto SMS como sospechosos o no sospechosos. La clasificación se basa en la presencia de palabras clave asociadas con mensajes fraudulentos, como aquellos relacionados con estafas de phishing, robos de identidad, y otros fraudes comunes a través de mensajes de texto.

Objetivo
El principal objetivo es detectar mensajes SMS sospechosos utilizando tres algoritmos de clasificación:

- Naive Bayes
- Random Forest
- Red Neuronal (MLP)

El proyecto permite identificar los mensajes fraudulentos que contienen términos relacionados con riesgos financieros o amenazas a la seguridad personal.

Tecnologías Utilizadas
Para la construcción de este proyecto, se utilizaron varias herramientas y tecnologías que facilitaron la extracción, procesamiento y análisis de los datos:

CoolMonster Assistant: Utilizado para extraer los mensajes de texto de diversos dispositivos móviles. Esta herramienta permitió acceder a aproximadamente 10,000 mensajes SMS, los cuales fueron esenciales para crear el dataset que alimentó los modelos de Machine Learning.

![image](https://github.com/user-attachments/assets/78937d93-e42a-4b9e-acbd-be7f7158eab7)

Python: Para la construcción de los algoritmos de clasificación. Se utilizaron diversas bibliotecas:

- Pandas: Para el manejo y preprocesamiento de datos.
- Scikit-learn: Para implementar los modelos de Machine Learning y realizar la evaluación.
- Numpy: Para la manipulación de datos numéricos.
- Matplotlib y Seaborn: Para la visualización de los resultados y las métricas.
- Jupyter Notebook: Utilizado para el análisis interactivo de datos y la construcción de los modelos.

TF-IDF: Para la vectorización de los mensajes de texto, convirtiéndolos en vectores numéricos que los modelos pueden procesar.

![image](https://github.com/user-attachments/assets/3da893d2-4446-4f3a-a7fd-e589e7f5571f)

Metodología y Fases del Proyecto

1. Extracción de los Datos
Los mensajes de texto fueron extraídos de varios dispositivos móviles mediante la herramienta CoolMonster Assistant. Esta herramienta permitió acceder a los SMS almacenados en los dispositivos y extraer un conjunto de aproximadamente 10,000 mensajes.

Una vez extraídos los mensajes, se construyó un dataset que contiene dos columnas:

Mensaje: El texto del mensaje de texto SMS.
Etiqueta: Una variable binaria que indica si el mensaje es sospechoso (1) o no sospechoso (0).

2. Preprocesamiento de los Datos
El dataset inicial contenía algunos mensajes no etiquetados o con caracteres especiales. Se realizó un proceso de limpieza y preprocesamiento de los datos para asegurar que los textos fueran consistentes y listos para el análisis.

Eliminación de mensajes vacíos o nulos.
Transformación de todos los mensajes a minúsculas para evitar problemas de consistencia.
Eliminación de caracteres especiales y de puntuación innecesaria.
Tokenización de los mensajes, dividiendo cada mensaje en palabras individuales.
El siguiente paso fue etiquetar los mensajes. Los mensajes que contenían palabras clave asociadas a fraudes o amenazas fueron etiquetados como sospechosos (1), mientras que los demás fueron etiquetados como no sospechosos (0). Las palabras clave incluyen términos como:

- Contraseña
- Tarjeta de crédito
- Número de cuenta
- Robos de identidad

3. Balanceo de Datos
Dado que la mayoría de los mensajes en el dataset no eran sospechosos, el conjunto de datos estaba desbalanceado, lo que podría afectar el desempeño de los modelos de clasificación. Para resolver este problema, se utilizó un proceso de balanceo de datos mediante técnicas como:

Submuestreo (Under-sampling): Se redujo el número de mensajes no sospechosos para balancear la distribución de clases.
Sobremuestreo (Over-sampling): En algunos casos, se duplicaron los mensajes sospechosos para equilibrar las clases.
Esto permitió que los modelos no se sesgaran hacia la clase mayoritaria (no sospechosa) y mejoró su capacidad para identificar correctamente los mensajes sospechosos.

4. Vectorización de los Mensajes
   
Para que los modelos pudieran procesar los textos, se utilizó el algoritmo TF-IDF (Term Frequency-Inverse Document Frequency) para convertir los mensajes de texto en vectores numéricos. Este método resalta las palabras más importantes en los mensajes y reduce el peso de las palabras comunes que aparecen en la mayoría de los mensajes, lo cual ayuda a mejorar la clasificación.

6. Construcción y Entrenamiento de los Modelos
Se entrenaron tres modelos de Machine Learning para clasificar los mensajes:

Naive Bayes: Un modelo probabilístico que clasifica mensajes basándose en las probabilidades condicionadas de cada palabra en el mensaje.
Random Forest: Un conjunto de árboles de decisión que votan para predecir la clase del mensaje. Este modelo es muy eficiente en la clasificación de datos desbalanceados.
Red Neuronal (MLP): Una red neuronal que utiliza varias capas de procesamiento para clasificar los mensajes.

6. Evaluación de los Modelos

Análisis de las Matrices de Confusión

![image](https://github.com/user-attachments/assets/6a9ebe6b-ab3d-4415-bdab-9e585e03c659)

1. Modelo Naive Bayes:

Verdaderos Positivos (TP): 32 (Mensajes de texto clasificados correctamente como no spam)
Falsos Positivos (FP): 7 (Mensajes de texto no spam clasificados incorrectamente como spam)
Falsos Negativos (FN): 1 (Mensajes de texto spam clasificados incorrectamente como no spam)
Verdaderos Negativos (TN): 31 (Mensajes de texto spam clasificados correctamente como spam)
Interpretación: El modelo Naive Bayes tiene una buena capacidad para identificar mensajes no spam (con 32 TP), pero también comete algunos errores al clasificar mensajes no spam como spam (7 FP). Sin embargo, el modelo tiene una baja tasa de falsos negativos (solo 1 FN), lo que es positivo ya que muy pocos mensajes spam son clasificados incorrectamente.

2. Modelo Red Neuronal:

Verdaderos Positivos (TP): 29 (Mensajes de texto clasificados correctamente como no spam)
Falsos Positivos (FP): 1 (Mensajes de texto no spam clasificados incorrectamente como spam)
Falsos Negativos (FN): 5 (Mensajes de texto spam clasificados incorrectamente como no spam)
Verdaderos Negativos (TN): 27 (Mensajes de texto spam clasificados correctamente como spam)
Interpretación: El modelo Red Neuronal tiene una tasa de verdaderos positivos (29 TP) similar al modelo Naive Bayes, pero presenta un número mayor de falsos negativos (5 FN). Sin embargo, el modelo también comete muy pocos falsos positivos (1 FP), lo que significa que se equivoca muy raramente al clasificar mensajes no spam como spam. Esto sugiere que la red neuronal tiene un buen balance en términos de precisión y recall.

3. Modelo Random Forest:

Verdaderos Positivos (TP): 30 (Mensajes de texto clasificados correctamente como no spam)
Falsos Positivos (FP): 0 (Ningún mensaje no spam clasificado como spam)
Falsos Negativos (FN): 4 (Mensajes de texto spam clasificados incorrectamente como no spam)
Verdaderos Negativos (TN): 28 (Mensajes de texto spam clasificados correctamente como spam)
Interpretación: El modelo Random Forest tiene un excelente desempeño en términos de precisión (sin falsos positivos), pero presenta una tasa relativamente más alta de falsos negativos (4 FN). Esto significa que, aunque es muy preciso al clasificar mensajes no spam, tiene dificultades para identificar algunos mensajes spam. En general, el modelo parece ser muy conservador en su clasificación de mensajes spam, lo que puede ser ventajoso en escenarios donde minimizar los falsos positivos es crucial.

Evaluación Metricas de desempeño:

![image](https://github.com/user-attachments/assets/fbcdbedf-fecd-494d-8fe6-206173a23d75)

Los modelos fueron evaluados utilizando las siguientes métricas:

Precision: Mide la exactitud de las predicciones positivas.
Recall: Mide la capacidad del modelo para identificar todos los casos positivos.
F1-Score: Métrica combinada de precisión y recall.
Accuracy: La exactitud global del modelo.

Análisis de las Métricas de Desempeño
Modelo Naive Bayes
Precision:

Clase 0 (no spam): 0.96
Clase 1 (spam): 0.82
La precisión es bastante alta para la clase 0, lo que indica que cuando el modelo predice que un mensaje no es spam, lo hace correctamente el 96% de las veces. Sin embargo, la precisión es más baja para la clase 1 (spam), lo que significa que cuando predice que un mensaje es spam, lo hace correctamente el 82% de las veces.

Recall:

Clase 0 (no spam): 0.77
Clase 1 (spam): 0.97
El recall para la clase 1 es muy alto (97%), lo que indica que el modelo es muy eficaz para identificar los mensajes spam, aunque la tasa de recall para la clase 0 es algo baja (77%), lo que sugiere que algunos mensajes no spam son clasificados incorrectamente como spam.

F1-Score:

Clase 0 (no spam): 0.85
Clase 1 (spam): 0.89
El F1-score es una medida combinada de precisión y recall, y ambos valores están bastante equilibrados, lo que indica un buen desempeño general. La clase 1 tiene un F1-score ligeramente superior debido a su alto recall.

Accuracy: 0.87
El modelo Naive Bayes tiene una precisión general del 87%, lo que es bastante bueno, aunque hay espacio para mejorar el manejo de los mensajes no spam.

Modelo Random Forest
Precision:

Clase 0 (no spam): 0.88
Clase 1 (spam): 1.00
El modelo Random Forest tiene una precisión perfecta (100%) para la clase 1, lo que significa que cuando clasifica un mensaje como spam, lo hace correctamente todas las veces. Sin embargo, la precisión para la clase 0 es más baja (88%).

Recall:

Clase 0 (no spam): 1.00
Clase 1 (spam): 0.88
El recall para la clase 0 es excelente (100%), lo que indica que todos los mensajes no spam fueron correctamente identificados. Sin embargo, el recall para la clase 1 es menor (88%), lo que significa que algunos mensajes spam no fueron detectados.

F1-Score:

Clase 0 (no spam): 0.94
Clase 1 (spam): 0.93
Los F1-scores para ambas clases son bastante altos, indicando un buen balance entre precisión y recall. La diferencia entre los F1-scores de ambas clases es pequeña, lo que refleja un buen desempeño general.

Accuracy: 0.94
El modelo Random Forest tiene una precisión general del 94%, lo que es excelente, especialmente dado su manejo efectivo de los mensajes no spam.

Modelo Red Neuronal
Precision:

Clase 0 (no spam): 0.85
Clase 1 (spam): 0.96
El modelo Red Neuronal tiene una buena precisión para la clase 1 (96%), pero la precisión para la clase 0 es más baja (85%), lo que indica que el modelo comete más errores al clasificar mensajes no spam como spam.

Recall:

Clase 0 (no spam): 0.97
Clase 1 (spam): 0.84
El recall para la clase 0 es alto (97%), lo que sugiere que el modelo es bueno para identificar mensajes no spam. Sin embargo, el recall para la clase 1 es más bajo (84%), lo que significa que algunos mensajes spam no son detectados.

F1-Score:

Clase 0 (no spam): 0.91
Clase 1 (spam): 0.90
El F1-score es muy equilibrado entre ambas clases, con valores cercanos (0.91 para la clase 0 y 0.90 para la clase 1), lo que sugiere un buen desempeño general para el modelo Red Neuronal.

Accuracy: 0.90
El modelo Red Neuronal tiene una precisión general del 90%, lo que es excelente, pero con un pequeño desequilibrio entre las clases en términos de recall.

Conclusiones de las Métricas:

Naive Bayes tiene una buena precisión para la clase 0, pero su desempeño podría mejorar en cuanto a recall para la clase 0.
Random Forest es el modelo con la mayor precisión y recall generales, especialmente para la clase 1 (spam), aunque su recall para la clase 1 es ligeramente inferior.
Red Neuronal ofrece un buen balance general, con un desempeño sólido en ambas clases, aunque su recall para la clase 1 es algo menor en comparación con los otros modelos.
Cada modelo tiene sus fortalezas y debilidades, y la elección del modelo final dependerá de los objetivos específicos del proyecto, como priorizar la precisión de la clasificación o la detección eficaz de mensajes spam.

7. Resultados y Conclusiones

![image](https://github.com/user-attachments/assets/81004cd8-3973-4671-b0d6-c4a387685514)

Mejor Modelo (Segun el desempeño general):

Random Forest tiene el mejor desempeño global, con una precisión de 0.94 y un recall del 100% para la clase 0 (no spam), lo que lo convierte en el modelo más robusto en términos de accuracy y balance entre precisión y recall para ambas clases. Sin embargo, presenta una pequeña baja en el recall para la clase 1 (88%).
Modelo más Equilibrado:

Red Neuronal es el modelo que muestra un buen balance entre precisión y recall, especialmente para la clase 1 (spam), con un F1-score alto en ambas clases (0.91 para clase 0 y 0.90 para clase 1). Aunque su recall para la clase 1 es algo inferior al de Random Forest, sigue siendo un modelo muy eficiente con un accuracy del 90%, lo que lo convierte en una excelente opción si se busca un buen balance.
Naive Bayes:

Naive Bayes tiene la precisión más baja para la clase 1 (spam) y un recall relativamente bajo para la clase 0. Aunque presenta un accuracy de 87%, su desempeño es inferior al de los otros modelos en la clasificación de spam y no spam.
Recomendación Final:
Si la prioridad es la precisión general y la detención efectiva de spam, Random Forest es el modelo con el mejor rendimiento, aunque se debe considerar que puede haber una ligera desventaja en la detección de algunos mensajes spam (bajo recall de la clase 1).
Si el objetivo es encontrar un equilibrio entre precisión y recall en ambas clases (sin priorizar demasiado una clase sobre la otra), la Red Neuronal es una excelente opción debido a su alto F1-score y accuracy equilibrados.
En resumen, Random Forest puede ser considerado el mejor modelo debido a su precisión global y recall perfecto para la clase 0, pero Red Neuronal también ofrece un excelente balance y sería una opción sólida si se prioriza un modelo más equilibrado.

