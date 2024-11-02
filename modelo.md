En este documento se define con presición las entidades involucradas.

## Estado del environment

El estado del environment es una representación del estado del problema en cada episodio del aprendizaje del agente, estará definido como una tupla $\xi = (t_1,...,t_n,s_1,...,s_m,I)$ donde $\vec{t}$ es el vector que representa al texto del turno post procesado (i.e. la salida de la componente PreProc que aparece en los esquemas mostrados), $\vec{s}$ representa los slots del estado del diálogo actual e $I$ es su intención según está definido el estado del diálogo en el dataset (como se explicó en [dataset](https://github.com/afiuriG/textMining/blob/main/datset.md)). La tupla $\varepsilon=(s_1,...,s_m,I)$ será llamada el estado del diálogo. Los tamaños $n$ y $m$ en principio son fijos, $n$ tendrá el valor que se considere adecuado, surgido de la experimentación con las diferentes representaciones postprocesadas, de los turnos, con las que se puedan probar, se manejará com un hiperparámetro del proceso de aprendizaje. Por otra parte $m$ si tiene tamaño fijo y conocido a ser $35$ que es la cantidad de slots definidos en el dataset. Se tomará la posición del vector $\vec{s}_i$ como el $i ésimo$ elemento que aparece listado en la definición del dataset, comenzando en 0, o sea que por ejemplo $s_3$ corresponde a "bus-day". $\xi$ es lo que aparece como compound state en el diagrama anterior. 


## Recompensa
La recompensa está definida en función de la cercanía de 2 estados de diálogos dados, donde la noción de cercanía en una propuesta inicial viene dada por las siguientes reglas:
Si $\varepsilon_1=(s_{11},...,s_{1m},I)$ y $\varepsilon_2=(s_{21},...,s_{2m},I)$ dos estados de diálogo con la misma intención, diremos que la cercanía $\delta$ entre $\varepsilon_1$ y $\varepsilon_2$ está dada por: $\delta(\varepsilon_1,\varepsilon_2)=\sum_{i=j}^{k}\varphi(s_{1i},s_{2i})$ donde $[j,k]\in[1,m]$ es el rango de índices de los slots asociados al dominio de la intención $I$ y si $d$ es la cantidad de slots que tiene ese dominio,  $\varphi(s_{1i},s_{2i})$
viene dada por

$$
\varphi(s_{1i},s_{2i}) = \begin{cases}
    0 & s_{1i}=s_{2i}=\text{default value} \\
    1/d & \text{si el } iésimo \text{ slot es categórico y }  s_{1i}=s_{2i}\ne\text{default value} \\
    1/d*\rho(s_{1i},s_{2i}) & \text{si el } iésimo \text{ slot no es categórico y }  s_{1i}=s_{2i}\ne\text{default value}
\end{cases}
$$

Donde $\rho(s_{1i},s_{2i})$ es una forma de caracterizar la cercanía de los slots no categóricos que dependerád e la implementación elejida para el preprocesamiento de los textos de los turnos por lo que su implementación se dejará para el momento de la implementación. Esta noción de cercanía necesitará validarse con los experimentos realizados, quizás se necesite otro criterio más complejo.

## Acciones




validar cercania
validar acciones
Validar preproceso
