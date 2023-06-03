###### tags `python-kata`

# Python, kata e almorzo / Python, kata y desayuno - 10ª Edición

Hola!

Breves instrucciones a continuación para que todo vaya fluido!

1. Nos juntaremos en grupos de 2-3 personas
1. Elegiremos conjuntamente y al "azar" un ejercicio de https://leetcode.com/
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


- [Ediciones anteriores](https://github.com/aindustriosa/python-kata-e-almorzo)


## Ejercicios: 

- https://leetcode.com/problems/move-zeroes/
- https://leetcode.com/problems/find-the-difference/submissions/
- https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/


### Grupo 1 - Integrantes: Dani & Alex

_Código:_

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        positions = [pos for pos,e in enumerate(nums) if e == 0]
        
        for position in reversed(positions):
            del nums[position]
            nums.append(0)

            
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """

        
        for position, e in reversed(list(enumerate(nums))):
            if e == 0:
                del nums[position]
                nums.append(0)
```

https://leetcode.com/problems/find-the-difference/submissions/

```python

class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        result = (Counter(t) - Counter(s))

        return list(result.keys())[0]
```


### Grupo 2 - Integrantes: Javier y Jose

_Código:_
1. Move Zeroes
https://leetcode.com/problems/move-zeroes/description/ 
```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        zeros = nums.count(0)
        for i in range(zeros):
            nums.remove(0)
        nums += [0]*zeros
```


2. Find the difference
https://leetcode.com/problems/find-the-difference/description/

```python
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        for l in t:
            if t.count(l) > s.count(l):
                return l
```



### Grupo 3 - Miguel y Domingo: 

_Código:_
```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        number_of_zeroes = nums.count(0)

        while number_of_zeroes > 0:

            nums.remove(0)
            nums.append(0)         
```

```python
class Solution:
    def findTheDifference(self, s: str, t: str) -> str:
        return list((Counter(t) - Counter(s)).keys())[0]
```

```python
class Solution:
    def countCharacters(self, words: List[str], chars: str) -> int:

        result = 0
        valid = True

        for word in words:
            for char in str(set(word)):
                if chars.count(char) < word.count(char):
                    valid = False
                    break
            
            if valid:
                result += len(word)
            
            valid = True

        return result
    
=====

class Solution:
    def countCharacters(self, words: List[str], chars: str) -> int:

        result = 0
        chars_counter = Counter(chars)

        for word in range(len(words)):
            if Counter(words[word]) <= chars_counter:
                result += len(words[word])
        
        return result
```

### grupo 4 _ Paul y Daniel : 
_Código:_
```python
from collections import Counter
class Solution:
    def countCharacters(self, words: List[str], chars: str) -> int:
        result = 0
        for i in words:
            w = Counter(i)
            c = Counter(chars)
            if not w-c:
                result += len(i)
        return result
```

## FRIKADAS
