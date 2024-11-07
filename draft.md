# Intro...
Los Spoken Dialogue Systems (SDS), o sistemas de diálogo en castellano, permiten a los usuarios interactuar con aplicaciones de computadora a traves de conversaciones. Los sistemas de ayuda basados en tareas ayudan a alcanzar las metas tales como obtener plazas de comida o reservar servicios tales como taxis o vuelos. El seguimiento del estado del diálogo o Dialogue State Tracking en inglés (DST) es un componente clave de un SDS que sirve para interpretar una entrada del usuario y actualizar si hace falta la creencia del estado del diálogo i.e. su intención, en cada turno del mismo. Es decir que el state tracker implementa la representación interna del sistema del estado de la conversación (Young et al., 2010). Esta información es usada por el manejador de diálogos para decidir que acción debería tomar el sistema.
En este trabajo se analiza la posibilidad de construir un state tracker utilizando RL clásico y RL con inspiración biológica. Se buscó un conjunto de datos rotulados acorde a esta problemática y se pensaron posibles experimentos bajo la asunción de que es posible tal construcción y se estudiaron métricas y baselines para comparar resultados.
En lo que sigue se describen cada una de las componentes del trabajo y se presentan discusiones al respecto. Para mejorar la organización tanto en la lectura como en el mantenimiento se profundizan dichos componentes en documentos separados.



# El dataset
Esta componente describe el dataset seleccionado para trabajar, el cual establece también el problema a resolver. Luego de analizar varios candidatos se eligió [Multiwoz](....) ya que es bastante usado en el ámbito de state tracking y se encuentran métricas y baselines para poder comparar. Está basado en diálogos (en inglés) usuario-máquina orientado a tareas. Plantea un escenario multi dominio (Restaurant, Attraction, Hotel, Taxi, Train, Bus, Hospital, Police) con los servicios de búsqueda o reserva (en algunos de ellos). Sobre este dataset es que se estudiará la construcción de un state tracker definiendo así el problema a resolver como se dijo con anterioridad. Los diálogos se encuentran rotulados (en cada turno) con el estado que necesita mantener el state tracker, dependiendo de la intensión del usuario y de las características de su intensión (llamadas slot) o sea por ejemplo el usuario podría estar buscando información (intensión) acerca del hotel "America" y en este caso el estado que mantiene el state tracker debería mantener alguna especie de representación que defina para el domino "Hotel" el slot "name" debe tener el valor "America" y que la intensión es la de busqueda de información (a diferencia de la intensión de reserva por ejemplo). 
Para profundizar en sus características ver [datase seleccionado](https://github.com/afiuriG/textMining/blob/main/datset.md)

# El problema

Antes de comenzar con definiciones de la solución es necesario describir con mayor presición el problema, se parte de un dataset de diálogos rotulados con los estados del diálogo en cada turno y se pretende construir una piesa de software que ante el texto correspondiente a un turno del usuario genere el estado del diálogo para ese momento. Además se pretende encontrar una solución con RL así que el environment será una caja negra que ofrece como descriptor de estado una mezcla entre el estado del diálogo y la entrada del turno, un reward será calculado a partir de calcular el acercamiento del estado de diálogo calculado y el rotulado y por último habrán acciones que cambiarán (o no) el estado del diálogo, para ver más detalles de la definición del problema ver ["el problema"](https://github.com/afiuriG/textMining/blob/main/problem.md)


# El modelo
## Reinforcement Learning
Esta es una parte crucial del proyecto, es momento de definir con presición cual es el modelo de aprendizaje que se usará y construir las entidades que fueron apareciendo. Por un lado hay que definir la descripción del estado del environment introducido informalmente antes, el cual a su vez está definido como una composición del turno corriente y del estado del diálogo. También se necesita detalles sobre el reward, el cual será alguna noción de cercanía entre el estado del diálogo calculado y el rotulado. Por último también hay que identificar las acciones que el agente puede hacer sobre el entono las cuales serán intuitivamente los cambios en los slots o la intensión asociados al diálogo. En ["el modelo"](https://github.com/afiuriG/textMining/blob/main/modelo.md) están los detalles de tales definiciones.

## Aprendizaje - RL Clásico
Una vez que se definieron todos estos conceptos recién podemos hablar del mecanismo de aprendizaje. Como primera alternativa se presenta el Reinforcement Learning Clásico, donde con "clásico" se intenta contrastar con la propuesta del RL con inspiración biológica. En principio en esta prueba de factibilidad se elige la técnica de diferencia temporal profunda dada la generalidad de situaciones en la que es aplicable, apostando que también lo sea para este problema. Para mas detalles ver [DeepQN](https://github.com/afiuriG/textMining/blob/main/dqn.md)   

## Aprendizaje - RL con inspiración biológica.
El RL con inspiración biológica es una propuesta propia en el que se modela el funcionamiento de una red neuronal artificial fuertemente orientada a aspectos biológicos tales como conexiones con diferentes comportamientos (inhibitorias, exitatorias, eléctricas), dinámica neuronal basada en comportamiento eléctrico de las neuronas y por tanto neuronas con estado interno, arquitectura neuronal motivada en circuitos biológicos, etc. Para mas detalles ver [Fnets](https://github.com/afiuriG/textMining/blob/main/fnets.md)



# Implementación
To be done...

# Métricas y Benchmarks
Para poder discutir el éxito o no del método es necesario primero definir que métricas serán tenidas en cuenta y luego buscar puntos de comparación con benchmarks en el estado del arte, en este sentido se usaran 2 fuentes de comparación a saber:
[Dialogue State Tracking on Wizard-of-Oz Benchmarks](https://paperswithcode.com/sota/dialogue-state-tracking-on-wizard-of-oz) gestionado por [paperswithcode.com](https://paperswithcode.com/sota), en este benchmark se usa como métrica Joint Goal Accuracyh (ver usos y definición de [JGA](https://arxiv.org/pdf/2204.03375) para más detalles). Por otro lado [Paweł Budzianowski](https://github.com/budzianowski/multiwoz/blob/master/README.md) en el sitio en el que mantiene oficialmente el dataset de Multiwoz también ofrece su ranking de métricas basadas en la estandar JGA. Para más detalles acerca del análisis de resultados obtenidos ver ...  



#  Referencias......
- Steve Young, Milica Gasiˇ c, Simon Keizer, Franc¸ois Mairesse, Jost Schatzmann, Blaise Thomson, and
Kai Yu. 2010. The hidden information state model: A practical framework for POMDP-based spoken dialogue management. Computer Speech and Language 24:150–174.
- NBT as Baseline: https://arxiv.org/pdf/1606.03777v2
- Multiwoz: https://arxiv.org/pdf/2007.12720
- RL for data augmentation: https://arxiv.org/pdf/1908.07795
- A state tracking benchmark: https://paperswithcode.com/sota/dialogue-state-tracking-on-wizard-of-oz
- RL clásico: Sutton, R.S., Barto, A.G.: Reinforcement Learning: An Introduction., MIT Press., Cambridge., (1998)
- RL con inspiración biológica: https://link.springer.com/chapter/10.1007/978-3-031-63616-5_5
- Deep Qlearning: https://www.datacamp.com/es/tutorial/introduction-q-learning-beginner-tutorial
- Deep Qlearning: https://huggingface.co/learn/deep-rl-course/unit3/deep-q-algorithm
- JGA: Suvodip Dey, Ramamohan Kummara, Maunendra Sankar Desarkar. Towards Fair Evaluation of Dialogue State Tracking by Flexible Incorporation of Turn-level Performances: https://arxiv.org/pdf/2204.03375
- 





 prueba de factibilidad?
