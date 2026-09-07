# Cuaderno de Python

Editor de código tipo Google Colab para aprender Python, pensado para estudiantes que empiezan.
Realizado por **Juan Luis Torralbo Muñoz**.

Funciona **completamente sin conexión**. No hay servidor, no hay backend, no hay CDN y no hay que instalar nada.

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

`pyodide/` es CPython **3.14.2** compilado a WebAssembly. Va incluido, así que el cuaderno no descarga nada de internet en ningún momento. Los dos elementos tienen que viajar juntos: si mueves `index.html`, lleva la carpeta al lado.

## Publicarlo en GitHub Pages

1. Crea un repositorio, por ejemplo `cuaderno-python`.
2. Sube `index.html` **y la carpeta `pyodide/`** a la raíz del repositorio.
3. **Settings → Pages**.
4. En *Source* elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`.
5. Guarda. En un par de minutos estará en `https://TU-USUARIO.github.io/cuaderno-python/`.

Ese enlace es el que reparten a los estudiantes.

### Probarlo en tu ordenador antes de subirlo

Al llevar el motor en local, los navegadores no permiten abrir `index.html` con doble clic (bloquean la lectura de archivos vecinos por seguridad). Levanta un servidor de un segundo desde la carpeta del paquete:

```
python -m http.server
```

y abre `http://localhost:8000`. En GitHub Pages no hace falta nada de esto: funciona directamente.

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

## Cómo entregan la tarea

El botón **Descargar** genera un `.ipynb` con el código, las entradas de cada celda y la salida obtenida. Ese archivo:

- se vuelve a cargar con el botón **Abrir**, para revisar ejercicios antiguos;
- se abre tal cual en Jupyter o en Google Colab, si prefieres corregir desde ahí;
- lleva el título del cuaderno en los metadatos, así que conviene que el estudiante ponga su nombre arriba antes de descargar.

Recuérdales que **nada se guarda al cerrar la pestaña**. El navegador avisa al salir, pero conviene insistir.

## El `input()` de los estudiantes

Cada celda de código tiene una caja plegable, *Entradas del programa*: ahí se escriben por adelantado las respuestas, una por línea, y los ejercicios ya vienen con ellas rellenas. Si se deja vacía, el navegador pregunta una a una en una ventanita. Las entradas se guardan también en el `.ipynb`, así que al corregir ves con qué datos se ejecutó.

## Modificar el contenido

Todo está en dos listas dentro de `index.html`, fáciles de localizar:

- `var EJERCICIOS = [...]` — cada ejercicio tiene:
  - `n` número, `b` bloque, `t` título
  - `e` enunciado (admite markdown: `**negrita**`, listas, tablas y bloques de código)
  - `s` ejemplo de salida. Lo que pongas entre `[[` y `]]` se resalta en amarillo como "esto lo teclea el usuario"
  - `i` entradas sugeridas, una por línea
  - `p` pista opcional
- `var APUNTES = [...]` — cada apartado tiene `t` (título) y `c` (contenido en markdown).
- `var BLOQUES = [...]` — los ocho bloques del índice.

Para añadir un ejercicio 55, copia la estructura de cualquier otro y añádelo a la lista. El índice se genera solo.

Si cambias un ejemplo de salida, comprueba que sea reproducible con `print()` y comas: recuerda que `print()` mete un espacio automático entre cada elemento, así que `print("¡Hola,", nombre, "!")` escribe `¡Hola, Ana !`.

## Actualizar el motor en el futuro

Descarga `pyodide-core-<version>.tar.bz2` de las [releases de Pyodide](https://github.com/pyodide/pyodide/releases), y sustituye el contenido de `pyodide/` por estos seis archivos: `pyodide.js`, `pyodide.mjs`, `pyodide.asm.mjs`, `pyodide.asm.wasm`, `python_stdlib.zip` y `pyodide-lock.json`. El resto del `.tar.bz2` es para Node y no hace falta.

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
