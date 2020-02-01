# Python, kata e almorzo / Python, kata y desayuno - 1º Edición

Enlace:

https://leetcode.com/problemset/all/?difficulty=Easy

Equipos:

Ejercicio 20: https://leetcode.com/problems/valid-parentheses/

Rastersoft:

``` python
class Solution:
    def isValid(self, s: str) -> bool:
        lista = []
        combinaciones = {'[': ']', '(': ')', '{': '}'}
        for elemento in s:
            if elemento in combinaciones:
                lista.append(elemento)
                continue
            try:
                if elemento != combinaciones[lista.pop()]:
                    return False
            except:
                return False
        return True
```


Dani & Xurxo:
~~~ python
class Solution:
    def isValid(self, s: str) -> bool:
        pila = []
        parentesis = {
            ')':'(',
            '}':'{',
            ']':'[',
                     }
        for c in s:
            if c in parentesis.values():
                pila.append(c)
            elif c in parentesis.keys():
                try:
                    if pila.pop() != parentesis[c]:
                        return False
                except:
                    return False
        return len(pila)==0
~~~




fpuga
```python
class Solution:
    def isValid(self, s):
        valids = {
            "(":")",
            "{":"}",
            "[":"]",
            ")":"(",
            "}":"{",
            "]":"[",
        
        }
        parents = []
        if s == "":
            return True
        
        for l in s:
            if l in valids.keys() or l in valids.values():
                parents.append(l)
        
        for i, l in enumerate(parents[:len(parents)/2]):
            if valids[l] == parents[i-1]:
                return True
        return False
```
daavoo

```
Runtime: 24 ms, faster than 29.17% of Python online submissions for Valid Parentheses.
Memory Usage: 11.8 MB, less than 57.14% of Python online submissions for Valid Parentheses.
```
```python
close_to_open = {
    ")": "(",
    "]": "[",
    "}": "{"
}

class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        to_be_closed = []
        for c in s:
            if c in close_to_open.values():
                to_be_closed.append(c)
            elif c in close_to_open.keys():
                if len(to_be_closed) == 0:
                    return False
                if to_be_closed.pop() != close_to_open[c]:
                    return False
        return len(to_be_closed) == 0
```
