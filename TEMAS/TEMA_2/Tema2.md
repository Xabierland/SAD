<!-- markdownlint-disable MD004-->
# Tema 2

- [Tema 2](#tema-2)
  - [Algoritmos de aprendizaje](#algoritmos-de-aprendizaje)
  - [Exploracion de datos](#exploracion-de-datos)
  - [Tipos de datos](#tipos-de-datos)
    - [Ejercicios: ¿Que tipos de Datos?](#ejercicios-que-tipos-de-datos)
  - [Representacion de datos](#representacion-de-datos)
  - [Preprocesado de los datos](#preprocesado-de-los-datos)
    - [Ejercicios: ¿Que valores son faltantes, erroneos, necesitan ser escalados?](#ejercicios-que-valores-son-faltantes-erroneos-necesitan-ser-escalados)
  - [Tratar texto](#tratar-texto)

## Algoritmos de aprendizaje

1. Aprendiza supervisado - Los datos de entrenamiento incluyen la salida esperada
    1. Clasificacion
        1. Clasificacion binaria
        2. Clasificacion multiclase
    2. Regresion
2. Aprendizaje no supervisado - Los datos de entrenamiento no incluyen la salida esperada
    1. Clustering
    2. Asociacion

## Exploracion de datos

* Tamaño de la muestra
* Numero de atributos
* Tipos de atributos
* Medidas estadisticas
* Numero de valores unicos
* Valores atipicos
* Valores perdidos

## Tipos de datos

* Numericos
  * Discretos
    * [1,2,3,...]
  * Continuos
    * [1.1,1.2,1.3,...]
* Categoriales
  * Nominales
    * [rojo,verde,azul,...]
  * Ordinales
    * [bajo,medio,alto,...]

### Ejercicios: ¿Que tipos de Datos?

* Altura
  * Continuo
* Edad
  * Discreto
* Color Cabello
  * Nominales
* Dominio de ingles
  * Ordinales

## Representacion de datos

* Histogramas
* Grafico de Barras

## Preprocesado de los datos

* Obtencion de los datos
  * Quien tiene los datos
  * Cuales son los datos relevantes
* Limpiar los datos
  * Tratas los valores faltantes
    * Borrarlos
    * Imputarlos - Reemplazarlos por un valor
      * Media
      * Moda
      * Prediccion
  * Identificar y reducir el ruido
    * Suavizar los datos
    * Eliminar los valores atipicos
  * Encontrar y eliminar datos erroneos
* Transformar los datos
  * Normalizar los datos
    * Escalar valores
      * Relativizar con respecto al maximo
      * Relativicar con respecto al maximo y minimo
      * Z-scale - Relativizar con respecto a la media y la desviacion estandar
  * Discretizar los datos
    * Agrupar los datos
    * Por amplitud
  * Generar nuevos atributos
* Reducir los datos
  * Reducir numero de atributos
  * Reducir numero de registros
  * Equilibrar los datos
    * Undersampling
      * Eliminar registros de la clase mayoritaria
      * Eliminar instancias que esten cerca a las de la clase minoritaria (Tomek Links)
    * Oversampling
      * Duplicar registros de la clase minoritaria
      * Generar instancias sinteticas de la clase minoritaria (SMOTE)

### Ejercicios: ¿Que valores son faltantes, erroneos, necesitan ser escalados?

* Faltantes:
  * Miren Lopetegi - Edad
  * Jorge Zelaia - Edad
  * Mireia Baztan - Edad
* Erroneos:
  * Joseba Lakarra - Edad
  * Itziar Ganbara - Edad

## Tratar texto

* BOW (Bag of Words)
  * Se toman todas las palabras del todos los documentos y se genera un vector con la frecuencia de cada palabra
* tf-idf (Term Frequency - Inverse Document Frequency)
  * tf - Frecuencia de la palabra en el documento
  * idf - Forma de ponderar la frecuencia de la palabra en el documento
* hashing
