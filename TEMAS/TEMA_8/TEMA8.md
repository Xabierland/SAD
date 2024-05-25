<!-- markdownlint-disable MD025 -->

# Tema 8 <!-- omit in toc -->

# Introducción

El analisis de sentimientos es:

> Aplicación de algoritmos supervisados de aprendizaje automático o basados en reglas con objeto de identificar automaticamente la opinión subyacentes en textos.

Los algoritmos supervisados de aprendizaje automático se basan en un conjunto de datos de entrenamiento que contiene ejemplos de texto con su correspondiente etiqueta de sentimiento.
Los algoritmos basados en reglas se basan en un conjunto de reglas que se aplican a los textos para determinar el sentimiento.
Algunos de los algoritmos más comunes son:

- K-Nearest Neighbors
- Decision Trees
- Random Forest
- Naive Bayes
- Regresión logística

En otras palabras:
> El analisis de sentimientos es el proceso para determinar la opinión de un autor sobre un tema o producto a partir de un texto.

# Aplicaciones

Tanto en redes sociales como en foros los clientes dan su opinión sobre productos o servicios.
El analisis de sentimientos permite a las empresas conocer la opinión de los clientes y mediante el `topic modeling` identificar los productos o servicios que más interesan a los clientes.

# Analisis de sentimientos

El proceso de analisis de sentimientos es el siguiente:

1. Obtener los datos (textos)
2. Procesar los datos
   1. Eliminar iconos
   2. Eliminar simbolos
   3. Normalizar el texto (minusculas, eliminar tildes, etc.)
3. Elegir el metodo de clasificación
   1. Basado en reglas
      1. Se definen listas de palabras polarizadas
      2. Se calcula la frecuencia de dichas palabras en el texto
      3. Si las positivas superan a las negativas, el texto es positivo, y viceversa
   2. Automático
   3. Híbrido
4. Se entrena el modelo
   1. Se extraen las características de los textos
      1. tf-idf...
   2. Se pasan por un algoritmo de machine learning
      1. Naive Bayes Multinomial...
5. Se evalua
   1. No solo tenemos porque buscar si es positivo, neutro o negativo.
      1. Podemos buscar emociones: alegria, tristeza, miedo, enfado, etc.
      2. Urgencia: si es urgente o no
      3. Intenciones: interesado, no interesado, etc.
