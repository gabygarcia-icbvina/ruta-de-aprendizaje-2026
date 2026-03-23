# 06 · Bucles

> **Objetivo:** Repetir acciones automáticamente usando `for` y `while`.

---

## ¿Qué aprenderás aquí?

- Bucle `while`: repetir mientras una condición sea verdadera
- Bucle `for`: iterar sobre secuencias
- `range()` para generar secuencias de números
- Control de flujo: `break`, `continue`, `pass`
- Bucle `for` con `else`

---

## 1. Bucle `while`

Se repite **mientras** la condición sea `True`. Debes asegurarte de que en algún momento la condición se vuelva `False`, o el bucle será infinito.

```python
contador = 1

while contador <= 5:
    print("Iteración:", contador)
    contador += 1   # ← Esto evita el bucle infinito

print("Fin del bucle")
```

**Salida:**
```
Iteración: 1
Iteración: 2
Iteración: 3
Iteración: 4
Iteración: 5
Fin del bucle
```

### Patrón común: pedir dato hasta que sea válido
```python
edad = -1

while edad < 0:
    edad = int(input("Ingresa tu edad (número positivo): "))
    if edad < 0:
        print("La edad no puede ser negativa, intenta de nuevo.")

print("Edad registrada:", edad)
```

---

## 2. Bucle `for`

Itera sobre cada elemento de una secuencia (lista, string, range, etc.).

```python
# Iterar sobre una lista
frutas = ["manzana", "naranja", "pera"]

for fruta in frutas:
    print("Fruta:", fruta)
```

```python
# Iterar sobre un string (carácter por carácter)
for letra in "Python":
    print(letra)
```

---

## 3. `range()` — generar secuencias de números

```python
range(stop)           # 0 hasta stop-1
range(start, stop)    # start hasta stop-1
range(start, stop, step)  # con salto
```

```python
for i in range(5):
    print(i)           # 0, 1, 2, 3, 4

for i in range(1, 6):
    print(i)           # 1, 2, 3, 4, 5

for i in range(0, 10, 2):
    print(i)           # 0, 2, 4, 6, 8

for i in range(10, 0, -1):
    print(i)           # 10, 9, 8, ..., 1  (cuenta regresiva)
```

---

## 4. `break` — salir del bucle

```python
for numero in range(1, 100):
    if numero % 7 == 0:
        print("Primer múltiplo de 7:", numero)
        break   # Sale del bucle en cuanto lo encuentra
```

```python
# break en while
while True:
    respuesta = input("¿Quieres salir? (si/no): ")
    if respuesta == "si":
        break
print("Adiós")
```

---

## 5. `continue` — saltar una iteración

```python
for i in range(1, 11):
    if i % 2 == 0:
        continue    # Salta los pares
    print(i)        # Solo imprime impares: 1, 3, 5, 7, 9
```

---

## 6. `pass` — placeholder vacío

Útil cuando necesitas un bloque pero aún no escribes el código:

```python
for i in range(5):
    pass   # Aún no sé qué hacer aquí, pero el bucle es válido
```

---

## 7. Bucles anidados

```python
for fila in range(1, 4):
    for columna in range(1, 4):
        print(fila, "x", columna, "=", fila * columna)
    print("---")
```

---

## 8. `for` con `else`

El bloque `else` se ejecuta cuando el bucle termina normalmente (sin `break`):

```python
numeros = [1, 3, 5, 7, 9]

for n in numeros:
    if n % 2 == 0:
        print("Encontré un par:", n)
        break
else:
    print("No hay números pares en la lista")
```

---

## 9. Funciones útiles con `for`

```python
nombres = ["Ana", "Luis", "María"]

# enumerate: obtener índice y valor
for i, nombre in enumerate(nombres):
    print(i, "→", nombre)

# zip: iterar dos listas en paralelo
edades = [25, 30, 22]
for nombre, edad in zip(nombres, edades):
    print(nombre, "tiene", edad, "años")
```

---

## Ejemplo integrador

```python
print("=== Suma acumulativa ===")
total = 0
contador = 0

while True:
    entrada = input("Ingresa un número (o 'fin' para terminar): ")
    if entrada.lower() == "fin":
        break
    total += float(entrada)
    contador += 1

if contador > 0:
    promedio = total / contador
    print(f"Suma total: {total}")
    print(f"Promedio: {round(promedio, 2)}")
else:
    print("No ingresaste ningún número.")
```

---

## Ejercicio propuesto

Escribe un programa que imprima la tabla de multiplicar del número que el usuario ingrese (del 1 al 10).

---

## Siguiente carpeta

➡️ [`07_Logica_Booleana`](../07_Logica_Booleana/README.md)