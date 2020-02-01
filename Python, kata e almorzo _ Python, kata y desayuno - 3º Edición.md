# Python, kata e almorzo / Python, kata y desayuno - 3º Edición

Hola!

Breves instrucciones a continuación para que todo vaya fluido!

1. Nos juntaremos en grupos de 2-3 personas
1. Elegiremos conjuntamente y al "azar" un ejercicio de https://leetcode.com/ o https://www.hackerrank.com/
1. Resolveremos el problema en iteraciones de 10 minutos.
1. Al final cada iteración decideremos entre todos los grupos si damos finalizado el problema o continuamos iterando para refactorizar u optimizar.
1. Finalizado el problema, copiaremos la solución en este documento en el espacio reservado para cada grupo.
1. Revisaremos y comentaremos soluciones de cada grupo.
1. Revisaremos soluciones de otros usuarios en Leetcode o Hackerank en Python, y en otros lenguajes.
1. Si queda tiempo volvemos al _Paso 2_.

Además..

1. No es necesario que todo el mundo traiga portatil (1 de cada 2 o 3 es suficiente) ni es necesario instalar nada.
1. Se puede acompañar de café, te, galletas, desayuno inglés...(recuerda teclear sin chocolate en los dedos)
2. No importa el nivel o la experiencia individual, lo importante es aprender todos de todos.
3. La reunión es informal y el objetivo es aprender pasando un buen rato!

Anteriores ediciones:
- [Primera Edición](https://hackmd.io/ZFqsaJQAQQGm8z2sPTwA3g)
- [Segunda Edición](https://hackmd.io/FO4AHdfHTASNM_1ahFn8DQ)

## Ejercicios: 

- 1184. Distance Between Bus Stops: https://leetcode.com/problems/distance-between-bus-stops/submissions/


### Grupo 1 - Componentes:

- David
- Alex

_Código:_
```python

class Solution:
    def distanceBetweenBusStops(self, distance: List[int], start: int, destination: int) -> int:
        start_sum = sum(distance[start:destination])
        
        if destination > start:
            tail_sum = sum(distance[destination:])
        elif destination < start:
            tail_sum = sum(distance[:destination]) + sum(distance[start:])

        if start_sum == 0:
            return tail_sum
        if start_sum > tail_sum:
            return tail_sum

        return start_sum

```

### Grupo 2 - Componentes:

- Alberto
- Mireia
- Borja

_Código:_
```python
class Solution:
    def distanceBetweenBusStops(self, distance: List[int], start: int, destination: int) -> int:
        if start > destination:
            direction_a = sum(distance[destination:start])
        else:
            direction_a = sum(distance[start:destination])
            
        direction_b = sum(distance) - direction_a
        
        if direction_a < direction_b:
            return direction_a
        return direction_b    
    

```

### Grupo 3 - Componentes:

 - Juan
 - Sergio

_Código:_
```python
class Solution:
        
    def distanceBetweenBusStops(self, distance: List[int], start: int, destination: int) -> int:
        distancedup = distance * 2
        inc = 0
        minv = min(start, destination)
        maxv = max(start, destination)
        
        return min(sum(distancedup[minv : maxv]), sum(distancedup[maxv : minv + len(distance)]))
            
```

### Grupo 4 - Componentes:
Dani, Xurxo

_Código:_
```python
# no funciona 😞
class Solution:
    def distanceBetweenBusStops(self, distance: List[int], start: int, destination: int) -> int:
        def getdistance(distance, start, destination, sentido):
            n = len(distance)
            d= 0
         
            for i in range (0, n):
                currpos = start+(i*sentido) % n
                print(currpos)
                if sentido ==1:
                    d += distance[currpos]
                else:
                    d += distance[currpos-1]
                if (currpos+1==destination):
                    break
            return d
        clockw =getdistance(distance, start, destination, 1)
        countercw = getdistance(distance, start, destination, -1)
        # print(clockw,countercw)
        return min (clockw,countercw)
            
```
## Grupo 5 - Componentes:
Francisco y Luis

```python
class Solution:
    def distanceBetweenBusStops(self, distance: List[int], start: int, destination: int) -> int:
        num_paradas= len(distance)
        distancia_directa = 0
        if start<destination: 
            for distancia in range(start,destination):
                distancia_directa+=distance[distancia]
        else:
            for distancia in range(destination,start):
                distancia_directa+=distance[distancia]
        distancia_inversa=0
        distancia_total=0
        for distancia in distance:
            distancia_total+=distancia   
        distancia_inversa=distancia_total-distancia_directa
        return min(distancia_directa, distancia_inversa)

```
          

## FRIKADAS

