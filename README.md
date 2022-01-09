# Runt-TAE
## Predicción del número de vehículos registrados en el sistema de tránsito nacional
El RUNT se define como un sistema de gestión que permite registrar y mantener actualizada, centralizada, autorizada y validada la información sobre los registros de automotores, conductores, licencias de tránsito, empresas de transporte público, infractores, seguros, entre otros. Se trata de un sistema que está siendo actualizado constantemente, girando alrededor de un sistema centralizado de información de tránsito y transporte el cual opera bajo un esquema de colaboración que depende de la información provista, en línea y en tiempo real.
El gran objetivo de este trabajo es la implementación de un modelo que permita predecir el número de vehículos registrados diariamente en el Registro Único Nacional de Tránsito (RUNT), utilizando como insumo principal la base de datos proporcionada para su elaboración, con el nombre de registros_autos_entrenamiento, la cual incluye la fecha y el número de registros de vehículos en determinada fecha.
## Introducción
El Registro Único Nacional de Tránsito, es un sistema que permite consolidar y actualizar la información del registro de tránsito, la cual garantiza una alta confiabilidad y transparencia en los procesos. Su idea está concebida como una solución en la que se integran grandes bases de datos con información, permitiendo registrar, validar y autorizar de una forma unificada cada uno de los trámites.
La creación de un modelo que permita predecir el número de vehículos registrados diariamente, puede ser de gran utilidad para el organismo de tránsito de la ciudad, ya que con dicha información se puede replantear futuros mecanismos en la metodología de registros, también obtener datos de gran utilidad, como la cantidad aproximada de vehículos registrados en un determinado año a futuro, lo que podría conducir a la implementación de nuevas medidas de tránsito, también se podría analizar qué días puntuales se ven reflejados cambios drásticos en números de registros en el RUNT.
## Justificación de variables
La base de datos que tenemos como insumo para analizar e implementar modelos predictivos, contiene 2 columnas con las variables Fecha dato numérico de fecha y Unidades dato entero real.
La estructura de las variables que contiene los datos es la siguiente:
IMAGEN
Se observa que cada mes es variable en su incremento de inscripción de vehículos, sin embargo, en los últimos años la cantidad de registros ha ido disminuyendo parcialmente. Se aprecia que, durante los meses de noviembre, diciembre, enero, febrero y marzo la cantidad de registros es creciente; una hipótesis que explica este hecho podría ser que se solapamiento de las vacaciones académicas con ingresos extras en los hogares colombianos, pues se espera que la mayoría de las inscripciones corresponden a personas que cumplen la edad requerida para sacar la licencia de conducción. Un acontecimiento para resaltar es que para los años 2012, 2013, 2014 y 2015 existe un crecimiento en el número de registros para el mes de julio que se explicaría a través de la hipótesis anteriormente planteada, sin embargo, este patrón desapareció para los años 2016 y 2017.
![alt text](https://github.com/Sigomezgi/Runt-TAE/blob/main/days.jpg)

IMAGEN
