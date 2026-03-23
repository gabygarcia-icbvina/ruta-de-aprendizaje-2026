# 15 · Sets (Conjuntos)

> **Objetivo:** Trabajar con colecciones de elementos únicos y realizar operaciones de conjuntos matemáticos.

---

## ¿Qué aprenderás aquí?

- Qué es un set y cómo crearlo
- Características principales: sin duplicados, sin orden
- Operaciones matemáticas: unión, intersección, diferencia
- Métodos para agregar y eliminar
- Cuándo usar sets en lugar de listas

---

## 1. ¿Qué es un set?

Un set es una colección **desordenada de elementos únicos**. Es como una lista pero:
- No permite duplicados
- No tiene orden (no se puede indexar)
- Es muy eficiente para buscar si un elemento existe

```python
# Crear un set
colores = {"rojo", "verde", "azul"}
numeros = {1, 2, 3, 4, 5}

# Los duplicados se eliminan automáticamente
repetidos = {1, 2, 2, 3, 3, 3}
print(repetidos)   # {1, 2, 3}
```

---

## 2. Crear sets

```python
# Desde cero con llaves
frutas = {"manzana", "pera", "uva"}

# Set vacío (¡no usar {} que crea un dict vacío!)
vacio = set()          # ✅ Set vacío
no_set = {}            # ❌ Diccionario vacío

# Desde una lista (elimina duplicados)
lista = [1, 2, 2, 3, 3, 3, 4]
s = set(lista)
print(s)   # {1, 2, 3, 4}

# Desde un string
letras = set("banana")
print(letras)   # {'b', 'a', 'n'} (sin orden)
```

---

## 3. Operaciones matemáticas de conjuntos

```python
a = {1, 2, 3, 4, 5}
b = {4, 5, 6, 7, 8}
```

### Unión `|` — todos los elementos de ambos
```python
print(a | b)          # {1, 2, 3, 4, 5, 6, 7, 8}
print(a.union(b))     # Equivalente
```

### Intersección `&` — solo los que están en ambos
```python
print(a & b)                # {4, 5}
print(a.intersection(b))    # Equivalente
```

### Diferencia `-` — los que están en a pero no en b
```python
print(a - b)                # {1, 2, 3}
print(a.difference(b))      # Equivalente
print(b - a)                # {6, 7, 8}
```

### Diferencia simétrica `^` — los que están en uno u otro, pero no en ambos
```python
print(a ^ b)                          # {1, 2, 3, 6, 7, 8}
print(a.symmetric_difference(b))      # Equivalente
```

---

## 4. Comparar conjuntos

```python
a = {1, 2, 3}
b = {1, 2, 3, 4, 5}

# Subconjunto: todos los de 'a' están en 'b'
print(a.issubset(b))    # True
print(a <= b)           # True

# Superconjunto: 'b' contiene todos los de 'a'
print(b.issuperset(a))  # True
print(b >= a)           # True

# Disjuntos: no tienen elementos en común
c = {10, 20}
print(a.isdisjoint(c))  # True
```

---

## 5. Agregar y eliminar elementos

```python
idiomas = {"español", "inglés"}

# Agregar un elemento
idiomas.add("francés")

# Agregar múltiples (desde iterable)
idiomas.update(["alemán", "italiano"])

# Eliminar (lanza KeyError si no existe)
idiomas.remove("alemán")

# Eliminar seguro (no lanza error si no existe)
idiomas.discard("chino")

# Sacar y retornar un elemento arbitrario
elemento = idiomas.pop()
print("Eliminado:", elemento)

# Vaciar
idiomas.clear()
```

---

## 6. Verificar membresía

```python
permisos = {"leer", "escribir", "ejecutar"}

print("leer" in permisos)       # True  — O(1), muy rápido
print("borrar" in permisos)     # False
print("borrar" not in permisos) # True
```

> Buscar en un set es **mucho más rápido** que en una lista, especialmente con miles de elementos.

---

## 7. Set comprehensions

```python
cuadrados = {x ** 2 for x in range(1, 6)}
print(cuadrados)   # {1, 4, 9, 16, 25}

pares = {x for x in range(1, 11) if x % 2 == 0}
print(pares)   # {2, 4, 6, 8, 10}
```

---

## 8. Casos de uso típicos

### Eliminar duplicados de una lista
```python
con_duplicados = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3]
sin_duplicados = list(set(con_duplicados))
print(sin_duplicados)
```

### Verificar si dos grupos tienen elementos en común
```python
equipo_a = {"Ana", "Luis", "Pedro"}
equipo_b = {"Carlos", "Luis", "Sofía"}

comunes = equipo_a & equipo_b
print("Están en ambos equipos:", comunes)  # {"Luis"}
```

### Encontrar elementos únicos de cada grupo
```python
solo_en_a = equipo_a - equipo_b
solo_en_b = equipo_b - equipo_a
print("Solo en A:", solo_en_a)
print("Solo en B:", solo_en_b)
```

---

## Resumen de comparación

| Característica | Lista | Tuple | Set | Dict |
|----------------|-------|-------|-----|------|
| Ordenado | ✅ | ✅ | ❌ | ✅ (Python 3.7+) |
| Duplicados | ✅ | ✅ | ❌ | ❌ (claves) |
| Indexable | ✅ | ✅ | ❌ | por clave |
| Mutable | ✅ | ❌ | ✅ | ✅ |

---

## Ejemplo integrador

```python
def analizar_audiencias(evento_a, evento_b):
    """Analiza solapamiento entre dos listas de asistentes."""
    set_a = set(evento_a)
    set_b = set(evento_b)

    ambos = set_a & set_b
    solo_a = set_a - set_b
    solo_b = set_b - set_a
    todos = set_a | set_b

    print(f"Asistieron a ambos eventos: {len(ambos)} → {ambos}")
    print(f"Solo al evento A: {len(solo_a)}")
    print(f"Solo al evento B: {len(solo_b)}")
    print(f"Total de personas únicas: {len(todos)}")

evento_a = ["Ana", "Luis", "María", "Ana", "Pedro"]
evento_b = ["Carlos", "Luis", "Sofía", "María"]
analizar_audiencias(evento_a, evento_b)
```

---

## Ejercicio propuesto

Dado el historial de compras de dos usuarios (como listas de productos con posibles repeticiones), encuentra: productos que ambos compraron, productos únicos de cada uno, y el total de productos distintos entre los dos.

---

## Siguiente carpeta

➡️ [`16_Metodos_de_Diccionarios`](../16_Metodos_de_Diccionarios/README.md)