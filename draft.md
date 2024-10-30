# Intro...
Los Spoken Dialogue Systems (SDS), o sistemas de diálogo en castellano, permiten a los usuarios interactuar con aplicaciones de computadora a traves de conversaciones. Los sistemas de ayuda basados en tareas ayudan a alcanzar las metas tales como obtener plazas de comida o reservar servicios tales como taxis o vuelos. El seguimiento del estado del diálogo o Dialogue State Tracking en inglés (DST) es un componente clave de un SDS que sirve para interpretar una entrada del usuario y actualizar si hace falta la creencia del estado del diálogo i.e. su intención, en cada turno del mismo. Es decir que el state tracker implementa la representación interna del sistema del estado de la conversación (Young et al., 2010). Esta información es usada por el manejador de diálogos para decidir que acción debería tomar el sistema.
En este trabajo se analiza la posibilidad de construir un state tracker utilizando RL clásico y RL con inspiración biológica. Se buscó un conjunto de datos rotulados acorde a esta problemática y se pensaron posibles experimentos bajo la asunción de que es posible tal construcción y se estudiaron métricas y baselines para comparar resultados.
En lo que sigue se describen cada una de las componentes del trabajo y se presentan discusiones al respecto. Para mejorar la organización tanto en la lectura como en el mantenimiento se profundizan dichos componentes en documentos separados.



# Dataset
Esta componente describe el dataset seleccionado para trabajar, el cual establece también el problema a resolver. Para profundizar en sus caracteristicas ver [datase seleccionado](https://github.com/afiuriG/textMining/blob/main/dataSet)




#  Referencias......

