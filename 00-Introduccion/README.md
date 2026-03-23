# 01 · Introducción — Instalación y Hola Mundo

> **Objetivo:** Tener Python funcionando en tu máquina y ejecutar tu primer programa.

---

## ¿Qué aprenderás aquí?

- Instalar Python 3 y Visual Studio Code
- Entender qué es un intérprete y cómo ejecuta código
- Escribir y correr tu primer script
- Conocer la terminal / consola

---

## 1. Instalación de Python

### Windows
1. Ve a [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Descarga la versión más reciente de Python 3
3. **Importante:** marca la casilla _"Add Python to PATH"_ antes de instalar
4. Verifica la instalación abriendo una terminal y ejecutando:

```bash
python --version
```

### macOS
```bash
# Con Homebrew (recomendado)
brew install python
python3 --version
```

### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install python3 python3-pip
python3 --version
```

---

## 2. Instalación de Visual Studio Code

1. Descarga VS Code desde [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Instala la extensión oficial de Python:
   - Abre VS Code → `Ctrl+Shift+X` (Extensions)
   - Busca **"Python"** (Microsoft) e instálala
3. Selecciona el intérprete de Python:
   - `Ctrl+Shift+P` → escribe _"Python: Select Interpreter"_ → elige la versión instalada

---

## 3. Tu primer programa

Crea un archivo llamado `hola_mundo.py` y escribe lo siguiente:

```python
print("¡Hola, mundo!")
```

### ¿Cómo ejecutarlo?

**Desde VS Code:**
- Haz clic en el botón ▶ (Run) en la esquina superior derecha
- O usa el atajo `Ctrl+F5`

**Desde la terminal:**
```bash
python hola_mundo.py
# En Mac/Linux puede ser:
python3 hola_mundo.py
```

**Salida esperada:**
```
¡Hola, mundo!
```

---

## 4. Entender qué pasa

```python
print("¡Hola, mundo!")
#  ^     ^
#  |     Argumento: el texto que se mostrará
#  Función incorporada de Python
```

- `print()` es una **función** que ya viene con Python. Su trabajo es mostrar texto en la pantalla.
- Las comillas (`"..."`) indican que el contenido es texto (más adelante aprenderás que se llama **string**).

---

## 5. Comentarios en Python

Los comentarios son notas para humanos; Python los ignora completamente.

```python
# Esto es un comentario de una línea

"""
Esto es un comentario
de múltiples líneas
(técnicamente es un string sin asignar)
"""

print("Hola")  # También puedo comentar al final de una línea
```

---

## 6. Errores comunes al empezar

| Error | Causa | Solución |
|-------|-------|----------|
| `python: command not found` | Python no está en PATH | Reinstala marcando "Add to PATH" |
| `SyntaxError` | Falta una comilla o paréntesis | Revisa que `print("...")` esté completo |
| No pasa nada al ejecutar | Guardaste el archivo sin extensión `.py` | Asegúrate de que se llame `archivo.py` |

---

## Ejercicio propuesto

Modifica `hola_mundo.py` para que imprima tres líneas distintas: tu nombre, tu edad y tu ciudad.

```python
print("Mi nombre es Ana")
print("Tengo 25 años")
print("Vivo en Santiago")
```

---

## Siguiente carpeta

➡️ [`02_Variables_y_Tipos`](../02_Variables_y_Tipos/README.md)