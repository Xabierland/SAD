# Topic Modeling

## Introducción

## Topic Modeling como Agrupamiento No Supervisado

### Metodos estrictos

- Solo puede haber un tema por documento

#### K-Means

#### Nearest Neighbors

### Metodos suaves

- Un documento puede tener varios temas

#### LDA

- Latent Dirichlet Allocation
- Modelo generativo (como Naive Bayes)
- Busca maximizar la probabilidad de que los documentos sean generados por los temas
  - Teniendo en cuenta la probabilidad de que los temas generen las palabras
  - Y la probabilidad de que los documentos generen las palabras
- Funcionamiento
  - Un documento es la distribucion de temas/topicos

#### LDA - Gibbs Sampling

- Algoritmo de muestreo de Gibbs
- Funcionamiento
  - Se asigna aleatoriamente un tema a cada palabra
  - Se actualiza la asignacion de temas de cada palabra
  - Se repite el proceso hasta que converja
