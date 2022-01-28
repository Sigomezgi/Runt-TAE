
![](https://upload.wikimedia.org/wikipedia/commons/5/53/UNAL_Aplicaci%C3%B3n_Medell%C3%ADn.svg)

<center> <h1> Predicción del número de vehículos registrados en el sistema de tránsito (RUNT) </h1> </center>
<center> <h4> Juan Daniel Bula Isaza - Bryan Garcia Villa - Simón Gómez Giraldo - Carolina Quintero Osorio </h4> </center>
<center> <h5> 17 de Enero de 2022 </h5> </center>

## Resumen
<p align = "justify"> El RUNT se define como un sistema de gestión que permite registrar y mantener actualizada, centralizada, autorizada y validada la información sobre los registros de automotores, conductores, licencias de tránsito, empresas de transporte público, infractores, seguros, entre otros. Se trata de un sistema que está siendo actualizado constantemente, girando alrededor de un sistema centralizado de información de tránsito y transporte el cual opera bajo un esquema de colaboración que depende de la información provista, en línea y en tiempo real. </p>

<p align = "justify">El gran objetivo de este trabajo es la implementación de un modelo que permita predecir el número de vehículos registrados diariamente en el Registro Único Nacional de Tránsito (RUNT), utilizando como insumo principal la base de datos proporcionada para su elaboración, con el nombre de registros_autos, la cual incluye la fecha y el número de registros de vehículos en determinada fecha. </p>

## Introducción

<p align = "justify"> El Registro Único Nacional de Tránsito, es un sistema que permite consolidar y actualizar la información del registro de tránsito, la cual garantiza una alta confiabilidad y transparencia en los procesos. Su idea está concebida como una solución en la que se integran grandes bases de datos con información, permitiendo registrar, validar y autorizar de una forma unificada cada uno de los trámites.  </p>

<p align = "justify">La creación de un modelo que permita predecir el número de vehículos registrados diariamente, puede ser de gran utilidad para el organismo de tránsito de la ciudad, ya que con dicha información se puede replantear futuros mecanismos en la metodología de registros, también obtener datos de gran utilidad, como la cantidad aproximada de vehículos registrados en un determinado año a futuro, lo que podría conducir a la implementación de nuevas medidas de tránsito, también se podría analizar qué días puntuales se ven reflejados cambios drásticos en números de registros en el RUNT. </p>

## Justificación de variables

<p align = "justify"> La base de datos que tenemos como insumo para analizar e implementar modelos predictivos, contiene 2 columnas con las variables Fecha dato numérico de fecha y Unidades dato entero real. </p>

La estructura de las variables que contiene los datos es la siguiente:
![tenden](https://user-images.githubusercontent.com/94578395/148704601-0c3ed295-07ba-495e-985a-8db25a3427c2.jpg)

<p align = "justify"> Se observa que cada mes es variable en su incremento de inscripción de vehículos, sin embargo, en los últimos años la cantidad de registros ha ido disminuyendo parcialmente. Se aprecia que, durante los meses de noviembre, diciembre, enero, febrero y marzo la cantidad de registros es creciente; una hipótesis que explica este hecho podría ser que se solapamiento de las vacaciones académicas con ingresos extras en los hogares colombianos, pues se espera que la mayoría de las inscripciones corresponden a personas que cumplen la edad requerida para sacar la licencia de conducción. Un acontecimiento para resaltar es que para los años 2012, 2013, 2014 y 2015 existe un crecimiento en el número de registros para el mes de julio que se explicaría a través de la hipótesis anteriormente planteada, sin embargo, este patrón desapareció para los años 2016 y 2017. </p>

![days](https://user-images.githubusercontent.com/94578395/148704453-100ed4b3-a84d-45ca-b6ba-7cdb4fd5c90a.jpg)



<p align = "justify"> El gráfico anterior muestra la distribución de las inscripciones a lo largo de la semana. Las inscripciones son uniformes a lo largo de la semana y se ha mantenido a lo largo de los años. Hay una disminución en los sábados y domingos que corresponde con la reducción de la carga laboral. Las barras de cada día aumentan de izquierda a derecha para los años en los que se analiza la base de datos. </p>


## Metodología
Se creo un modelo de predicción de los registros diarios RUNT. Para esto se crean las variables:
  - **Día de la semana**: Al ser una plataforma que depende del horario normal laboral, la cantidad de registros puede variar a lo largo de la semana.
  - **Época de vacaciones**: Se espera que los mayores registros RUNT corresponden a aquellas personas que sacan su licencia de conducción por primera vez, y existe la tendencia de expedirlo recién se cumple la edad requerida. Los estudiantes sacan provecho del tiempo de vacaciones para realizar este procedimiento.
  - **Festivo**: Corresponde si el día es festivo en Colombia o no.

<p align = "justify"> Se evalúa el comportamiento de la predicción para varios modelos, principalmente:
Regresión lineal, regresión de bosques aleatorios, K vecinos más cercanos, Regresión Lasso.
El rendimiento del modelo se evalúo con el R2. Obteniéndose el más alto para el modelo de regresión de bosques aleatorios. Sin embargo, se sintonizaron dos modelos: Bosque aleatorio y Regresión lineal. El primero porque fue el de mejor rendimiento y el segundo para evaluar su comportamiento con una sintonización de parámetros más detallada por su característica inferencial. </p>

<p align = "justify"> A pesar de que los resultados de sintonización mejoraron el R2 de la regresión lineal, los bosques aleatorios exhiben un mejor comportamiento en casi un 20% mejor que el primero, por lo tanto, el modelo a implementar para la predicción es, Bosques aleatorios. </p>


## Comportamiento del modelo

<p align = "justify"> Para sintonizar el modelo se crea una malla de posibles valores dada la primera aproximación otorgada de forma automática. Esto se puede observar en notebook, Runt entrenamiento.ipny </p>

<p align = "justify"> La importancia de las variables seleccionadas en el modelo se presenta a continuación:  </p>

![variables](https://user-images.githubusercontent.com/94578395/148703836-1456dc68-13bf-44df-a45f-708bd70af129.jpg)

<p align = "justify"> Se aprecia que no existe una gran diferencia en el aporte de información de las variables seleccionados, a excepción de la variable vacaciones esto se explica a que este período no fue detallado estrictamente. </p>

<p align = "justify"> La base de datos consta de registros desde el año 2012 al 2017, se realiza un particionamiento para el data set de prueba para los años 2012 hasta 2016 mientras que para el data set de prueba corresponde al 2017. Al sintonizar los parámetros se obtiene un R2 para la data set de entrenamiento de R2 = 78% y para el data set de prueba se obtiene R2= 70 %. Las predicciones para valores futuros se pueden observar en el aplicativo web que se adjunta al final del informe. </p>

![scatter](https://user-images.githubusercontent.com/94578395/148703559-ccb55a04-33fb-4a81-b3b2-1ed1f2fc79f5.png)

## Conclusión y trabajos futuros

<p align = "justify"> La existencia de una base de datos con los registros del RUNT es una buena práctica para tomar medidas de control y optimizar el proceso, sin embargo, se cuenta con muy poco detalle en la inscripción de cada registro lo cual limita la creación de variables explicativas que mejoren el rendimiento del modelo. Para trabajos futuros se espera indagar más sobre el fenómeno a predecir, pues se sospecha la existencia de acontecimientos o funcionamiento interno que puede ayudar a predecir mucho la cantidad de registros y que solo se puede tener en cuenta con la ayuda de un experto. </p>

## Nota evaluador.

En el repositorio se encuentran dos cuadernos .ipny . El primero [Runt entrenamiento](https://github.com/Sigomezgi/Runt-TAE/blob/main/Runt%20entrenamiento.ipynb) que es aquel donde se detalla la derivación y la elección del modelo y el segundo es [Runt test](https://github.com/Sigomezgi/Runt-TAE/blob/main/Runt%20test.ipynb) que es donde se realizan las predicciones para el primer semestre del 2018. Los datos se disponen en una tabla html para una correcta previsualización en el repositorio, sin embargo, se exportaron los resultados en el archivo [predicciones.xlsx](https://github.com/Sigomezgi/Runt-TAE/blob/main/Predicciones.xlsx) que también se disponen en git.

## Archivos planos

## Referencias
  - James, G., Witten, D., Hastie, T., & Tibshirani, R. (2013). *An introduction to statistical learning (Vol. 112, p. 18). New York: springer.*
  - Ospina J. (2019) *Introducción a la analítica predictiva, Vehículos registrados en el RUNT. Material de clase especialización en Analítica Unal.*
  - Stack Overflow - Where Developers Learn, Share, & Build Careers. (n.d.). Retrieved January 17, 2022, de: [Stackoverflow](https://stackoverflow.com/)
  - Hacia la ciencia de datos. (n.d.). Retrieved January 17, 2022, de: [Towards Data Science](https://towardsdatascience.com/)
  - FrikisparaGeeks | Un portal de informática para geeks. (n.d.). Retrieved January 17, 2022, de: [Geeks for geeks](https://www.geeksforgeeks.org/)
  - pandas - Biblioteca de análisis de datos de Python. (n.d.). Retrieved January 17, 2022, de: [Pandas](https://pandas.pydata.org/)
  - Mısra Turp - YouTube. (n.d.). Retrieved January 17, 2022, de: [Misra Turp](https://www.youtube.com/c/Soyouwanttobeadatascientist)
  - RUNT (2019). RUNT EN CIFRAS. Obtenido de: [RUNT](https://www.runt.com.co/)
  
 ## Aplicativo Web
  - [RUNTapp](https://share.streamlit.io/sigomezgi/apliacacion-runt/Main.py)

