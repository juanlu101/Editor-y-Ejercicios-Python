# Cuaderno de Python

Editor de código tipo Google Colab para aprender Python, pensado para estudiantes que empiezan.
Realizado por **Juan Luis Torralbo Muñoz**.

Funciona **completamente sin conexión**.

## Qué hay en el paquete

```
cuaderno-python/
├── index.html          ← el cuaderno entero (85 KB)
└── pyodide/            ← el motor de Python (13 MB)
    ├── pyodide.js
    ├── pyodide.mjs
    ├── pyodide.asm.mjs
    ├── pyodide.asm.wasm
    ├── python_stdlib.zip
    └── pyodide-lock.json
```

## Cada celda es un programa independiente

A diferencia de Google Colab, aquí **las variables no se comparten entre celdas**. Al ejecutar una celda, Python arranca de cero: lo que definas en una no existe en las demás.

Es deliberado. Evita el problema clásico de que el programa de un estudiante "funciona" solo porque ejecutó otra celda hace media hora, y obliga a que cada ejercicio esté completo en una sola celda. Lo que se ve en la celda es exactamente lo que se ejecuta, y lo que entregan es lo que corrige.

## Qué incluye

- **Formato cuaderno**: celdas de código y de texto, que se pueden añadir, mover y borrar.
- **Python de verdad**: funcionan `math`, `random`, `input()` y toda la biblioteca estándar.
- **Coloreado de sintaxis**: palabras clave, funciones incorporadas, cadenas, números y comentarios.
- **Sin f-strings**: todo el material enseña a mezclar texto y variables con `print("Tengo", edad, "años")`, y los decimales con `round()`.
- **Sin sangría automática**, a propósito. `Tab` escribe 4 espacios y nada más. En *Ajustes* se puede activar la vista de la sangría con puntitos (`····`), muy útil para cazar errores de espacios.
- **54 ejercicios** en 8 bloques progresivos, de `print()` a funciones, cada uno con su ejemplo de salida y una pista opcional. El bloque de condicionales termina con cuatro problemas largos de reglas encadenadas (envío, factura de la luz, parking y nota final).
- **Apuntes** de consulta en la pestaña de al lado, en el mismo orden que los ejercicios.
- **Descargar / Abrir** en formato `.ipynb`, compatible con Jupyter y Google Colab.
- **Protección contra bucles infinitos**: si un programa pasa de 20 segundos se corta con un mensaje explicativo, en vez de bloquear la pestaña.
- **Errores en castellano**: además del mensaje de Python, una pista traducida para los fallos más habituales de principiante.

## Atajos de teclado

| Atajo | Qué hace |
|---|---|
| `Ctrl` + `Enter` | Ejecuta la celda |
| `Shift` + `Enter` | Ejecuta y pasa a la siguiente |
| `Ctrl` + `S` | Descarga el cuaderno |
| `Tab` | Escribe 4 espacios |
| `Shift` + `Tab` | Quita 4 espacios |

## Navegadores

Chrome, Edge, Firefox y Safari actualizados, en ordenador y en tablet. En móvil el índice se abre con el botón *Índice* de la cabecera.
