---
title: "Max Verstappen en la Formula 1"
author: "Jose Mª Pérez Marco"
date: "2023-01-12"
categories: [analysis]
image: "Max.jpeg"
---

Max Verstappen es un piloto de automovilismo neerlandés que actualmente pilota en la Fórmula 1 llegándose a considerar para muchos, uno de los 10 mejores pilotos de la historia con tan solo 8 años en la categoría. En 2021 consiguió su primer título mundial en una batalla apasionante con Lewis Hamilton consiguiendo el triunfo en la últia vuelta de la última carrera. Además, en la temporada 2022 ha revalidado el título y ha conseguido varios récords como por ejemplo ser el piloto con mas victorias y podios en una sola temporada. Además, es el piloto más joven en liderar una vuelta durante un Gran Premio de Fórmula 1 y el ganador más joven de un Gran Premio (18 años 7 meses y 15 días en el Gran Premio de España de 2016).
Finalmente fue Red Bull quién se hizo con los servicios del neerlandés con una apuesta arriesgada, ya que significaba sentarlo en un Toro Rosso para el siguiente año cuando el piloto no había completado ni una sola temporada en Fórmulas de promoción. El 3 de octubre de 2014, Verstappen debutaba sobre un Fórmula 1 tomando parte en la primera sesión de entrenamientos libres del GP de Japón, dando comienzo a la etapa en F1 de uno de los pilotos llamados a marcar la próxima generación de la categoría.

**Análisis de sus resultados en carrera**

Como observaremos en el siguiente gráfico, analizaremos las diferentes posiciones y su frecuencia en la que ha conseguido finalizar un Gran Premio a lo largo de su trayectoria en la categoría. Lo más curioso de estas estadísticas es que las dos que más se repiten son la primera posición y el abandono lo que muestra su conducción agresiva que le lleva a tomar muchos riesgos pero que si los soluciona, es capaz de triunfar en la categoría como estos dos últimos años.

```{r}
library(ggplot2)
library(tidyverse)
rdos <- data.frame(
  "posicion" = c(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,"DNF"),
   "veces" = c(35,26,16,14,12,6,5,6,5,3,2,1,0,0,1,1,0,0,0,0,31))

grafico_resultados <- ggplot(rdos) +
  aes(x = reorder(posicion, desc(veces)), y = veces) +
  geom_col(fill = "#112446") +
  labs(
    x = "Posición",
    y = "Frecuencia",
    title = "Resultados de Max Verstappen",
    subtitle = "En su carrera en la F1"
  ) +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 16L,
                              hjust = 0.5),
    plot.subtitle = element_text(size = 13L,
                                 hjust = 0.5)+
      geom_text(aes(label=veces), vjust=0.99,hjust=0.49, color="white",    
                position = position_dodge(0.1),  size=2.0))

grafico_resultados

```


**Victorias de Max Verstappen**

Max ha conseguido subir a lo alto del podio en 35 ocasiones pero nos preguntamos como han estado repartidas en los 8 años de trayectoria. Así observaremos que los dos últimos años, curiosamente cuando se ha coronado campeón, ha conseguido prácticamente el 72% de sus victorias totales. Esto es debido a que, gracias a mucho esfuerzo por parte de Red Bull, han conseguido tener un coche ganador que le permitiera luchar por ello.

```{r}
victorias <- data.frame(
  "año" = c("2015", "2016", "2017", "2018", "2019", "2020", "2021", "2022"),
  "victorias" = c(0,1,2,2,3,2,10,15))


grafico_victorias <- ggplot(victorias) +
  aes(x = año, y = victorias) +
  geom_col(fill = "#440154") +
  labs(x = "Año", 
       y = "Victorias", title = "Victorias de Max Verstappen") +
  theme_minimal() +
  theme(plot.title = element_text(size = 16L, hjust = 0.5))+
geom_text(aes(label=victorias), vjust=0.99,hjust=0.49, color="white",    
          position = position_dodge(0.1),  size=4.0)

grafico_victorias
          
```


**Diferencia de puntos con compañeros de equipo**

A lo largo de su carrera, Verstappen ha tenido 5 compañeros de equipo diferentes los cuales algunos le han exigido más aumentando así la rivalidad entre ellos. El resultado total es que en 6 ocasiones ha salido victorioso de este duelo mientras que solamente dos años se vio superado por su compañero, siendo el mismo piloto en ambas ocasiones, Daniel Ricciardo quien atravesaba su "prime" en ese momento.


```{r}
diferencia_puntos <- data.frame(
  "compañeros" = c("2015Sainz","2016Ricciardo","2017Ricciardo","2018Ricciardo","2019Gasly-Albon", "2020Albon", "2021Pérez", "2022Pérez"),
  "diferencia" = c("+31", "-52", "-32", "+79", "+125", "+120", "+205.5", "+149"))

grafico_diferencia_puntos <- ggplot(diferencia_puntos) +
  aes(x = compañeros, y = diferencia) +
  geom_tile()+
  labs(
    x = "Compañeros de equipo",
    y = "Diferencia de puntos",
    title = "Diferencia de puntos con compañeros"
  ) +
  theme_minimal() +
  theme(plot.title = element_text(size = 15L, hjust = 0.5))
  

grafico_diferencia_puntos
          
```


**Conclusión**

Como hemos podido observar, desde sus inicios, Max Verstappen tuvo un gran impacto en la Formula 1. Además, ha conseguido una evolución bastante favorable adquiriendo experiencia y madurez necesaria para convertirse en bicampeón mundial en los dos últimos años donde su nivel de pilotaje ha llegado a nivel superior al resto de la parilla. Debido a ello, se mira con expectación su futuro puesto que si continua progresando como hasta ahora, puede llegar a convertirse en el mejor piloto de la historia.   Solamente el tiempo lo dirá.
