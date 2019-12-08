# Gestión de la Espera

En una gestión eficaz de las operaciones, la capacidad de las instalaciones, la del equipamiento y la del personal de servicio estarán equilibradas unas con otras, y todas ellas con la demanda. De forma similar, la secuencia de las operaciones estará diseñada para minimizar el riesgo de cuellos de botella en cualquier punto del proceso.

Este ideal, sin embargo, puede ser muy difícil de alcanzar. No sólo el nivel de demanda fluctúa, a menudo de manera aleatoria, sino que el tiempo y el esfuerzo requeridos para procesar cada persona u objeto varía mucho en cualquier punto del proceso, por lo que en definitiva, esperar es parte del proceso.

En este módulo veremos algunas estrategias que nos permiten “almacenar” la demanda y gestionar la espera de tal manera que la percepción satisfactoria de los clientes hacia el servicio no se vea afectada. Para comenzar, veamos el video en el que se desarrollan los contenidos fundamentales que necesitás comprender:

[Ver video](https://youtu.be/DfBOz5Y9Pz0)

Quizás todos tengan experiencias en las que han tenido que esperar para poder utilizar o recibir un servicio. Tolerar largos tiempos de espera es una de las causas más comunes de insatisfacción de los clientes.

## Introducción al análisis de filas

>¿Por qué se producen las filas?
>¿Es posible modelarlas?
>¿Qué costos deberíamos balancear al momento de diseñar la gestión de una fila?
>¿Qué información es necesaria para modelar una fila?
>¿Qué tipos de filas podemos identificar?

¡Las filas son aborrecidas por los clientes! Se producen esencialmente por las diferencias entre el flujo al que arriban los clientes al servicio y las variaciones internas del proceso, porque no siempre se demora lo mismo para atender a un cliente.

Si bien los clientes no se presentan a demandar el servicio a una tasa constante, tampoco lo hacen a una totalmente aleatoria. A la hora de almorzar, el flujo de clientes a un restaurante es bastante predecible entre determinadas horas; fuera de ellas, la variabilidad aumenta.

En términos de la variabilidad interna, claramente no es fácil predecir exactamente cuánto demorará un odontólogo en obturar una muela; depende del paciente y las circunstancias. Tendríamos una excelente información para mejorar la gestión de estas indeseadas filas si pudiéramos modelarlas para pronosticar su comportamiento. Básicamente esto puede lograrse incorporando algunos modelos matemáticos o haciendo simulaciones.

La posibilidad de contar con herramientas para guiar el diseño de las filas será fundamental, puesto que están en juego dos costos muy importantes: el costo del servicio y el costo de esperar. El costo de servicio tenderá a subir cuando menor sea la espera. Intuitivamente podemos inferir que un servicio sin espera implica un diseño con mucha capacidad para que siempre haya disponibilidad para prestar el servicio; pero claro, eso es caro. Implicaría gimnasios con muchas máquinas, por las dudas venga mucha gente, restoranes con muchas mesas y camareros, etc.

Por otro lado, esperar también tiene un costo para el cliente. Su tiempo vale, deja de hacer otras cosas mientras espera. Del adecuado balance de estos costos dependerá el éxito de la propuesta. Si representamos estos costos con dos funciones en un plano Tasa de Servicio vs. Costo, obtenemos el siguiente gráfico:

![Tasa de Servicio vs. Costo](https://lh5.googleusercontent.com/8FpIJrxeH9dsjBazv4VWibQGK8yxlgWDzERq7oR-erB3yPL8Nz2MQGOX4R4L_C2Q8bSX6G13RRbysbNyHojxiTp9zBqwOIiDO3j55s8s_4q2Ox6oZK3swTqzCzfyRyVtCH9NwEQ5)

El costo del servicio es lineal, sube proporcionalmente al nivel de servicio. El costo de esperar no es lineal; el costo percibido por el cliente baja a medida que el nivel de servicio sube, pero a un ritmo cada vez menor a medida que el nivel de servicio sube. La sensibilidad de los clientes no será la misma en los distintos servicios, pero nos sirve esta idea para entender la situación a la que nos enfrentamos.

Aclarados estos conceptos, es posible pensar en modelar estos procesos para obtener información que optimice su gestión. Como se menciona en el video, el modelo más común para estudiar los arribos a una cola es el de la Distribución de Poisson. Este modelo nos brinda, dada una tasa promedio de arribos `λ` (lamda), la probabilidad de que un cierto número de clientes X, arribe en una determinada ventana de tiempo.

Por su parte, el modelo más común para estudiar la distribución de servicios es la Distribución Exponencial. Dado un tiempo promedio de servicio `µ` (mu), esta distribución nos determina la probabilidad de que el tiempo de servicio exceda un determinado tiempo t.

La distribución de Poisson y la Exponencial pertenecen a la familia de las Marcovianas. También suelen usarse para la tasa de servicios la distribución uniforme o constante, o distribuciones que pueden ser caracterizadas por la media y la varianza, como la Distribución Normal y la Distribución Gamma.

La Notación de Kendall es un método estándar para describir las filas. Con cinco letras se describe un sistema de cola: A/B/s/M/P. Donde:

- A: es la distribución de probabilidad de los arribos (la más común M, Marcoviana de Poisson). 
- B: es la distribución de probabilidad del tiempo de servicio (la más común M, Marcoviana Exponencial). Si fuese uniforme o constante se una la letra D. Si es una caracterizable por media y varianza se denota con la letra G.
- s: es el número de servidores.
- M: es el largo máximo de la cola. Si no se indica se supone es grande, tendiendo a infinito.
- P: es el tamaño de la población. Si no se indica se supone es grande, tendiendo a infinito.

Es decir, si tenemos un sistema de filas con arribos de Poisson, tiempo de servicio Exponencial y un servidor, lo denotaríamos: M/M/1

Si fuesen tres líneas con arribos de Poisson, tiempo de servicio Exponencial y un servidor: 3M/M/1.

Si fuese 3 líneas con arribos Poisson, tiempo de servicio Exponencial y 3 servidores: 3M/M/3. Luciría así:

![Poisson](https://lh3.googleusercontent.com/6QIKaNkylRqioQEcyVsAUbNyVYf99z1jLEXbxDiDRe0sC6WLFLereLj77o9-1y6nfnUKJfd_cLYy14a-12gUSClLRRAO9oW23-ui7eE60gD-3l93EHc1Uh4j-Pz-CdGX3QWHMqoP)

En la misma situación, si solo se admitieran 4 clientes como máximo en la cola y la población de clientes fuese 20, lo denotaríamos: M/M/3/4/20.

Para completar esta sección, introducimos una [hoja de Excel](https://drive.google.com/file/d/1TrQJq6pmbmGVal4nIY84Xksn6suU3Vhc/view?usp=sharing) que nos ayudará con los cálculos. Primero miremos el modelo `M / M / s`. Exploramos un escenario de ejemplo en el que necesitamos encontrar el número óptimo de servidores para una empresa, una cafetería. ¿Cuántos baristas contratar? Al hacerlo, desarrollamos una tabla de datos para analizar el costo y decidir.

Este es un caso típico de análisis de una situación M/M/s: llegadas de clientes siguiendo una distribución de Poisson, tasa de servicio siguiendo una distribución Exponencial (por eso dos letras M en la notación de Kendall) en la que hay que determinar el s óptimo.

La tasa media de arribos l= 4 clientes por minuto. La tasa media de servicio µ = 2 clientes por minuto, por barista. El costo de esperar es de $60  por minuto y el de servicio $15 por barista

Mirá el [video en el que trabajamos sobre la hoja de cálculo](https://youtu.be/VjxeB-0VCcU) y te enseñamos a hacer los ejercicios.

Ahora introduciremos el modelo M / D / 1 (es decir, Marcovianos los arribos y Uniforme la tasa de servicio con un servidor). Utilizando el modelo M / D / 1, exploramos la decisión de recapitalización de una empresa. En este caso se trata de un lavadero de autos. Es decir, estamos analizando si conviene hacer una inversión que, de acuerdo a los datos de la tabla ubicada más abajo, mejorará el tiempo de servicio, aunque aumentará algo el costo de servicio. Queremos determinar cuál es el monto máximo que estaría dispuesto a pagar por el nuevo lavadero. Al analizar esta decisión, utilizamos el análisis de “Búsqueda de objetivo". También nos interesa saber cuál debería ser la nueva tasa de arribos de autos para justificar la inversión.

## Una cuestión de percepción

El tiempo juega un rol muy importante en la mayoría de los servicios, por lo que debe ponerse mayor atención a la comprensión de cómo los clientes lo perciben, presupuestan, consumen y valoran. Al construir la lealtad con los clientes, la satisfacción en el tiempo de espera es casi tan importante como la satisfacción en el servicio.

[Ver video](https://youtu.be/IPxBKxU8GIQ)

La siguiente infografía presenta a modo de síntesis una de las cuestiones trabajadas en este módulo y te servirá para resolver la actividad que te proponemos a continuación:

<div style="width: 100%;"><div style="position: relative; padding-bottom: 200.94562647754137%; padding-top: 0; height: 0;"><iframe frameborder="0" width="746.4705882352941" height="1500" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://view.genial.ly/5cfa817ce0a8e60f67c44339" type="text/html" allowscriptaccess="always" allowfullscreen="true" scrolling="yes" allownetworking="all"></iframe> </div> </div>