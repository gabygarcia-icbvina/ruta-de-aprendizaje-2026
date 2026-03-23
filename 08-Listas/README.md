# 10 · Listas

> **Objetivo:** Manejar colecciones ordenadas de datos usando listas.

---

## ¿Qué aprenderás aquí?

- Crear y acceder a listas
- Indexación y slicing
- Iterar sobre listas
- Listas anidadas (matrices)
- List comprehensions básicas

---

## 1. Crear una lista

```python
frutas = ["manzana", "naranja", "pera"]
numeros = [1, 2, 3, 4, 5]
mixta = [42, "hola", True, 3.14]   # Puede tener distintos tipos
vacia = []
```

---

## 2. Acceder a elementos (indexación)

Los índices empiezan en `0`:

```python
frutas = ["manzana", "naranja", "pera", "uva"]
#           0           1          2       3
#          -4          -3         -2      -1   (negativos)

print(frutas[0])    # manzana
print(frutas[2])    # pera
print(frutas[-1])   # uva     (último elemento)
print(frutas[-2])   # pera    (penúltimo)
```

---

## 3. Slicing — extraer sublistas

```python
numeros = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(numeros[2:5])    # [2, 3, 4]      (del índice 2 al 4)
print(numeros[:4])     # [0, 1, 2, 3]   (desde el inicio hasta 3)
print(numeros[6:])     # [6, 7, 8, 9]   (desde 6 hasta el final)
print(numeros[::2])    # [0, 2, 4, 6, 8] (de 2 en 2)
print(numeros[::-1])   # [9, 8, ..., 0]  (invertida)
```

---

## 4. Modificar una lista

```python
colores = ["rojo", "verde", "azul"]

# Cambiar un elemento
colores[1] = "amarillo"
print(colores)   # ["rojo", "amarillo", "azul"]

# Agregar al final
colores.append("morado")

# Insertar en posición
colores.insert(1, "cyan")

# Eliminar por valor
colores.remove("rojo")

# Eliminar por índice
del colores[0]

# Eliminar y obtener el valor
ultimo = colores.pop()       # Elimina el último
segundo = colores.pop(1)     # Elimina el de índice 1
```

---

## 5. Longitud y verificar existencia

```python
numeros = [3, 1, 4, 1, 5, 9]

print(len(numeros))        # 6
print(4 in numeros)        # True
print(7 in numeros)        # False
print(7 not in numeros)    # True
```

---

## 6. Iterar sobre una lista

```python
frutas = ["manzana", "pera", "uva"]

for fruta in frutas:
    print(fruta)

# Con índice
for i, fruta in enumerate(frutas):
    print(i, "→", fruta)

# Iterar en reversa
for fruta in reversed(frutas):
    print(fruta)
```

---

## 7. Ordenar y copiar

```python
numeros = [5, 2, 8, 1, 9, 3]

# sorted() devuelve una nueva lista
print(sorted(numeros))           # [1, 2, 3, 5, 8, 9]
print(sorted(numeros, reverse=True))  # [9, 8, 5, 3, 2, 1]

# .sort() modifica la original
numeros.sort()
print(numeros)   # [1, 2, 3, 5, 8, 9]

# Copiar una lista (no con =)
original = [1, 2, 3]
copia = original.copy()    # ✅ Copia real
alias = original           # ❌ Mismo objeto, no es copia
```

---

## 8. Funciones útiles con listas

```python
numeros = [3, 1, 4, 1, 5, 9, 2, 6]

print(min(numeros))    # 1
print(max(numeros))    # 9
print(sum(numeros))    # 31
print(len(numeros))    # 8
```

---

## 9. Listas anidadas (matrices)

```python
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(matriz[0])       # [1, 2, 3]
print(matriz[1][2])    # 6  (fila 1, columna 2)

# Iterar una matriz
for fila in matriz:
    for elemento in fila:
        print(elemento, end=" ")
    print()
```

---

## 10. List comprehensions

Una forma compacta de crear listas:

```python
# Forma tradicional
cuadrados = []
for x in range(1, 6):
    cuadrados.append(x ** 2)

# Con comprehension
cuadrados = [x ** 2 for x in range(1, 6)]
print(cuadrados)   # [1, 4, 9, 16, 25]

# Con condición
pares = [x for x in range(1, 11) if x % 2 == 0]
print(pares)   # [2, 4, 6, 8, 10]

# Transformar strings
frutas = ["manzana", "pera", "uva"]
mayusculas = [f.upper() for f in frutas]
```

---

## Ejemplo integrador

```python
notas = []
print("Ingresa 5 notas:")

for i in range(5):
    nota = float(input(f"Nota {i + 1}: "))
    notas.append(nota)

promedio = sum(notas) / len(notas)
aprobadas = [n for n in notas if n >= 60]

print(f"\nNotas: {notas}")
print(f"Promedio: {round(promedio, 1)}")
print(f"Nota más alta: {max(notas)}")
print(f"Nota más baja: {min(notas)}")
print(f"Notas aprobadas: {len(aprobadas)}/{len(notas)}")
```

---

## Ejercicio propuesto

Crea un programa que reciba una lista de temperaturas diarias (7 días) y muestre: promedio, día más caluroso, día más frío, y cuántos días superaron los 30°.

---

## Siguiente carpeta

➡️ [`11_Metodos_de_Listas`](../11_Metodos_de_Listas/README.md)