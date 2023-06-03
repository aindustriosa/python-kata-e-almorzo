###### tags `python-kata`

# Python, kata e almorzo / Python, kata y desayuno - 9ª Edición

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


- https://leetcode.com/problems/ransom-note/
- https://leetcode.com/problems/distribute-candies/
- https://leetcode.com/problems/keyboard-row/

### Grupo 1 - Integrantes: Alex & Dani

_Código:_

https://leetcode.com/problems/ransom-note/

```python
# Versión con ifs
from collections import Counter

class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        counterNote = Counter(ransomNote)
        counterMagazine = Counter(magazine)
        for letter, count in counterNote.items():
            if letter not in counterMagazine:
                return False
            if counterMagazine[letter] < counterNote[letter]:
                return False
        return True

# Versión con list comprehensions
from collections import Counter

class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        counterNote = Counter(ransomNote)
        counterMagazine = Counter(magazine)

        return all([False if 
                    letter not in counterMagazine or counterMagazine[letter] < counterNote[letter]) else True for letter, count in counterNote.items() 
            ]
        )

```

https://leetcode.com/problems/distribute-candies/

```python 
class Solution:
    def distributeCandies(self, candyType: List[int]) -> int:
        candies_to_eat = len(candyType)//2
        unique_candies_types = len(set(candyType))
        return min([candies_to_eat, unique_candies_types])

```


```python 
    
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        keyboard = [
            "qwertyuiop",
            "asdfghjkl",
            "zxcvbnm",
        ]
        result = []
        for word in words:
            set_word = set(word.lower())
            for row in keyboard:
                r = set_word - set(row)
                if r == set():
                    result.append(word)
        return result

```python

    def findWords(self, words: List[str]) -> List[str]:
        keyboard = [
            set("qwertyuiop"),
            set("asdfghjkl"),
            set("zxcvbnm"),
        ]

        def can_write(word):
            set_word = set(word.lower())
            for row in keyboard:
                if not set_word - row:
                    return True
            return False
        
        return [
            word for word in words if can_write(word)
        ]
```



### Grupo 2 - Integrantes: Breixo & Nacho

#### RansomNote
```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        magazine_list = [*magazine]
        for a in ransomNote:
            if a in magazine_list:
                magazine_list.pop(magazine_list.index(a))
            else:
                return False
        return True

```

#### A dieta
```python
class Solution:
    def distributeCandies(self, candyType: List[int]) -> int:
        return int(min(len(set(candyType)), len(candyType) / 2))
```

#### Palabras con teclado
```python
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        frow = set("qwertyuiop")
        srow = set("asdfghjkl")
        trow = set("zxcvbnm")

        result = []
        for w in words:
            s = set(w.lower())
            if len(s) == max(len(s.intersection(frow)),
               len(s.intersection(srow)),
               len(s.intersection(trow))):

               result.append(w)
        return result
```


### Grupo 3 - Integrantes: Sergio y Eduardo

_Código:_
```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        while len(ransomNote) >0 :
            pos=magazine.find(ransomNote[0])
            if pos == -1 :
                return False
            magazine=magazine[0:pos]+magazine[pos+1:]
            ransomNote=ransomNote[1:]
        return True
            
```

### Grupo 4 - Integrantes: Luís, Serhii, Jose

_Código:_
```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        ransomNote = list(ransomNote)
        magazine = list(magazine)
        for i in ransomNote:
            if i in magazine:
                magazine.remove(i)
            else:
                return False
        return True
            
```

```python
from collections import Counter
class Solution:
    def distributeCandies(self, candyType: List[int]) -> int:
        tipos = len(Counter(candyType).keys())
        max_candys = int(len(candyType)/2)
        if tipos < max_candys:
            return int(tipos)
        return max_candys
```

```python
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        first = 'qwertyuiop'
        second = 'asdfghjkl'
        third = 'zxcvbnm'

        resultados = []

        for j in words:
            i = j.lower()
            if (len(list(set(i) & set(first))) == len(set(i))) or (len(list(set(i) & set(second))) == len(set(i))) or (len(list(set(i) & set(third))) == len(set(i))):
                resultados.append(j)
        
        return resultados
```             

### Grupo 5 - Integrantes: Miguel y Carlos

#### Keyboard Row
###### Normal
```python
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        result = []
        
        rows = ("qwertyuiop", "asdfghjkl", "zxcvbnm")

        for row in rows:
            for word in words:
                for i in range(len(word)):
                    if word[i].lower() not in row:
                        break
                    
                    if i == len(word) - 1:
                        result.append(word)

        return result
```

###### One Liner
```python
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        return [word for word in words if any(all(c in row for c in word.lower()) for row in (list("qwertyuiop"), list("asdfghjkl"), list("zxcvbnm")))]
```

_Código:_
```python
class Solution:
    def distributeCandies(self, candyType: List[int]) -> int:
        length = len(candyType)//2
        set_length = len(set(candyType))
        return set_length if set_length < length else length
```

```python
def remove_character(string, index):
    new_str = ""
    for i in range(len(string)):
        if index == i:
            continue
        new_str += string[i]
    return new_str

class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:

        if len(magazine) < len(ransomNote):
            return False
        for character in ransomNote:
            for magazine_character in range(len(magazine)):
                # print(f"{ransomNote} : {magazine}")
                if character == magazine[magazine_character]:
                    magazine = remove_character(magazine, magazine_character)                    
                    break

                
                if magazine_character == len(magazine) - 1:    
                    return False
        return True
```

```python
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        ransomNote_list = list(ransomNote)
        ransomNote_set = list(dict.fromkeys(ransomNote_list))
        return all(magazine.count(c) >= ransomNote_list.count(c) for c in ransomNote_set)
```

## FRIKADAS
