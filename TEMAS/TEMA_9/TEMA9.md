<!-- markdownlint-disable MD025 -->
# Topic Modeling <!-- omit in toc -->

- [Introducción](#introducción)
- [Topic Modeling como Agrupamiento No Supervisado](#topic-modeling-como-agrupamiento-no-supervisado)
  - [Metodos estrictos](#metodos-estrictos)
    - [K-Means](#k-means)
    - [Nearest Neighbors](#nearest-neighbors)
  - [Metodos suaves](#metodos-suaves)
    - [LDA](#lda)
    - [LDA - Gibbs Sampling](#lda---gibbs-sampling)


# Introducción

El `topic modeling` es:

> Aplicación de algoritmos de agrupamiento/clustering no supervisados con objeto de identificar automaticamente los temas subyacentes en textos.

Se basa en la idea de que los documentos son una mezcla de temas y que cada tema es una distribución de palabras. Por lo tanto, el objetivo es encontrar los temas y las palabras que los definen.

# Topic Modeling como Agrupamiento No Supervisado

La no supervisión se basa en encontrar patrones en los datos sin la necesidad de etiquetas durante el entrenamiento.

El clustering, por otro lado, es descubrir grupos en base a similitudes entre los datos.

Existen dos tipos de metodos de agrupamiento:

- Estrictos
  - Un item solo puede pertenecer a un cluster
    - Una palabra solo puede pertenecer a un tema
- Suaves
  - Un item puede pertenecer a varios clusters
    - Una palabra puede tener aparecer en varios temas

## Metodos estrictos

### K-Means

### Nearest Neighbors

## Metodos suaves

### LDA

- Latent Dirichlet Allocation
- Modelo generativo (como Naive Bayes)
- Busca maximizar la probabilidad de que los documentos sean generados por los temas
  - Teniendo en cuenta la probabilidad de que los temas generen las palabras
  - Y la probabilidad de que los documentos generen las palabras
- Funcionamiento
  - Un documento es la distribucion de temas/topicos

### LDA - Gibbs Sampling

- Algoritmo de muestreo de Gibbs
- Funcionamiento
  - Se asigna aleatoriamente un tema a cada palabra
  - Se actualiza la asignacion de temas de cada palabra
  - Se repite el proceso hasta que converja
