# Python, kata e almorzo / Python, kata y desayuno - 4ª Edición

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
- [Tercera Edición](https://hackmd.io/-sF1xb0ASkC98ArsOgdItA?view)


## Ejercicios seleccionados: 

- https://leetcode.com/problems/nim-game/
- https://leetcode.com/problems/add-two-numbers/

### Grupo 1 - David, Carlos:

_Código:_

```python
class Solution:
    def canWinNim(self, n: int) -> bool:
        return n % 4
```

_Código:_

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

def convert_listnode_to_reversed_list(listnode):
    result_list = []
    x = listnode
    while True:
        if x.next is None:
            result_list.append(x.val)
            break 
        else:
            result_list.append(x.val)
        x = x.next
    return result_list[::-1]

def revert_list_and_convert_to_listnode(original_list):
    node = ListNode(original_list[-1])
    for n, x in enumerate(original_list[::-1]):
        if n == 0:
            continue
        new_node = ListNode(x)
        node.next = new_node
        # Isto non vai
        node = new_node
    return node

        
        
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:

        l1_list = convert_listnode_to_reversed_list(l1)
        l2_list = convert_listnode_to_reversed_list(l2)
        number_1 = int("".join(map(str, l1_list[::-1])))
        number_2 = int("".join(map(str, l2_list[::-1])))
        result = str(number_1 + number_2)
        
        # Isto non vai
        result_listnode = revert_list_and_convert_to_listnode(result)

        return result_listnode
        
```

### Grupo 2 - Xurxo, Daniel:

_Código:_
```python
class Solution:
    def canWinNim(self, n: int) -> bool:
        return (n % 4)

```

No funciona :(
~~~python
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1.next and not l2.next:
            return ListNode(l1.val + l2.val)
        if not l1.next:
            return l2
        if not l2.next:
            return l1

        node = ListNode(l1.val + l2.val % 10)
        node.next = self.addTwoNumbers(l1.next, l2.next)
        if node.next.val > 9:
            node.val += node.next.val // 10
            node.next.val = node.next.val % 10
        return node
~~~

### Grupo 3 - Sergio, Vilchez, Álex:


_Código:_
```python
class Solution:
    def canWinNim(self, n: int) -> bool:
        return (n % 4) != 0
```

```python
class Solution:
    
    def _listToNumber(self, lista, mult = 1):
        if lista is None:
            return 0
        return lista.val * mult + self._listToNumber(lista.next, mult * 10)
    
    def _numberToList(self, numero):
        if numero == 0:
            return None
        elemento = ListNode(numero % 10)
        elemento.next = self._numberToList(numero // 10)
        return elemento
        
    
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        n = self._listToNumber(l1) + self._listToNumber(l2)
        if n == 0:
            return ListNode(0)
        return self._numberToList(n)
```



---
## A Posteriori: Xurxo
```python

# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class SumList:
    def __init__(self, l1: ListNode, l2: ListNode, carry: int = 0):
        
        self.val = l1.val + l2.val + carry
        
        next_carry = 0
        if self.val > 9:
            next_carry, self.val = divmod(self.val, 10)
        
        l1next = l1.next or ListNode(0)
        l2next = l2.next or ListNode(0)
        if l1.next or l2.next or next_carry:
            self.next = SumList(l1next, l2next, next_carry)
        else:
            self.next = None


class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        return SumList(l1, l2)
```

---

## A Posteriori: David
```python
def to_list(listnode):
    result_list = []
    while listnode.next:
        result_list.append(listnode.val)
        listnode = listnode.next
    result_list.append(listnode.val)
    return result_list

def to_listnode(iterable):
    listnode = ListNode(iterable[0])
    current_node = listnode
    for x in iterable[1:]:
        new_node = ListNode(x)
        current_node.next = new_node
        current_node = new_node
    return listnode

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        l1_list = to_list(l1)[::-1]
        l2_list = to_list(l2)[::-1]
        number_1 = int("".join(map(str, l1_list)))
        number_2 = int("".join(map(str, l2_list)))
        result = str(number_1 + number_2)
        return to_listnode(result[::-1])
```