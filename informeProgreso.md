#  Informe de progreso al 25 de Octubre de 2024
Este documento tiene el objetivo de exponer el progreso en el desarrollo del proyecto [RL en State Trakers](https://github.com/afiuriG/textMining/blob/main/README.md). Se presenta el una breve descripción de lo actuado hasta el momento con respecto a cada objetivo planteado en el orden establecido en el documento de presentación de dicho proyecto. 

  
#  Dataset: terminado.
El primero de los objetivos planteados en este proyecto fue el de encontrar un dataset apropiado, incluso antes del 
objetivo general de la conseptualización de la posible aplicación de RL a la resolución de este problema, ya que dicha
conceptualización dependerá del problema específico a resolver dada la naturaleza misma del RL. En este contexto la búsqueda dió como resultado el candidato [Multiwoz](https://arxiv.org/pdf/2007.12720), el cual es el dataset asociado a un sistema de diálogo usuario-máquina, anotado en cada turno con las intensiones del usuario, lo cual facilita las definiciones e implementaciones de RL para la definición y resolución del problema. Además este dataset es muy usado en el ámbito de las implementaciones y pruebas con state trackers lo cual lo convierte en un buen punto de comparación con otras soluciones, de hecho hay un benchmark asociado a él para comparar performances de diferentes soluciones [Dialogue State Tracking on Wizard-of-Oz](https://paperswithcode.com/sota/dialogue-state-tracking-on-wizard-of-oz) y otro propio del autor de la última versión del dataset [Budzianowski et al](https://github.com/budzianowski/multiwoz/blob/master/README.md). En este trabajo se decidió usar como baseline de comparación [NBT](https://arxiv.org/pdf/1606.03777v2) y [TRADE](https://arxiv.org/pdf/1905.08743) respectivamente de cada benchmark, sirviendo este último también como código base para todo el resto del sistema que no sea estrictamente parte del componente state tracker.  

# RL clásico: en progreso.

# RL con inspiración biológica: pendiente.

# Implementación: pendiente.

# Análisis de resultados: inicializado.
Este objetivo ya tiene definido los baselines y el benchmark del cual se extraen pero todavía no hay resultados generados.
