# Laboratoria
## 🎧Proyecto-Spotify
Este repositorio se encuentran los datos del proyecto que analiza un conjunto de datos para validar o refutar una serie de hipotesis y conocer que causas influyen en el exito de una cancion.

![71q7l9vTrnL _AC_UF1000,1000_QL80_](https://www.cronista.com/files/image/674/674320/64fb09dfe478d.jpg)


# 📑Temas

- [Introducción](#introducción)
- [Hipótesis a validar o refutar](#hipótesis-a-validar-o-refutar)
- [Objetivo](#objetivo)
- [Equipo](#equipo)
- [Herramientas de apoyo](#herramientas-de-apoyo)
  - [Procesamiento de los datos](#procesamiento-de-los-datos)
  - [Análisis exploratorio](#análisis-exploratorio)
  - [Validación de hipótesis](#validación-de-hipótesis)
- [Resultados](#resultados)
- [Conclusiones](#conclusiones)
- [Recomendaciones](#recomendaciones)

## 📄Introducción

En un mundo en el que la industria musical es extremadamente competitiva y está en permanente evolución, la capacidad de tomar decisiones basadas en datos se ha convertido en un activo invaluable.

En este contexto, una discográfica se enfrenta al emocionante desafío de lanzar un nuevo artista en el escenario musical global. Afortunadamente, cuenta con una herramienta poderosa en su arsenal: un extenso dataset de Spotify con información sobre las canciones más escuchadas en 2023, con el que se trabajó para valida o refutar las cinco hipótesis que la discografía planteo. 

## 📈Hipótesis a validar o refutar

 + Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify.
 + Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
 + La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
 + Los artistas con un mayor número de canciones en Spotify tienen más streams.
 + Las características de la música influyen en el éxito en términos de cantidad de streams en Spotify.
 + Las canciones con más cantidad de veces en playlist de Spotify tienen un comportamiento similar en otras plataformas como Deezer o Apple.

## 🎯Objetivo
 El objetivo es que la discográfica y el nuevo artista puedan tomar decisiones informadas que aumenten sus posibilidades de conseguir el “éxito”.
 
## 👩🏻‍🤝‍👩🏻Equipo
- [Frida Castillo](https://github.com/Fri21)
- [Jaqueline Mera](https://github.com/JaquelineMera)

## ⚙Herramientas de apoyo
<details>
<summary> ⚙️ Lenguajes </summary>

+ SQL
+ Python

</details>

<details>
<summary> ⚙️ Herramientas </summary>

+ Google BigQuery
+ Google Colab
+ Google Slides
+ Google Looker Studio

</details>


## 💻Procesamiento de los datos
+ Identificar valores nulos a través COUNTIF e IS NULL.
+ Identificar duplicados a través de COUNT, GROUP BY, HAVING.
+ Manejar variables que no son útiles en el análisis a través de EXCEPT.
+ Identificar datos discrepantes en variables categóricas con REGEXP_REPLACE.
+ Identificar datos discrepantes en variables numéricas con MAX, MIN y AVG.
+ Comprobar y modificar tipos de datos con SAFE_CAST y CAST.
+ Crear nuevas variables utilizando CONCAT, SUM y DATE. 
+ Construir tablas auxiliares utilizando WITH.
+ Unir las tablas utilizando LEFT JOIN.

## 🔎Análisis exploratorio
+ Agrupar datos según variables categóricas a través de tablas
+ Visualizar las variables categóricas a través de gráficos de barras y líneas 
+ Aplicar medidas de tendencia central en BPM, Playlists y Streams
+ Aplicar medidas de dispersión BPM, Playlists y Streams
+ Visualizar distribución a través de Hitogramas BPM, Playlists y Streams
## ✔Validación de hipótesis

La validación de hipótesis se llevó a cabo en BigQuery y Google Colab
+ Análisis de correlación entre métricas (Coeficiente de Pearson)
  
Regresión Lineal Simple
+ Error Cuadrático Medio (MSE)
+ Coeficiente de Determinación (R²)
+ Precisión del modelo
## 📃Resultados
+ 🔴**H1**: Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify.
    + **Conclusión**: No hay relación lineal significativa entre los BPM de una canción y su popularidad  en términos de streams.
      + *Coeficiente de Pearson* (-0.0023): Hay una correlación negativa extremadamente débil (casi nula).
      + *Regresión lineal simple*: Modelo Inadecuado, no hay una relación lineal significativa entre BPM y Streams; Coeficiente de determinación R² (-0.0013).
        
+ 🟢**H2**: Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
    + **Conclusión**: Las canciones que son populares en los ranking de Spotify también tienden a ser populares en otras plataformas como Deezer, Apple y Shazam. Sin embargo, el modelo de regresión lineal no puede usarse como modelo predictivo pues solo explica el 30% de esta variabilidad en Deezer y el 14% en Apple y Shazam.
      +  *Coeficiente de Pearson* (Dezzer 0.6051; Apple 0.5518; Shazam 0.6056): Existe una correlación positiva moderada entre el ranking de las canciones en Spotify y otras plataformas.
      +  *Regresión lineal simple*: Relación moderada entre la presencia en los charts de Spotify y otras plataformas. Sin embargo, un R² 0.303 indica en Deezer que el 30.3% de la variabilidad en "In Spotify Charts" puede explicarse por "In Deezer Charts“. Para Apple el R² es de 0.1403 y para Shazam de 0.1407.
# Hipótesis 1 Refutada y 2 Validada
![db2](https://github.com/user-attachments/assets/21c75983-e0aa-4674-b763-8ce435d5a242)
+ 🟢**H3**: La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
    + **Conclusión**: La inclusión en playlists es un factor importante que impulsa el número de streams de una canción. El modelo de regresión lineal puede usarse como modelo predictivo, nos explica el 67% de los casos.
      + *Coeficiente de Pearson* (0.7833): Existe una fuerte correlación positiva entre el número de streams y la cantidad de veces que una canción aparece en playlists. 
      + *Regresión lineal simple*: Relación fuerte entre el número de "Total playlist" y "Streams". Un R² de aproximadamente 0.670 indica que el 67% de la variabilidaden "Streams" puede explicarse por "Total playlist".
 + 🟢**H4**: Los artistas con un mayor número de canciones en Spotify tienen más streams.
    + **Conclusión**: A medida que el número de canciones de un artista aumenta, el total de streams también tiende a aumentar . Sin embargo, el modelo de regresión lineal no es adecuado para predecir el total de streams basándose en el total de canciones, puesto que existen muchos casos de canciones únicas con alta cantidad de streams.
      + *Coeficiente de Pearson*(-0.0536): Existe una correlación positiva fuerte entre el total de streams y el total de canciones.
      + *Regresión lineal simple*: El modelo no es adecuado para predecir "Total streams" basándose en "Total canciones". Coeficiente de determinación R² (-0.0536)
# Hipótesis 3 Validada y 4 Validada
![db3](https://github.com/user-attachments/assets/ae5f26c5-2e4e-491b-9c0d-ee8192ce61ff)
 + 🔴**H5**: Las características de la música influyen en el éxito en términos de cantidad de streams en Spotify. Aplicable en “Danceability y Speechiness”
    + **Conclusión**: La bailabilidad y número de elementos hablados en una canción tiene muy poco en la popularidad medida por streams. A valores bajos de estas características, ligeramente hay más streams.
      + *Coeficiente de Pearson* (Danceability -0.1055; Speechiness -0.1128): Hay una correlación negativa débil entre el número de streams, la bailabilidad y el número de elementos hablados en una canción.
      + *Regresión lineal simple*: Relación muy débil, modelo inadecuado.
## Hipótesis 5 Refutada
![db4](https://github.com/user-attachments/assets/36609086-9877-4586-b28e-1bbe3350ce89)


## 📄Conclusiones
Al validar y refutar las hipótesis se puede determinar que dentro de los factores que influyen principalmente en el éxito de una canción destaca el hecho de que aquellas canciones que se posicionan en los primeros lugares de los rankings provienen de artistas con una mayor cantidad de canciones; así también un factor determinante es aquel que tiene que ver con la publicidad y la cantidad de plataformas en las que se encuentra publicada una canción.
De esta manera se descarta la premisa de que las características técnicas de una canción influyan en su éxito.

## 📝Recomendaciones
+ Lanzar una canción en varias plataformas de streaming (Spotify, Deezer y Apple, principalmente).
+ Se sugiere que el artista a despuntar cuente con más de una canción.
+ Dar promoción para tener presencia en un mayor número de playlist.

## 🌐Enlaces

### [Presentación](https://drive.google.com/file/d/1ByA65mDGVs__wQtR2OKMfRdaS6oTMKe1/view?usp=sharing)
### [Dashboard](https://drive.google.com/file/d/1aWTPEtqaZA3NkA82V5d4XnCke3YhU540/view?usp=sharing)
### [Video](https://www.loom.com/share/11ab5f29c6824351a116a8de530a6c9e?sid=7f22661d-77fe-4439-aa52-69fc54293ffe)
