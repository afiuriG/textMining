En este documento se define con presición las entidades involucradas desde el punto de vista del problema y su resolucón con RL, la primera simplificación necesaria en esta prueba de factibilidad es la desicion de trabajar con diálogos del dataset de dominio simple es decir cuyas intensiones a lo largo de los turnos no camdia de domio, o sea que si el usuario arranca el diálogo interesado en charlar sobre "restorants" entonces nunca cambia a "hotels". Esta desición simplifica la definición de las acciones reduciendo la combinatoria de las mismas. 

## Estado del environment

El estado del environment es una representación del estado del problema en cada episodio del aprendizaje del agente, estará definido como una tupla $\xi = (t_1,...,t_n,s_1,...,s_m,I,\omega)$ donde $\vec{t}$ es el vector que representa al texto del turno post procesado (i.e. la salida de la componente PreProc que aparece en los esquemas mostrados), $\vec{s}$ representa los slots del estado del diálogo actual para los dominios de interés en este diálogo ($\omega$, que en este primer paso en las pruebas de factibilidad será sólo uno, son los dominios de interes en ese diálogo) e $I$ es su intención según está definido el estado del diálogo en el dataset (como se explicó en [dataset](https://github.com/afiuriG/textMining/blob/main/datset.md)). La tupla $\varepsilon=(s_1,...,s_m,I,\omega)$ será llamada el estado del diálogo. Los tamaños $n$ y $m$ en principio son fijos, $n$ tendrá el valor que se considere adecuado, surgido de la experimentación con las diferentes representaciones de postprocesamiento de los turnos, con las que se puedan probar, el aspecto del postprocesamiento será uno de los factores que determine diferentes variaciones en las soluciones (no está definido en este momento). Por otra parte $m$ si tiene tamaño fijo y conocido a ser la cantidad de slots que tenga el dominio de interés en el diálogo en cuestión (para el caso multidominio será la suma de los slots de los dominios componentes). Se tomará la posición del vector $\vec{s}_i$ como el $i ésimo$ elemento que aparece listado en la definición del dataset, comenzando en 0, o sea que por ejemplo $s_2$ corresponde a "bus-destination" para el dominio "bus". $\xi$ es lo que aparece como compound state en el diagrama anterior. 


## Recompensa
La recompensa está definida en función de la cercanía de 2 estados de diálogos dados, donde la noción de cercanía en una propuesta inicial viene dada por las siguientes reglas:
Si $\varepsilon_1=(s_{11},...,s_{1m},I,\omega)$ y $\varepsilon_2=(s_{21},...,s_{2m},I,\omega)$ son dos estados de diálogo con la misma intención en los mismos dominios, diremos que la cercanía $\delta$ entre $\varepsilon_1$ y $\varepsilon_2$ está dada por: $\delta(\varepsilon_1,\varepsilon_2)=\sum_{i=0}^{d}\varphi(s_{1i},s_{2i})$ donde $\vec{s}$ son los slots del dominio $\omega$ y $d$ es la cantidad de slots que tiene ese dominio,  $\varphi(s_{1i},s_{2i})$
viene dada por

$$
\varphi(s_{1i},s_{2i}) = \begin{cases}
    0 & s_{1i}=s_{2i}=\text{default value} \\
    1/d & \text{si el } iésimo \text{ slot es categórico y }  s_{1i}=s_{2i}\ne\text{default value} \\
    1/d & \text{si el } iésimo \text{ slot no es categórico y }  \rho(s_{1i})=\rho(s_{2i}) \text{ y } s_{1i},s_{2i}\ne\text{default value}
\end{cases}
$$

Donde en un primer approach como prueba de factibilidad categorizo todos los slots no categóricos con la función $\rho(s)$ que devuelve la categoría impuesta a un slot no categórico. O sea por ejemplo un slot dado $s$ que mantiene algún horario (por ejemplo de la partida de un tren) se categoriza en 24 valores, uno por hora (o sea que la atomicidad de a 1 hr). Esto simplifica el cálculo de cercanías para slots no categóricos y además dependerá de la implementación elejida para el preprocesamiento de los textos de los turnos por lo que su definición se dejará para el momento de la implementación. Esta noción de cercanía necesitará validarse con los experimentos realizados, quizás se necesite otro criterio más complejo y cada nueva definición estará constituyendo una versión de la solución.

## Acciones
Las acciones son las que nos permiten influenciar el comportamiento del environment. Se establecen 36 acciones (que se distinguen con el nombre de atómicas) motivadas por la necesidad de cambiar los slots del estado del diálogo y la intensión del mismo. Asi entonces habrá el conjunto $\mathcal{A}={A_0,A_1,...,A_{35}}$ de acciones donde $A_0$ es la acción que cambia el estado de la inensión del diálogo mientras que las restantes cambian el estado del slot asociado. Cada acción atómica recibe como parámetro el valor del estado del slot que necesita cambiar, siendo en el caso de los slots categóricos justamente sus diferentes valores y para el caso de los no categóricos habrá una discretización de sus valores, esto se definirá en tiempo de implementación y formará parte del proceso de experimentación como en el caso del proprocesamiento. Estas acciones atómicas serán compuestas en una secuencia de acciones según convenga ya que en cada turno el usuario puede expresar varias ideas juntas, así entonces lo que aparece en los diagramas como acción será en realidad una secuencia $S_{at}$ de secuencias atómicas y la semántica de tal construcción es la de ejecutar la conjunción de todas las acciones de la secuencia. 

Las acciones son las que nos permiten influenciar el comportamiento del environment. En este problema se define "solamenete" una acción que es la que asigna un estado de diálogo al environment, se llama $set(\varepsilon)$ a la acción que asigna el estado $\varepsilon$ al environment. 

## Tareas pendientes hasta la implementación:
- [ ] validar cercania
- [ ] validar acciones
- [ ] validar preproceso


