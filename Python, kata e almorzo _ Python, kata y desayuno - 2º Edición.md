# Python, kata e almorzo / Python, kata y desayuno - 2º Edición

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
- [Primera Edición](https://hackmd.io/imuIhPbvRHugi0ocWmckUQ?edit)

## Ejercicios: 

* Defanging an IP Address / https://leetcode.com/problems/defanging-an-ip-address/
* Goat Latin / https://leetcode.com/problems/goat-latin/


### Grupo 1 - Componentes:

- David
- Mireia

_Código:_
```python
class Solution:
    def defangIPaddr(self, address: str) -> str:
        return address.replace(".", "[.]")
```

_Código:_

```python
class Solution:
    def toGoatLatin(self, S: str) -> str:
        new_words = []
        for n, word in enumerate(S.split(" ")):
            
            if word[0].lower() not in {"a", "e", "i", "o", "u"}:
                word = word[1:] + word[0]
           
            word += "ma" + ("a" * (n + 1))
                        
            new_words.append(word)

        return " ".join(new_words)

class Solution2:
    def toGoatLatin(self, S: str) -> str:
        new_words = []
        for n, word in enumerate(S.split(" ")):
        
            # not in 'aeiou'
            if word[0].lower() not in {"a", "e", "i", "o", "u"}:
                word = word[1:] + word[0]
                            
            new_words.append(f"{word}ma{'a' * (n + 1)}")
        
        return " ".join(new_words)   
```

### Grupo 2 - Componentes:

- Luis
- Alex
- Dani

_Código:_
```python
class Solution:
    def defangIPaddr(self, address: str) -> str:
        # return address.replace('.', '[.]')
        result: str = ""
        for char in address:
            if char == '.':
                result += '[.]'
            else:
                result += char
        return result

```


_Código:_
```python
class Solution:
    def toGoatLatin(self, sentence: str) -> str:
        tail = 'a'

        def translate(word: str, position: int):
            if word[0] not in 'aeiouAEIOU':
                word = word[1:] + word[0]
            word += 'maa' + tail * position
            return word

        return " ".join(
            [translate(word, position) 
             for position, word in enumerate(sentence.split())]
        )
```


### Grupo 3 - Componentes:

_Código:_
Jose 
Sergio


### Grupo 4 - Componentes:
_Código:_
Xurxo
Félix

_Código:_
```python
import re

class Solution:
    def defangIPaddr(self, address: str) -> str:
        #return address.replace('.','[.]')
        # return re.sub(r"\.",'[.]' , address)
        return ''.join(a if a !='.' else '[.]' for a in address)
        
        
        
class Solution:
    
    def toGoatLatin(self, S: str) -> str:
        
        vowels ='aeiouAEIOU'
        newwords = []
        for i, word in enumerate (S.split(' '), 1):
            if word[0] in vowels:
                word += 'ma'
            else:
                word = word[1:] + word[0] + 'ma'
            word += ('a' * i)
            newwords.append (word)  
            
        return ' '.join(newwords)
            
```


## FRIKADAS

* https://leetcode.com/problems/sudoku-solver/
* https://en.wikipedia.org/wiki/Sudoku_solving_algorithms
