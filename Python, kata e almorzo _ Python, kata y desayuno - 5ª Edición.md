# Python, kata e almorzo / Python, kata y desayuno - 5ª Edición

Hola!

Breves instrucciones a continuación para que todo vaya fluido!

1. Elegiremos conjuntamente y al "azar" un ejercicio de https://leetcode.com/ o https://www.hackerrank.com/
2. Nos juntaremos en grupos de 2-3 personas
3. Resolveremos el problema en iteraciones de 10 minutos.
4. Al final cada iteración decideremos entre todos los grupos si damos finalizado el problema o continuamos iterando para refactorizar u optimizar.
5. Finalizado el problema, copiaremos la solución en este documento en el espacio reservado para cada grupo.
6. Revisaremos y comentaremos soluciones de cada grupo.
7. Revisaremos soluciones de otros usuarios en Leetcode o Hackerank en Python, y en otros lenguajes.
8. Si queda tiempo volvemos al _Paso 2_.

Además..

1. No es necesario que todo el mundo traiga portatil (1 de cada 2 o 3 es suficiente) ni es necesario instalar nada.
1. Se puede acompañar de café, te, galletas, desayuno inglés...(recuerda teclear sin chocolate en los dedos)
2. No importa el nivel o la experiencia individual, lo importante es aprender todos de todos.
3. La reunión es informal y el objetivo es aprender pasando un buen rato!

Anteriores ediciones:
- [Primera Edición](https://hackmd.io/ZFqsaJQAQQGm8z2sPTwA3g)
- [Segunda Edición](https://hackmd.io/FO4AHdfHTASNM_1ahFn8DQ)
- [Tercera Edición](https://hackmd.io/-sF1xb0ASkC98ArsOgdItA?view)
- [Cuarta Edición](https://hackmd.io/@aindustriosa/B1cQ0DdZU)

## Ejercicios: 

Beautiful Arrangement II: https://leetcode.com/problems/beautiful-arrangement-ii/

### Grupo 1 - Componentes:
- Mireia
- Alex

(not finished)
_Código:_

```python
class Solution:
    def constructArray(self, n: int, k: int) -> List[int]:
        lista_final = []
        lista_resta = [] #lenght n-1
    
        for n1, n2 in enumerate(range(1, n+1)):
            resta = n1 - n2
            lista_resta.append(resta)
            
            if n1 == 1:
                lista_final.append(n1)
                lista_final.append(n2)
            else:
                if len(set(lista_resta)) <= k:
                    lista_final.append(n2)       

        return lista_final

```

``` python


```

### Grupo 2 - Componentes: Xurxo et Dani

A medio hacer :-1: 
_Código:_
```python
import itertools

class Solution:
    def comprueba (combination):
        suma = []
        for i in range(n-1):
          suma.append(abs(combination[i] - combination[i+1]))
        if len(set(suma))==k:
          return True
              
    def recursive (n, l, k):
        if (len(l)==n and comprueba(l)):
          return l
        if len(l)==n:
          return False
        for (elementos in range(n) ):
          if elemento in l:
            continue
          l.append(l)
          if not recursive (n,l,k):
            l.pop()
    def constructArray(self, n: int, k: int) :
        start_perms = itertools.permutations(elementos,2)
        recursive (n, start_perms, k)
        
        elementos=range(1,n+1)
        for combination in itertools.permutations(elementos):
  
```
fuerza bruta - Funciona, pero timeout
```python

import itertools

class Solution:
    def constructArray(self, n: int, k: int) :
        elementos=range(1,n+1)
        for combination in itertools.permutations(elementos):
            suma = []
            for i in range(n-1):
              suma.append(abs(combination[i] - combination[i+1]))
            if len(set(suma))==k:
              return list(combination)


s = Solution().constructArray(3,2)
print(s)



s = Solution().constructArray(3,2)
print(s)


```


### Grupo 3 - Componentes:

- Juan
- Sergio

_Código:_
```python
class Solution:
    def constructArray(self, n: int, k: int) -> List[int]:
        salida = []
        elementos = []
        for b in range(n):
            elementos.append(b + 1)
        if k == 1:
            return elementos
        pos = k
        sumar = False
        for b in range(k + 1):
            a = k - b
            salida = salida + [elementos[pos]]
            if sumar:
                pos += a
                sumar = False
            else:
                pos -= a
                sumar = True
        salida += elementos[k+1:]
        return salida
            
```
