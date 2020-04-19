# Python, kata e almorzo / Python, virtual kata y desayuno - 7ª Edición (Virtual Meetup)

**¡¡ESTE DOCUMENTO SE ACTUALIZARÁ ANTES Y DURANTE EL EVENTO!!**

Hola de nuevo!

Debido a situación actual la sesión la realizaremos de manera virtual.

Y ahora más que nunca, breves instrucciones a continuación para que todo vaya fluido!

1. Nos juntaremos en la sala virtual que publicaremos minutos antes del evento.
2. Actualizaremos este documento con un primer ejercicio a realizar de https://leetcode.com/
3. Nos dividiremos en grupos de 2-3 personas para realizar el ejercicio. Uno de los participantes (driver/conductor) debe compartir pantalla mientra que el resto actuan como navegadores u observadores.
4. Resolveremos el problema en iteraciones de 10 minutos.
5. Al final cada iteración decideremos entre todos los grupos si damos finalizado el problema o continuamos iterando para refactorizar.
6. Finalizado el problema, retomaremos la reunión en la sala principal y copiaremos la solución en este documento en el espacio reservado para cada grupo.
8. Revisaremos y comentaremos soluciones de cada grupo.
9. Revisaremos soluciones de otros usuarios en Leetcode en Python, y en otros lenguajes.
10. Si queda tiempo volvemos al _Paso 2_.

Además..

1. Los grupos de 2-3 personas se reunirán en salas independientes y el conductor puede ir rotando en cada ejercicio.
1. Se puede acompañar de café, te, galletas, desayuno inglés...(recuerda teclear sin chocolate en los dedos)
1. No importa el nivel o la experiencia individual, lo importante es aprender todos de todos.
1. La reunión es informal y el objetivo es aprender pasando un buen rato!

Anteriores ediciones:
- [Primera Edición](https://hackmd.io/ZFqsaJQAQQGm8z2sPTwA3g)
- [Segunda Edición](https://hackmd.io/FO4AHdfHTASNM_1ahFn8DQ)
- [Tercera Edición](https://hackmd.io/-sF1xb0ASkC98ArsOgdItA?view)
- [Cuarta Edición](https://hackmd.io/@aindustriosa/B1cQ0DdZU)
- [Quinta Edición](https://hackmd.io/@aindustriosa/H1lc-qgG8)
- [Sexta Edición](https://hackmd.io/@aindustriosa/H1sgaq9MI)


## Datos de acceso

* URL Sala principal: https://meet.jit.si/AIndustriosa__PythonKataEAlmorzo
* Contraseña: cuarentena

## Ejercicios

* https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/
* https://leetcode.com/problems/maximum-69-number/


### Grupo 1
* Participantes: Rastersoft, Yoshua Lino
* URL Sala: https://meet.jit.si/AIndustriosa__PythonKataEAlmorzo_grupo_1

_Código:_

```python
# Work in progress
class Solution:
    def removeDuplicates(self, S: str) -> str:
        if len(S) < 2:
            return S
        while True:
            cambiado = False
            for a in (range(len(S) - 1)):
                c1 = S[a]
                c2 = S[a+1]
                if c1 == c2:
                    S = S[:a] + S[a+2:]
                    cambiado = True
                    break
            if not cambiado:
                break
        return S
```

_Código:_

```python
# Work in progress

class Solution:
    def maximum69Number (self, num: int) -> int:
        return int(str(num).replace("6", "9", 1))
```

### Grupo 2
* Participantes:        Daniel, CyberMODEm
* URL Sala: https://meet.jit.si/AIndustriosa__PythonKataEAlmorzo_grupo_2

_Código:_
```python
# Work in progress
class Solution:
    def removeDuplicates(self, S: str) -> str:
      i = 1
      while i < len(S):
        i = 1
        while i < len(S):
            i += 1
            if S[i] == S[i+1]:
                j = i+1
                while S[i] = S[j+1]:
                    j = j+1
                S = S[:min(i-1, 0)] + S[min(j+1, len(S)):]
      return S

```

```python

class Solution:
    def maximum69Number (self, num: int) -> int:
        return int(str(num).replace('6', '9', 1))

```

### Grupo 3
* Participantes: Xurxo, Javier Lopez Pino
* URL Sala: https://meet.jit.si/AIndustriosa__PythonKataEAlmorzo_grupo_3

Alex -> "no me deja veros/hablar en vuestra sala"

_Código:_
```python
class Solution(object):
    def removeDuplicates(self, S):
        """
        :type S: str
        :rtype: str
        """
        result = " "
        for character in S:
            if (character == result[-1]):
                result = result[:-1]
            else:
                result = result + character
        return result[1:]


class Solution(object):
    def maximum69Number (self, num):
        strNum = str (num)
        posiblesResultados = []
        for x in range (0, len(strNum)):
            tmp = strNum
            if (strNum[x] == '6'):
                tmp = strNum[:x-1] + '9' + strNum[x:]
            else:
                tmp = strNum[:x-1] + '6' + strNum[x:]
            posiblesResultados.append(tmp)
        return int(max(posiblesResultados))

```

### Grupo 4
* Participantes: Tomás Dias Almeida
* URL Sala: https://meet.jit.si/AIndustriosa__PythonKataEAlmorzo_grupo_4

_Código:_
```python
# work in progress
# idea: stack 
class Solution(object):
    def removeDuplicates(self, S):
        keep = [' ']
        myList = S.split()
        for c in myList:
            elem = keep.pop()
            if c != elem:
                keep.append(elem)
                keep.append(c)
        return ''.join([str(elem) for elem in keep])

```

```python
# change first 6 to 9, concat the rest
#
class Solution(object):
    def maximum69Number (self, num):
        """
        :type num: int
        :rtype: int
        """
        result = ""
        S = str(num)
        changed = False
        for character in S:
            if character == '6' and changed == False:
                result += '9'
                changed = True
            else:
                result += character
        return result

class Solution(object):
    def maximum69Number (self, num):
        """
        :type num: int
        :rtype: int
        """
        newNum = 0
        divisor = 1000
        while (divisor != 0):
            numPosition = num // divisor
            if (numPosition == 6):
                newNum = newNum + (9*divisor) + (num%divisor)
                return newNum
            else: 
                newNum = newNum + (numPosition *divisor)
                num = (num%divisor)
                divisor = divisor // 10
        return newNum
```

## FRIKADAS


## Otros comentarios


