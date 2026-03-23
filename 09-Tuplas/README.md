# 12 · Tuplas

> **Objetivo:** Entender cuándo y por qué usar tuplas en lugar de listas.

---

## ¿Qué aprenderás aquí?

- Qué es una tupla y cómo crearla
- Diferencias clave con las listas
- Cuándo usar tuplas
- Desempaquetado de tuplas
- Tuplas con un solo elemento
- Funciones que retornan tuplas

---

## 1. ¿Qué es una tupla?

Una tupla es una colección **ordenada e inmutable** — una vez creada, no se puede modificar.

```python
coordenadas = (40.7128, -74.0060)
colores_rgb = (255, 128, 0)
punto_3d = (1, 2, 3)
```

---

## 2. Crear tuplas

```python
# Con paréntesis
t1 = (1, 2, 3)

# Sin paréntesis (menos común pero válido)
t2 = 1, 2, 3

# Tupla vacía
vacia = ()

# Tupla de un solo elemento (¡coma obligatoria!)
uno = (42,)         # ✅ Esto es una tupla
no_tupla = (42)     # ❌ Esto es solo el número 42 con paréntesis

print(type(uno))        # <class 'tuple'>
print(type(no_tupla))   # <class 'int'>
```

---

## 3. Acceder a elementos

Igual que las listas: indexación y slicing funcionan igual.

```python
frutas = ("manzana", "naranja", "pera", "uva")

print(frutas[0])     # manzana
print(frutas[-1])    # uva
print(frutas[1:3])   # ("naranja", "pera")

for fruta in frutas:
    print(fruta)
```

---

## 4. Inmutabilidad — no se puede cambiar

```python
punto = (3, 5)
punto[0] = 10   # TypeError: 'tuple' object does not support item assignment
```

Pero si contiene listas, esas listas sí son mutables:

```python
datos = ([1, 2], [3, 4])
datos[0].append(5)
print(datos)   # ([1, 2, 5], [3, 4])  — la tupla no cambió, pero su lista interior sí
```

---

## 5. Métodos disponibles

Las tuplas solo tienen dos métodos (no pueden modificarse):

```python
colores = ("rojo", "azul", "rojo", "verde")

print(colores.count("rojo"))   # 2
print(colores.index("azul"))   # 1
```

---

## 6. Desempaquetado de tuplas

```python
punto = (3, 7)
x, y = punto
print(x)   # 3
print(y)   # 7

# Con más valores
nombre, edad, ciudad = ("Ana", 25, "Santiago")

# Ignorar valores con _
primero, _, tercero = (1, 2, 3)
print(primero, tercero)   # 1 3

# Capturar el resto con *
a, *resto = (1, 2, 3, 4, 5)
print(a)       # 1
print(resto)   # [2, 3, 4, 5]

primero, *medio, ultimo = (1, 2, 3, 4, 5)
print(primero, medio, ultimo)   # 1 [2, 3, 4] 5
```

---

## 7. Retorno múltiple en funciones (son tuplas)

```python
def calcular_estadisticas(numeros):
    return min(numeros), max(numeros), sum(numeros) / len(numeros)

minimo, maximo, promedio = calcular_estadisticas([4, 7, 2, 9, 1])
print(f"Min: {minimo}, Max: {maximo}, Prom: {promedio}")
```

---

## 8. Cuándo usar tuplas vs listas

| Característica | Lista | Tupla |
|----------------|-------|-------|
| Mutable | ✅ Sí | ❌ No |
| Velocidad | Normal | Más rápida |
| Usa como clave de dict | ❌ No | ✅ Sí |
| Intención | Colección que puede cambiar | Datos fijos |

### Casos ideales para tuplas

```python
# Coordenadas (no cambian)
santiago = (-33.45, -70.66)

# Configuración fija
COLORES_PERMITIDOS = ("rojo", "verde", "azul")

# Registro de datos (como una fila de tabla)
empleado = ("Juan Pérez", 35, "Ingeniería", 85000)

# Claves de diccionario
ubicaciones = {
    (0, 0): "origen",
    (1, 0): "derecha",
    (0, 1): "arriba"
}
```

---

## 9. Conversión entre listas y tuplas

```python
lista = [1, 2, 3]
tupla = tuple(lista)   # Convierte lista a tupla

tupla2 = (4, 5, 6)
lista2 = list(tupla2)  # Convierte tupla a lista
lista2.append(7)
```

---

## Ejemplo integrador

```python
def obtener_datos_usuario():
    nombre = input("Nombre: ")
    edad = int(input("Edad: "))
    ciudad = input("Ciudad: ")
    return nombre, edad, ciudad   # Retorna tupla

def mostrar_usuario(datos):
    nombre, edad, ciudad = datos
    print(f"Nombre: {nombre}")
    print(f"Edad: {edad}")
    print(f"Ciudad: {ciudad}")

usuario = obtener_datos_usuario()
mostrar_usuario(usuario)

# Las tuplas permiten comparar registros fácilmente
usuarios = [
    ("Ana", 25, "Santiago"),
    ("Luis", 30, "Lima"),
    ("María", 22, "Bogotá")
]

por_edad = sorted(usuarios, key=lambda u: u[1])
for u in por_edad:
    print(u)
```

---

## Ejercicio propuesto

Crea una lista de tuplas donde cada tupla contenga: nombre de producto, precio y stock. Muestra el producto más barato, el más caro, y filtra los que tienen stock > 0.

---

## Siguiente carpeta

➡️ [`13_Diccionarios`](../13_Diccionarios/README.md)