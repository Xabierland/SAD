<!-- markdownlint-disable MD024 -->
<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD029 -->
# Topic Modeling <!-- omit in toc -->

- [Introducción](#introducción)
- [Topic Modeling como Agrupamiento No Supervisado](#topic-modeling-como-agrupamiento-no-supervisado)
  - [K-Means](#k-means)
  - [K-means++](#k-means-1)
  - [Nearest Neighbors](#nearest-neighbors)
  - [LDA](#lda)
  - [LDA - Gibbs Sampling](#lda---gibbs-sampling)
- [Metricas de valoración](#metricas-de-valoración)
  - [Inercia](#inercia)
  - [Coherencia](#coherencia)
    - [U-MASS](#u-mass)
    - [UCI](#uci)
    - [C\_V](#c_v)

# Introducción

El Topic Modeling es:

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

# Metodos estrictos<!-- omit in toc -->

- K-Means
- Nearest Neighbors

## K-Means

El algoritmo K-means es uno de los métodos de agrupamiento (clustering) más populares en el campo del aprendizaje automático y la minería de datos.

### Algoritmo K-means <!-- omit in toc -->

#### Objetivo <!-- omit in toc -->

El objetivo de K-means es dividir un conjunto de datos en $k$ grupos (clusters), de manera que los puntos dentro de cada grupo sean lo más similares posible, y los puntos de diferentes grupos sean lo más distintos posible.

#### Pasos del Algoritmo <!-- omit in toc -->

1. **Inicialización**:
   - Seleccionar $k$ puntos iniciales llamados centroides. Estos centroides pueden ser seleccionados al azar de los datos o según algún criterio específico.

2. **Asignación de Clusters**:
   - Asignar cada punto de datos al centroide más cercano utilizando una medida de distancia (comúnmente la distancia euclidiana). Esto forma $k$ clusters.

3. **Recalcular Centroides**:
   - Calcular la nueva posición de cada centroide como el promedio de los puntos asignados a ese cluster.

4. **Repetición**:
   - Repetir los pasos de asignación de clusters y recalculación de centroides hasta que los centroides no cambien significativamente entre iteraciones o hasta que se alcance un número máximo de iteraciones.

### Limitaciones del K-means <!-- omit in toc -->

- **Sensibilidad a la Inicialización**:
  La calidad de los clusters obtenidos depende fuertemente de la selección inicial de los centroides.
  
- **Clusters Esféricos**:
  El algoritmo asume que los clusters tienen una forma esférica, lo cual puede no ser adecuado para todos los tipos de datos.

- **Número de Clusters**:
  El valor de $k$ debe ser especificado de antemano, lo cual puede no ser trivial en muchos casos.

## K-means++

Para abordar el problema de la sensibilidad a la inicialización de centroides, se introdujo una variante mejorada llamada K-means++.

#### Algoritmo K-means++ <!-- omit in toc -->

1. **Inicialización Inteligente de Centroides**:
   - Seleccionar el primer centroide al azar de los puntos de datos.
   - Para cada punto restante, calcular la distancia mínima al centroide más cercano ya seleccionado. Seleccionar el siguiente centroide con una probabilidad proporcional a esta distancia (es decir, los puntos más distantes tienen una mayor probabilidad de ser seleccionados).
   - Repetir el proceso hasta que se hayan seleccionado $k$ centroides.

2. **Ejecutar K-means**:
   - Una vez que se han seleccionado los $k$ centroides iniciales, continuar con los pasos estándar del algoritmo K-means (asignación de clusters y recalculación de centroides).

#### Ventajas de K-means++ <!-- omit in toc -->

- **Mejor Calidad de Clusters**:
  La inicialización inteligente de centroides mejora la calidad de los clusters, haciendo que el algoritmo converja más rápido y a una solución mejor.
  
- **Reducción de la Variabilidad**:
  Disminuye la probabilidad de obtener clusters de baja calidad debido a malas elecciones iniciales de los centroides.

### Resumen <!-- omit in toc -->

El algoritmo K-means es un método efectivo y simple para la agrupación de datos, aunque tiene sus limitaciones. K-means++ mejora la inicialización de centroides, aumentando la robustez y la calidad de los resultados obtenidos. Al comprender estos algoritmos, se pueden aplicar de manera más efectiva en una variedad de contextos en la ciencia de datos y la minería de datos.

## Nearest Neighbors

> [!NOTE]
> Estoy todavia redactando esta parte y a la espera de que me responda un correo Aitziber porque creo que el algoritmo de Nearest Neighbors no se puede aplicar a clustering. Y que el algoritmo que se nos explico en clase es el de Jerarquico Aglomerativo.

El algoritmo de Vecinos Más Cercanos (Nearest Neighbors) es ampliamente conocido por su uso en clasificación y regresión. Sin embargo, también puede ser aplicado en el contexto de clustering.

### Algoritmo Nearest Neighbors <!-- omit in toc -->

#### Objetivo <!-- omit in toc -->

El objetivo del clustering mediante Nearest Neighbors es agrupar datos en clusters basándose en la proximidad de los puntos de datos entre sí.

#### Pasos del Algoritmo <!-- omit in toc -->



#### Limitaciones <!-- omit in toc -->

- El algoritmo de Vecinos Más Cercanos puede ser computacionalmente costoso, especialmente en conjuntos de datos grandes.
- La búsqueda de vecinos más cercanos puede ser lenta en dimensiones altas debido a la [maldición de la dimensionalidad](https://es.wikipedia.org/wiki/Maldici%C3%B3n_de_la_dimensi%C3%B3n).
  - Se pueden utilizar técnicas de reducción de dimensionalidad para abordar este problema.

# Metodos suaves <!-- omit in toc -->

## LDA

### Algoritmo LDA <!-- omit in toc -->

#### Objetivo <!-- omit in toc -->

El objetivo del algoritmo LDA (Latent Dirichlet Allocation) es descubrir los temas subyacentes en un conjunto de documentos.

LDA se basa en la suposición de que los documentos son generados por una mezcla de temas, y que cada tema es una distribución de palabras. El objetivo de LDA es inferir la distribución de temas en los documentos y la distribución de palabras en los temas.

#### Pasos del Algoritmo <!-- omit in toc -->

1. **Inicialización**:
   - Inicializar aleatoriamente las distribuciones de temas y palabras en los documentos.
2. **Inferencia Variacional**:
   - Se trata de encontrar las distribuciones de temas y palabras que mejor explican los datos observados.
   1. **Definir la distribución variacional**
     - Se define una familia de distribuciones variacionales que aproximan la distribución posterior de los temas y palabras.
   2. **Optimizar los parámetros variacional**
     - Se ajustan los parámetros de la distribución variacional para maximizar la probabilidad de los datos observados.
3. **Evaluar la Convergencia**:
   - Se evalúa la convergencia del algoritmo bien mediante ELBO o mediante la coherencia de los temas.
4. **Obtener las Distribuciones Posteriores**:
   - Una vez que se ha alcanzado la convergencia, se obtienen las distribuciones posteriores de temas y palabras en los documentos.
5. **Inferir los Temas en los Documentos**:
    - Se asignan los temas a los documentos en función de las distribuciones posteriores obtenidas.

#### Limitaciones <!-- omit in toc -->

- Computacionalmente intratable, demasiado costoso.

## LDA - Gibbs Sampling

### Algoritmo LDA - Gibbs Sampling <!-- omit in toc -->

#### Objetivo <!-- omit in toc -->

El algoritmo LDA (Latent Dirichlet Allocation) con Gibbs Sampling es una técnica de aprendizaje no supervisado utilizada para descubrir los temas subyacentes en un conjunto de documentos.

La diferencia con el algoritmo LDA estándar es que en lugar de utilizar métodos de optimización como la inferencia variacional, LDA con Gibbs Sampling utiliza un enfoque de muestreo de Gibbs para estimar las distribuciones de temas y palabras en los documentos.

#### Pasos del Algoritmo <!-- omit in toc -->



#### Limitaciones <!-- omit in toc -->

# Metricas de valoración

## Inercia

La inercia es una métrica comúnmente utilizada para evaluar la calidad de los clusters obtenidos por algoritmos de clustering como K-means.

La inercia mide la suma de las distancias al cuadrado de cada punto al centroide de su cluster. En otras palabras, cuantifica cuán dispersos están los puntos dentro de cada cluster.

Para un conjunto de datos $X$ y un conjunto de centroides $\mu = \{\mu_1, \mu_2, ..., \mu_k\}$, la inercia se calcula como:

$\text{inercia} = \sum_{i=1}^{k} \sum_{x \in C_i} \|x - \mu_i\|^2$

Donde $C_i$ es el conjunto de puntos en el cluster $i$ y $\mu_i$ es el centroide del cluster $i$.

En general, se busca minimizar la inercia para obtener clusters más compactos y bien definidos.

Para conseguir el numero optimo de clusters se puede utilizar el metodo del codo.

El metodo del codo consiste en graficar la inercia en función del numero de clusters y buscar el punto donde la inercia deja de disminuir de forma significativa.

Ese punto es el numero optimo de clusters.

> [!WARNING]
> En los apuntes de la asignatura la formula de la inercia no es correcta del todo ya que lo que calcula es la inercia de un unico cluster y no de todos los clusters. Por si las dudas tambien al estar al cuadrado el orden de restar el elemento al centroide o el centroide al elemento no afecta al resultado.

## Coherencia

La coherencia es una métrica que evalúa la interpretabilidad y calidad de los temas obtenidos mediante algoritmos de topic modeling como LDA.

La coherencia mide cuán semánticamente coherentes son las palabras dentro de un tema. En otras palabras, cuantifica cuán bien las palabras en un tema están relacionadas entre sí.

### U-MASS

La coherencia U-MASS (Umich Cohesion Coherence) es una métrica de coherencia que evalúa la relación semántica entre las palabras en un tema.

La coherencia U-MASS se calcula como la suma de las puntuaciones de coherencia de todas las palabras en un tema. La puntuación de coherencia de una palabra es la suma de las puntuaciones de co-ocurrencia de esa palabra con todas las demás palabras en el tema.

La formula de la coherencia U-MASS es:

$\text{coherencia U-MASS} = \sum_{i=1}^{n} \sum_{j=1}^{n} \text{score}(w_i, w_j)$

Donde $n$ es el número de palabras en el tema, $w_i$ y $w_j$ son palabras en el tema, y $\text{score}(w_i, w_j)$ es la puntuación de co-ocurrencia de las palabras $w_i$ y $w_j$.

La puntuación de co-ocurrencia se calcula como:

$\text{score}(w_i, w_j) = \log \frac{P(w_i, w_j) + \epsilon}{P(w_i)}$

Donde $P(w_i, w_j)$ es la probabilidad de co-ocurrencia de las palabras $w_i$ y $w_j$, y $P(w_i)$ es la probabilidad de la palabra $w_i$.

### UCI

La coherencia UCI (Umass Cohesion Coherence) funciona calculando la coherencia de las palabras en un tema en función de su co-ocurrencia en un corpus de texto.

La coherencia UCI usa la Puntuación de Información Mutua (PMI) para medir la co-ocurrencia de las palabras en un tema. La PMI es una medida de la relación entre dos palabras basada en la probabilidad de que aparezcan juntas en un texto.

La formula de la coherencia UCI es:

$\text{coherencia UCI} = \sum_{i=1}^{n} \sum_{j=1}^{n} \text{PMI}(w_i, w_j)$

Donde $n$ es el número de palabras en el tema, $w_i$ y $w_j$ son palabras en el tema, y $\text{PMI}(w_i, w_j)$ es la puntuación de co-ocurrencia de las palabras $w_i$ y $w_j$.

Este PMI se calcula como:

$\text{PMI}(w_i, w_j) = \log \frac{P(w_i, w_j)+\epsilon}{P(w_i)P(w_j)}$

### C_V

La coherencia C_V (C_V Cohesion Coherence) es una métrica de coherencia que evalúa la relación semántica entre las palabras en un tema.

La coherencia C_V usa la Puntuación de Información Mutua Normalizada (NMPI) para medir la co-ocurrencia de las palabras en un tema. La NMPI es una medida de la relación entre dos palabras basada en la probabilidad de que aparezcan juntas en un texto.

La formula de la coherencia C_V es:

$\text{coherencia CV} = \sum_{i=1}^{n} \sum_{j=1}^{n} \text{NMPI}(w_i, w_j)$

Donde $n$ es el número de palabras en el tema, $w_i$ y $w_j$ son palabras en el tema, y $\text{NMPI}(w_i, w_j)$ es la puntuación de co-ocurrencia normalizada de las palabras $w_i$ y $w_j$.

La puntuación de co-ocurrencia normalizada se calcula como:

$\text{NMPI}(w_i, w_j) = \frac{\text{PMI}(w_i, w_j)}{-\log P(w_i, w_j) + \epsilon}$

o

$\text{NMPI}(w_i, w_j) = \frac{\log \frac{P(w_i, w_j)+\epsilon}{P(w_i)P(w_j)}}{-\log P(w_i, w_j) + \epsilon}$

Donde $\text{PMI}(w_i, w_j)$ es la puntuación de co-ocurrencia de las palabras $w_i$ y $w_j$, y $P(w_i, w_j)$ es la probabilidad de co-ocurrencia de las palabras $w_i$ y $w_j$.

> Mas informacion sobre NMPI [aquí](./.files/Full-Text_or_Abstract_Examining_Topic_Coherence_Scores_Using_Latent_Dirichlet_Allocation.pdf)
