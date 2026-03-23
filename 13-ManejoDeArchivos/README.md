# 17 · Manejo de Archivos

> **Objetivo:** Leer y escribir archivos de texto, CSV y JSON para que tus programas persistan datos.

---

## ¿Qué aprenderás aquí?

- Abrir, leer y escribir archivos de texto
- Context manager `with open()`
- Modos de apertura
- Trabajar con CSV
- Trabajar con JSON
- Módulos `os` y `pathlib` para rutas

---

## 1. Abrir archivos con `open()`

```python
# Forma básica (debes cerrar manualmente)
archivo = open("datos.txt", "r")
contenido = archivo.read()
archivo.close()

# Forma recomendada: with (cierra automáticamente)
with open("datos.txt", "r") as archivo:
    contenido = archivo.read()
# El archivo se cierra aquí, aunque haya error
```

### Modos de apertura

| Modo | Significado |
|------|-------------|
| `"r"` | Leer (por defecto) |
| `"w"` | Escribir (crea o sobreescribe) |
| `"a"` | Agregar al final |
| `"x"` | Crear (error si ya existe) |
| `"r+"` | Leer y escribir |
| `"rb"` | Leer en modo binario |

---

## 2. Leer archivos de texto

```python
# Leer todo el contenido como un string
with open("notas.txt", "r", encoding="utf-8") as f:
    contenido = f.read()
    print(contenido)

# Leer línea por línea (eficiente en archivos grandes)
with open("notas.txt", "r", encoding="utf-8") as f:
    for linea in f:
        print(linea.strip())   # strip() elimina el \n del final

# Leer todas las líneas como lista
with open("notas.txt", "r", encoding="utf-8") as f:
    lineas = f.readlines()   # ["línea 1\n", "línea 2\n", ...]

# Leer una sola línea
with open("notas.txt", "r", encoding="utf-8") as f:
    primera = f.readline()
```

> Siempre usa `encoding="utf-8"` para evitar problemas con caracteres especiales como tildes.

---

## 3. Escribir archivos de texto

```python
# Escribir (crea o sobreescribe)
with open("salida.txt", "w", encoding="utf-8") as f:
    f.write("Primera línea\n")
    f.write("Segunda línea\n")

# Agregar al final (no sobreescribe)
with open("log.txt", "a", encoding="utf-8") as f:
    f.write("Nueva entrada de log\n")

# Escribir múltiples líneas
lineas = ["línea 1", "línea 2", "línea 3"]
with open("salida.txt", "w", encoding="utf-8") as f:
    f.writelines(linea + "\n" for linea in lineas)
```

---

## 4. Trabajar con CSV

```python
import csv

# Escribir CSV
datos = [
    ["nombre", "edad", "ciudad"],
    ["Ana", 25, "Santiago"],
    ["Luis", 30, "Lima"],
    ["María", 22, "Bogotá"],
]

with open("personas.csv", "w", newline="", encoding="utf-8") as f:
    writer = csv.writer(f)
    writer.writerows(datos)

# Leer CSV
with open("personas.csv", "r", encoding="utf-8") as f:
    reader = csv.reader(f)
    encabezado = next(reader)   # Salta la primera fila
    for fila in reader:
        print(fila)   # ["Ana", "25", "Santiago"]

# Leer CSV como diccionarios (más cómodo)
with open("personas.csv", "r", encoding="utf-8") as f:
    reader = csv.DictReader(f)
    for fila in reader:
        print(fila["nombre"], fila["edad"])
```

---

## 5. Trabajar con JSON

```python
import json

# Escribir JSON
datos = {
    "usuarios": [
        {"nombre": "Ana", "edad": 25},
        {"nombre": "Luis", "edad": 30}
    ],
    "total": 2
}

with open("datos.json", "w", encoding="utf-8") as f:
    json.dump(datos, f, indent=4, ensure_ascii=False)
    # indent=4: formato legible
    # ensure_ascii=False: permite tildes y ñ

# Leer JSON
with open("datos.json", "r", encoding="utf-8") as f:
    datos_leidos = json.load(f)

print(datos_leidos["total"])
print(datos_leidos["usuarios"][0]["nombre"])

# Convertir dict a string JSON (sin archivo)
json_string = json.dumps(datos, indent=2)
print(json_string)

# Convertir string JSON a dict
diccionario = json.loads('{"nombre": "Ana", "edad": 25}')
```

---

## 6. Verificar si un archivo existe

```python
import os

# Con os
if os.path.exists("datos.txt"):
    print("El archivo existe")

if os.path.isfile("datos.txt"):
    print("Es un archivo")

if os.path.isdir("carpeta"):
    print("Es un directorio")

# Con pathlib (más moderno)
from pathlib import Path

archivo = Path("datos.txt")
if archivo.exists():
    print("Existe:", archivo.name)
    print("Extensión:", archivo.suffix)   # ".txt"
    print("Carpeta:", archivo.parent)
```

---

## 7. Rutas con `pathlib`

```python
from pathlib import Path

# Construir rutas de forma segura (funciona en Windows y Linux)
carpeta = Path("datos")
archivo = carpeta / "usuarios.json"

# Crear directorio si no existe
carpeta.mkdir(exist_ok=True)

# Leer y escribir directamente
archivo.write_text('{"nombre": "Ana"}', encoding="utf-8")
contenido = archivo.read_text(encoding="utf-8")

# Listar archivos de una carpeta
for f in Path(".").iterdir():
    print(f.name)

# Buscar por patrón
for txt in Path(".").glob("*.txt"):
    print(txt)
```

---

## Ejemplo integrador: agenda de contactos

```python
import json
from pathlib import Path

ARCHIVO = Path("contactos.json")

def cargar_contactos():
    if ARCHIVO.exists():
        return json.loads(ARCHIVO.read_text(encoding="utf-8"))
    return {}

def guardar_contactos(contactos):
    ARCHIVO.write_text(json.dumps(contactos, indent=2, ensure_ascii=False), encoding="utf-8")

def agregar_contacto(nombre, telefono):
    contactos = cargar_contactos()
    contactos[nombre] = telefono
    guardar_contactos(contactos)
    print(f"Contacto '{nombre}' guardado.")

def buscar_contacto(nombre):
    contactos = cargar_contactos()
    telefono = contactos.get(nombre)
    if telefono:
        print(f"{nombre}: {telefono}")
    else:
        print("Contacto no encontrado.")

agregar_contacto("Ana García", "+56 9 1234 5678")
buscar_contacto("Ana García")
```

---

## Ejercicio propuesto

Crea un programa que lea un archivo de texto con nombres de estudiantes y notas (uno por línea, separados por coma), calcule el promedio de cada uno y guarde el resultado en un nuevo archivo CSV con columnas: nombre, promedio, estado (Aprobado/Reprobado).

---

## Siguiente carpeta

➡️ [`18_Excepciones`](../18_Excepciones/README.md)