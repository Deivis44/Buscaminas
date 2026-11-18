# Buscaminas pirata

Guía un barco hasta el tesoro sin tocar minas ni salir del mapa. Este proyecto de consola en C++ lee un tablero y una secuencia de instrucciones desde un archivo de texto, simula la ruta y registra el resultado. Fue el proyecto final de Programación Básica en la Universidad Distrital (2022-III).

[Demostración en video](https://www.youtube.com/watch?v=ysYxtQjMuvY)

## Compilar y jugar

Desde la raíz del repositorio, compila [`Proyecto_Final.cpp`](Proyecto_Final.cpp) con GNU C++. El código usa arreglos de longitud variable, por eso los comandos seleccionan el modo GNU.

**Linux**

```bash
g++ -std=gnu++17 Proyecto_Final.cpp -o buscaminas
./buscaminas
```

**Windows (PowerShell con MinGW/GCC)**

```powershell
g++ -std=gnu++17 Proyecto_Final.cpp -o buscaminas.exe
.\buscaminas.exe
```

Cuando aparezcan las dos preguntas, escribe un nombre de una sola palabra y el nombre del mapa con extensión. Para empezar, usa `game1.txt`. En Linux pueden aparecer mensajes de que `cls` y `PAUSE` no existen. La simulación continúa sin limpiar la pantalla ni hacer esas pausas.

## Crear un mapa

Cada archivo contiene, en orden, las dimensiones `filas columnas`, la cuadrícula, las coordenadas de partida, las coordenadas del tesoro, la orientación inicial y la cantidad de instrucciones. La última línea contiene las instrucciones separadas por un espacio.

- En la cuadrícula, `0` indica agua libre y `1`, una mina.
- Las coordenadas usan el orden `fila columna` y empiezan en `1`.
- La orientación inicial puede ser `N`, `S`, `E` u `O` (oeste).
- `A` avanza una casilla, `I` gira a la izquierda y `D` gira a la derecha. Los giros también cuentan como instrucciones. Se admiten entre 2 y 40.

Por ejemplo, [`game1.txt`](game1.txt) usa este tablero de 4 × 5:

```text
4 5
0 1 0 0 0
1 0 1 1 0
0 0 0 0 0
0 0 0 0 0
2 2
1 3
E
16
D A A I A A I A D A I A A I A A
```

## Mapas incluidos

| Mapa | Resultado | `ROBCOM.txt` |
| --- | --- | --- |
| [`game1.txt`](game1.txt) | Alcanza el tesoro en 16 instrucciones | `C` |
| [`game2.txt`](game2.txt) | Choca con una mina | `E` |
| [`game3.txt`](game3.txt) | Choca con el borde del mapa | `E` |
| [`game4.txt`](game4.txt) | Agota las instrucciones antes de llegar | `E` |
| [`game5.txt`](game5.txt) | Alcanza el tesoro en 26 instrucciones | `C` |

La ejecución puede sobrescribir `ROBCOM.txt` en el directorio actual. El archivo registra `C` si el barco alcanza el tesoro y `E` si la ruta se evaluó y no llegó.
