# Python, kata e almorzo / Python, kata y desayuno - 6ª Edición

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
- [https://github.com/aindustriosa/python-kata-e-almorzo](https://github.com/aindustriosa/python-kata-e-almorzo)


## Ejercicios: 

* https://leetcode.com/problems/climbing-stairs/

### Grupo 1 - Componentes:

Dani
Alex

_Código:_

```python
import itertools

class Solution:
    def climbStairs(self, n: int) -> int:
        unos = n
        doses = 0
        resultado = 0
        while True:
            elementos = "1" * unos + "2" * doses
            resultado += len(set(itertools.permutations(elementos)))
            if unos >=2:
                unos -= 2
                doses += 1
            else:
                return resultado
```

### Grupo 2 - Componentes:
Alberto et Xurxo
_Código:_
```python
class Solution:
    
    def recursive (self, left):
        # print(left)
        if left==[]:
            self.contador+=1 
            return
        for i in [1,2]:
            if i<=len(left):
                self.recursive(left[i:])
    def climbStairs(self, n: int) -> int:
        self.contador =0    
        self.recursive([1 for _ in range(n)])
        return self.recursive


solucion:
1 -> 1
2 -> 2
3 -> 3
4 -> 5
5 -> 8
6 -> 13
7 -> 21

asi que 
f(n) -> f(n-1) + f(n-2)
f(1) -> 1
f(2) -> 2
```


### Grupo 3 - Componentes:
Javi Franco
Jhon
Mireia

_Código:_
```python

N = 6

_min=int(math.floor(N / 2.0) + 1)
print("min", _min)

res=0
for x in range(0, _min, 1):
	print(x, res)
	res = res + (N - x)

print(res)
#  n - 0 + (n - 1) + (n - 2)

```
