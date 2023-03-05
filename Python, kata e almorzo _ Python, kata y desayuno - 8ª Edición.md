###### tags `python-kata`

# Python, kata e almorzo / Python, kata y desayuno - 8ª Edición

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

1 - https://leetcode.com/problems/valid-palindrome/
2 - https://leetcode.com/problems/isomorphic-strings/

### Grupo 1:
- Domingo y Miguel

Palindromes


```python
from math import floor
class Solution:
    def isPalindrome(self, s: str) -> bool:
        
        s = s.lower()

        new_str = ""

        for i in range(len(s)):
            if (ord(s[i]) <= 122 and ord(s[i]) >= 97) or (ord(s[i]) >= 48 and ord(s[i]) <= 57):
                new_str += s[i]
        
        for i in range(floor(len(new_str)/2)):

            if new_str[i] != new_str[len(new_str) - i - 1]:
                return False
        
        return True
```
Isomorphic Strings
```python=
class Solution:

    def times_element_repeated(self, dict, element):
        times = 0
        
        for i in dict:
            if dict[i] == element:
                times += 1
        
        return times
    
    def isIsomorphic(self, s: str, t: str) -> bool:

        equivalents = {}

        for i in range(len(s)):
            if s[i] in equivalents:
                if equivalents[s[i]] == t[i]:
                    continue
                
                return False
            else:
                equivalents[s[i]] = t[i]
                if self.times_element_repeated(equivalents, t[i]) > 1:
                    return False
            
            print(equivalents)
        
        return True
```




### Grupo 2: 
- Manu y Lorena


```python
#Ejercicio 1
import string

class Solution:
    def isPalindrome(self, input: str) -> bool:
        #input = input.replace(",", "").replace(":", "").replace(" ", "").replace(".", "").lower()
        var_newinput = ""
        for i in input:
            if i in string.ascii_lowercase:
                var_newinput += i

        return var_newinput == var_newinput[::-1]
```
``` python
#Ejercicio 2
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        dic_symbols = {}
        if len(s) != len(t):
            return False

        for i, char in enumerate(s):
            if char == t[i]:
                return False
            if char not in dic_symbols:
                dic_symbols[char] = t[i]
            else:
                if dic_symbols[char] != t[i]:
                    return False
        return True
```
    
    
### Grupo 3:
- Luis, Miguel y MiguelAngello

```python

import re

class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = re.sub(r'[^a-zA-Z0-9]', '', s).lower()
        size = int(len(s)/2)
        for i in range(0, size):
            if(s[i] != s[-(i+1)]):
                return False
        return True


Solution()

```
``` python

class Solution :
    def isIsomorphic(self, string1, string2):

        MAX_CHARS = 256

        m = len(string1)
        n = len(string2)
    

        if m != n:
            return False
    
        marked = [False] * MAX_CHARS
    
        
        map = [-1] * MAX_CHARS
    
        for i in range(n):
    

            if map[ord(string1[i])] == -1:
    
                if marked[ord(string2[i])] == True:
                    return False

                marked[ord(string2[i])] = True
    
                map[ord(string1[i])] = string2[i]
    

            elif map[ord(string1[i])] != string2[i]:
                return False
    
        return True



```

### Grupo 4:
- Dani y Javi
```python
import re
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s_clean = re.sub(r'[^a-zA-Z0-9]', '', s).lower()
        if s_clean == s_clean[::-1]:
            return True
        return False

    
```
``` python

class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        print(s)
        print(t)
        if len(set(s)) == len(set(t)):
            track = {}
            for i, char in enumerate(s):
                if char != t[i] and char not in track.keys() and t[i] not in track.values():
                    track[char] = t[i]
                    s.replace(char,t[i])
                    print(s)
            return s == t
        return False    
    
    
    
    
```
### Grupo 5:
- Breixo, Sergio y Alex

``` python
    import string
    class Solution:
        def isPalindrome(self, s: str) -> bool:
            s = s.lower()
            s2 = [a for a in s if a in (string.ascii_lowercase + string.digits)]
            medio = int(len(s2) /2 + .5)
            l1 = s2[:medio]
            l2 = s2[-1:-medio-1:-1]
            return l1 == l2
```


```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        coincidencias = {}
        if len(s) != len(t):
            return False
        for a in range(len(s)):
            if s[a] in coincidencias:
                if coincidencias[s[a]] != t[a]:
                    return False
            else:
                if t[a] in coincidencias.values():
                    return False
                coincidencias[s[a]] = t[a]
        return True
```