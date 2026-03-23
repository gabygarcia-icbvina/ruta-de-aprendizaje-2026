# 13 · Diccionarios

> **Objetivo:** Almacenar y acceder a datos mediante claves descriptivas en lugar de índices numéricos.

---

## ¿Qué aprenderás aquí?

- Crear y acceder a diccionarios
- Agregar, modificar y eliminar claves
- Iterar sobre diccionarios
- Diccionarios anidados
- Dict comprehensions

---

## 1. ¿Qué es un diccionario?

Un diccionario guarda pares **clave: valor**. Las claves son únicas y permiten acceder al dato de forma descriptiva.

```python
persona = {
    "nombre": "Ana García",
    "edad": 28,
    "ciudad": "Santiago",
    "activo": True
}
```

---

## 2. Acceder a valores

```python
persona = {"nombre": "Ana", "edad": 28}

# Con corchetes (lanza KeyError si no existe)
print(persona["nombre"])    # Ana

# Con .get() (devuelve None o valor por defecto si no existe)
print(persona.get("edad"))          # 28
print(persona.get("altura"))        # None
print(persona.get("altura", 0.0))   # 0.0 (valor por defecto)
```

---

## 3. Agregar y modificar

```python
contacto = {"nombre": "Luis", "telefono": "123456"}

# Modificar valor existente
contacto["telefono"] = "789012"

# Agregar nueva clave
contacto["email"] = "luis@mail.com"
contacto["ciudad"] = "Lima"

print(contacto)
```

---

## 4. Eliminar elementos

```python
datos = {"a": 1, "b": 2, "c": 3, "d": 4}

# del — elimina la clave
del datos["a"]

# pop() — elimina y retorna el valor
valor = datos.pop("b")
print(valor)   # 2

# pop() con valor por defecto (no lanza error si no existe)
datos.pop("z", None)

# popitem() — elimina y retorna el último par insertado
ultimo = datos.popitem()
print(ultimo)   # ("d", 4)

# clear() — vacía el diccionario
datos.clear()
```

---

## 5. Verificar existencia de claves

```python
usuario = {"nombre": "María", "edad": 30}

print("nombre" in usuario)     # True
print("email" in usuario)      # False
print("email" not in usuario)  # True
```

---

## 6. Iterar sobre un diccionario

```python
producto = {"nombre": "Laptop", "precio": 999, "stock": 15}

# Solo claves
for clave in producto:
    print(clave)

# Solo valores
for valor in producto.values():
    print(valor)

# Claves y valores juntos
for clave, valor in producto.items():
    print(f"{clave}: {valor}")
```

---

## 7. Longitud y copia

```python
config = {"debug": True, "version": "1.0", "max_users": 100}

print(len(config))   # 3

# Copiar (mismo problema que las listas con =)
copia = config.copy()
```

---

## 8. Diccionarios anidados

```python
empresa = {
    "nombre": "TechCorp",
    "empleados": {
        "ana": {"edad": 28, "cargo": "Desarrolladora"},
        "luis": {"edad": 35, "cargo": "Gerente"}
    },
    "activa": True
}

# Acceder a datos anidados
print(empresa["empleados"]["ana"]["cargo"])   # Desarrolladora

# Modificar dato anidado
empresa["empleados"]["luis"]["edad"] = 36
```

---

## 9. Dict comprehensions

```python
# Forma tradicional
cuadrados = {}
for n in range(1, 6):
    cuadrados[n] = n ** 2

# Con comprehension
cuadrados = {n: n ** 2 for n in range(1, 6)}
print(cuadrados)   # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Con condición
pares = {n: n ** 2 for n in range(1, 11) if n % 2 == 0}

# Invertir claves y valores
original = {"a": 1, "b": 2, "c": 3}
invertido = {v: k for k, v in original.items()}
print(invertido)   # {1: "a", 2: "b", 3: "c"}
```

---

## 10. Tipos válidos como claves

Las claves deben ser **inmutables**:

```python
# ✅ Válidas como clave
d = {
    "texto": 1,
    42: 2,
    3.14: 3,
    True: 4,
    (1, 2): 5    # Tupla: inmutable, válida
}

# ❌ Inválidas como clave
d = {[1, 2]: "valor"}   # TypeError: lista no es hashable
```

---

## Ejemplo integrador

```python
def crear_inventario():
    inventario = {}
    print("=== Registro de inventario ===")
    
    while True:
        nombre = input("Producto (o 'fin'): ")
        if nombre == "fin":
            break
        precio = float(input("Precio: "))
        stock = int(input("Stock: "))
        inventario[nombre] = {"precio": precio, "stock": stock}
    
    return inventario

def mostrar_inventario(inventario):
    print("\n--- Inventario ---")
    for producto, datos in inventario.items():
        print(f"{producto}: ${datos['precio']} | Stock: {datos['stock']}")

inv = crear_inventario()
mostrar_inventario(inv)
```

---

## Ejercicio propuesto

Crea un diccionario que represente un estudiante con claves: nombre, notas (lista), carrera. Luego calcula su promedio, agrega una nueva nota y determina si aprobó (promedio >= 60).

---

## Siguiente carpeta

➡️ [`14_F-Strings`](../14_F-Strings/README.md)