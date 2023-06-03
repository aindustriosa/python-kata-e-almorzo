###### tags `python-kata`

# Python, kata e almorzo / Python, kata y desayuno - 11ª Edición

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



### Grupo 1 - Integrantes:  Dani

#### Validar Sudoku
_Código:_

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        
        for fila in board:
            fila_filtrada = [num for num in fila if num != "."]
            if len(fila_filtrada) != len(set(fila_filtrada)):
                return False
        for columna in zip(*board):
            
            columna_filtrada = [num for num in columna if num != "."]
            if len(columna_filtrada) != len(set(columna_filtrada)):
                return False
        
        for fila in [0,3,6]:
            for columna in [0,3,6]:
                cuadrado = self.extraer_cuadrado(fila, columna, board)
                cuadrado_filtrado = [num for num in cuadrado if num != "."]
                if len(cuadrado_filtrado) != len(set(cuadrado_filtrado)):
                    return False
        return True

    def extraer_cuadrado(self, x: int, y: int, tablero: List[List[str]]):
        return tablero[x][y:y+3] + tablero[x+1][y:y+3] + tablero[x+2][y:y+3]
```

_Optimizado:_
```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:       
        lista_de_cuadrados = []
        for fila in [0,3,6]:
            for columna in [0,3,6]:
                lista_de_cuadrados.append( self.extraer_cuadrado(fila, columna, board))
        
        
        for tablero in [board, zip(*board), lista_de_cuadrados]:
            for fila in tablero:
                fila_filtrada = [num for num in fila if num != "."]
                if len(fila_filtrada) != len(set(fila_filtrada)):
                    return False
        return True

    def extraer_cuadrado(self, x: int, y: int, tablero: List[List[str]]):
        return tablero[x][y:y+3] + tablero[x+1][y:y+3] + tablero[x+2][y:y+3]
```


### Grupo 2 - Integrantes: 

_Código:_

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        
        # Check rows
        column_elements = []
        for row in range(len(board)):
            elements_repeated = Counter(board[row])
            if len(set(elements_repeated.values())) != 2:
                print("Invalid row")
                return False
            
            squares = [[], [], []]

            for i in range(len(board[row])):
                squares[int(i // 3)].append(board[row][i])
            
            if row % 3 == 0 and row != 0:
                for square in squares:
                    if len(set(Counter(square).values())) != 2:
                        print(squares)
                        return False
                squares = []

        # Check columns
        column_elements = []
        for index in range(0, 9):
            for i in range(len(board)):
                column_elements.append(board[i][index])
            
            if len(set(Counter(column_elements).values())) != 2:
                print("Invalid column")
                return False

            column_elements = []

        return True
            
```


## FRIKADAS

### One-liner
[Valid Sudoku One-liner](https://leetcode.com/problems/valid-sudoku/solutions/2788228/python-solution-one-liner/)