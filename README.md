# RL en State Trakers


# Resumen
Los Spoken Dialogue Systems (SDS), o sistemas de diálogo en castellano, permiten a los usuarios interactuar con aplicaciones de computadora a traves de conversaciones. Los sistemas de ayuda basados en tareas ayudan a alcanzar las metas tales como obtener plazas de comida o reservar servicios tales como taxis o vuelos. El seguimiento del estado del diálogo o Dialogue State Tracking en inglés (DST) es un componente clave de un SDS que sirve para interpretar una entrada del usuario y actualizar si hace falta la creencia del estado del diálogo i.e. su intención, en cada turno del mismo. Es decir que el state tracker implementa la representación interna del sistema del estado de la conversación (Young et al., 2010). Esta información es usada por el manejador de diálogos para decidir que acción debería tomar el sistema.
En este trabajo se analiza la posibilidad de construir un state tracker utilizando RL clásico y RL con inspiración biológica. Se busca un conjunto de datos rotulados acorde a esta problemática y se piensan posibles experimentos bajo la asunción de que es posible tal construcción. Al momento de esta redacción no se conoce con certeza la probabilidad de éxito pero en tal caso se recolectarán métricas y se comparará con baselines del área.

# Hipótesis de trabajo
Se puede aplicar RL y RL con inspiración biológica a problemas de state trackers.

# Objetivos
Estudiar y conceptualizar la aplicación de RL y RL con inspiración biológica en state trackers.
- Encontrar un dataset apropiado.
- Estudiar la posibilidad de aplicación de RL
- Conceptualizar dicha aplicación.
- Estudiar la posibilidad de aplicación de RL con inspiración biológica.
- Conceptualizar dicha aplicación.
- Implementar alguna o ambas de dichas versiones.
- Recojer métricas acordes y comparar con baselines del área de state trackers.

# Técnicas a aplicar
RL, RL con inspiración biológica.

# Justificación
En el procesamiento de diálogos el RL aparece como una alternativa natural.

# Referencias
- Steve Young, Milica Gasiˇ c, Simon Keizer, Franc¸ois Mairesse, Jost Schatzmann, Blaise Thomson, and
Kai Yu. 2010. The hidden information state model: A practical framework for POMDP-based spoken dialogue management. Computer Speech and Language 24:150–174.
- NBT as Baseline: https://arxiv.org/pdf/1606.03777v2
- Multiwoz: https://arxiv.org/pdf/2007.12720
- RL for data augmentation: https://arxiv.org/pdf/1908.07795
- A state tracking benchmark: https://paperswithcode.com/sota/dialogue-state-tracking-on-wizard-of-oz
- RL clásico: Sutton, R.S., Barto, A.G.: Reinforcement Learning: An Introduction., MIT Press., Cambridge., (1998)
- RL con inspiración biológica: https://link.springer.com/chapter/10.1007/978-3-031-63616-5_5

