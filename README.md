# UNIR-RPA-ACTIVIDAD-1


## BLOQUE 0 - SISTEMAS INTELIGENTES

Los algorimos de búsqueda buscan resolver problemas complejos mediante algoritmos con el menor coste de computación. Dos tipos,
algoritmos no informados y algoritmos informados (heurísticos).

![Algoritmos](/docs/algoritmos.png)

### ALGOTIMOS NO INFORMADOS

Busqueda ciega, no guiada o por fuerza bruta. Sin información sobre el dominio del problema. Se imponen restricciones para buscar
una solución óptima.

La complejidad temporal y espacial se mide en:

1. b: **branching factor** -> número máximo de hijos de cada nodo
2. d: **depth** -> profundidad de la solución de menor coste.
3. m: **máximum depth** -> máxima profunidad del espacio (puede ser infinito a no ser que lo estrechemos nosotros)

![Eficiencia computacional](/docs/eficiencia-computacional.png)

#### Breadth-First Search **BFS** // Búsqueda en anchura

Explora primero los nodos hijos de cada nivel. Cola tipo FIFO.

![BFS](/docs/BFS.png)

#### Uniform-cost Search **BFD** // Búsqueda de coste uniforme

Trata de coger el nodo de menor coste entre sus nodos hijos, pero sigue priorizando la busqueda primero de un nivel destrás de
otro. Si todos los nodos tienen el mismo coste entonces es igual que el BFS.

#### Depth-First Search **DFS** // Búsqueda en profundidad

Empieza el  nodo y explora todos los caminos en prfunidad. Es limitado, BFS no es tan problemático ya que podría estar en un bucle.
Para solucionarlo hay que LIMITARLO a un número de profundidad.

![DFS](/docs/DFS.png)

### ALGORITMOS INFORMADOS

Básicamente son como los no informados pero proporcionandoles información sobre el problema. Tienen un contexto específico y mo
existe un camino fijo que recorrer. **Los nodos ahora son visitados acorde a su coste computacional o heurístico**. Se recorren
los árboles para calcular el coste computacional y los más costosos de ignoran.

> [!IMPORTANT]
> La heurística trata de hacer innovaciones en un algoritmo para alcanzar objetivos. Puede reducir drásticamente el coste de
> computación de problemas que son resueltos con algoritmos no informados.

#### Best First Approarch **DFS** // Búsqueda el primero el mejor

El siguiente nodo visitadfo es aquel que tiene menor coste computacional

#### Greedy Best-First Search **GBFS** // Búsqueda codicionsa el primero el mejor

Se usa cola para que se ordene el coste computacional de acuerdo al valor h(n).

f(n) = h(n)

![Arbol](/docs/arbol-GBFS.png)

El siguiente nodo eleguido es aquel que tiene menor coste computacional representada por la cola. **Sólo se sigue por el coste
representada por la lista estrictamente**.

Por ejemplo, en el siguiente caso del viaje de ciudades tomará el camino siguiente:

![Mapa](/docs/mapa.png)

Solución 1: Arad -> Sibiu -> Fagaras -> Bucharest con un coste de **450**

Solución GBFS:

1. Desde Arad elige entre 3 opciones:

- Sibiu 253
- Zerind 374
- Timisoara 329

Elige **Sibiu**

2. Desde Sibiu tiene otras 3 opciones

- Arad o Oradea, ambas con un coste muy grande, 366 y 380. Descartadas, sería volver hacía atrás y por eso la cola lo especifica.
- Fagaras 178
- Rimnicu 193

Elige **Fagaras**

El coste total computacional équivalente sería 140 + 99 + 178 = **417**

GBFS ha contrado una mejor solución que la anterior.

#### A* // Búsqueda A estrella

A diferencia del anterior, A* considera el coste de alcanzar el nodo y la estación del coste al llegar al objetivo:

f(n) = g(n) + h(n) donde g(n) es el coste de llegar al nodo y h(n) es el coste de llegar al objetivo.

![Mapa](/docs/mapa.png)

Solución A*:

1. Desde Arad elige entre 3 opciones:

- Sibiu **140 +** 253 = 393
- Zerind **75 +** 374 = 449
- Timisoara **111** + 329 = 440

Elige **Sibiu** de nuevo

2. Desde Sibiu tiene otras 3 opciones

- Arad o Oradea. Descartadas, sería volver hacía atrás y por eso la cola lo especifica.
- Fagaras **99 +** 178 = 277
- Rimnicu **80 +** 193 = 273

Elige **Rimnicu**

El coste total computacional équivalente sería 140 + 80 + 193 = **413**

Ha conseguido una solución mejor. No es más rápida pero te asegura un coste computacional mejor. GBFS escoge un mejor coste por
heurística pero no considera el coste del movimiento hacia el siguiente nodo.

![Tabla](/docs/tabla-informados.png)
