# Intro...
Los Spoken Dialogue Systems (SDS), o sistemas de diálogo en castellano, permiten a los usuarios interactuar con aplicaciones de computadora a traves de conversaciones. Los sistemas de ayuda basados en tareas ayudan a alcanzar las metas tales como obtener plazas de comida o reservar servicios tales como taxis o vuelos. El seguimiento del estado del diálogo o Dialogue State Tracking en inglés (DST) es un componente clave de un SDS que sirve para interpretar una entrada del usuario y actualizar si hace falta la creencia del estado del diálogo i.e. su intención, en cada turno del mismo. Es decir que el state tracker implementa la representación interna del sistema del estado de la conversación (Young et al., 2010). Esta información es usada por el manejador de diálogos para decidir que acción debería tomar el sistema.
En este trabajo se analiza la posibilidad de construir un state tracker utilizando RL clásico y RL con inspiración biológica. Se buscó un conjunto de datos rotulados acorde a esta problemática y se pensaron posibles experimentos bajo la asunción de que es posible tal construcción y se estudiaron métricas y baselines para comparar resultados.
En lo que sigue se describen cada una de las componentes del trabajo y se presentan discusiones al respecto. Para mejorar la organización tanto en la lectura como en el mantenimiento se profundizan dichos componentes en documentos separados.



# Dataset
Esta componente describe el dataset seleccionado para trabajar, el cual establece también el problema a resolver. Luego de analizar varios candidatos se eligió [Multiwoz](....) ya que es bastante usado en el ámbito de state tracking y se encuentran métricas y baselines para poder comparar. Esta basado en diálogos ()en inglés) usuario-máquina orientado a tareas. Plantea un escenario multi dominio (Restaurant, Attraction, Hotel, Taxi, Train, Bus, Hospital, Police) con los servicios de búsqueda o reserva (en algunos de ellos). Sobre este dataset es que se estudiará la construcción de un state tracker definiendo así el problema a resolver como se dijo con anterioridad. Los diálogos se encuentran rotulados con el estado que necesita mantener el state tracker, dependiendo de la intensión del usuario y de las características de su intensión (llamadas slot) o sea por ejemplo el usuario podría estar buscando información acerca del hotel "America" y en este caso el estado que mantiene el state tracker debería mantener alguna especie de representación que defina para el domino "Hotel" el slot "name" debe tener el valor "America" y que la intensión es la de busqueda de información (a diferenci de la intensión de reserva por ejemplo). 
Para profundizar en sus características ver [datase seleccionado](https://github.com/afiuriG/textMining/blob/main/datset.md)

# Model del problema


# Métodos

# Implementación

# Métricas y Benchmarks


#  Referencias......

