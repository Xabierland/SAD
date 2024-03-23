<!-- markdownlint-disable MD004 -->
# Tema 3 - Evaluación

- [Tema 3 - Evaluación](#tema-3---evaluación)
  - [Objetivos de Aprendizaje](#objetivos-de-aprendizaje)
  - [¿Como validamos nuestros modelos/algoritmos?](#como-validamos-nuestros-modelosalgoritmos)
    - [Ejercicio - ¿Que son los epochs?](#ejercicio---que-son-los-epochs)
    - [Ejercicio - ¿Calcular las metricas?](#ejercicio---calcular-las-metricas)

## Objetivos de Aprendizaje

* Ser capaces de estimar la calidad de un modelo
* Conocer los esquemas de evaluacion
  * no-honesta
  * hold-out
  * k-fold-cross validation

## ¿Como validamos nuestros modelos/algoritmos?

* Se debe encontrar una forma de medir la calidad de un modelo
  * Que errores se cometen
  * Overfitting
    * Alimentar el modelo con datos de más
    * No es capaz de generalizar
* Suponiendo una muestra de n elementos
  * La salida sera de tamaño n
  * Mirando el valor que da con el real podemos ver el error
* Epoch
  * El numero de veces que pasamos por el conjunto de datos
* Learning rate
  * La cantidad de aprendizaje que se aplica en cada paso
  * Si es muy grande, puede pasarse del mínimo
  * Si es muy pequeño, puede tardar mucho en converger
* Evaluaciones
  * no-honesta
    * Se entrena con un conjunto de datos y se evalua con el mismo
  * honesta
    * Se divide el conjunto de datos en dos se entrena con uno y se evalua con otro
  * k-fold
    * Cuando no se tiene suficientes datos
    * Se divide el conjunto de datos en k partes
    * Se entrena con k-1 y se evalua con la restante
    * Se hace k veces
    * Se promedian los resultados
* Particion de datos
  * Aleatoria
  * Estratificada
  * Desbalanceados

### Ejercicio - ¿Que son los epochs?

Primera aproximación - Aprobado con 8

> Hay un error en Jorge Zelaia porque el aprobado seria con un 8 pero el 6 deberia ser aprobado

Segunda aproximación - Aprobado con &

> Ya no da error

### Ejercicio - ¿Calcular las metricas?

| | Prediccion Gato | Prediccion Perro |
| --- | --- | --- |
| Valor real Gato | 990 | 0 |
| Valor real Perro | 10 | 0 |

* Precision - 99%
* Recall - 100%
* F-Score - 99.49%
