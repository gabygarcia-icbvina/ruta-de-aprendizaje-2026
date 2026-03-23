# 03 · Input y Output

> **Objetivo:** Hacer programas interactivos que reciban datos del usuario y muestren información de forma clara.

---

## ¿Qué aprenderás aquí?

- Recibir datos del usuario con `input()`
- Mostrar información con `print()`
- Formatear la salida: separadores, fin de línea, múltiples valores
- Convertir el input al tipo correcto

---

## 1. Salida con `print()`

### Uso básico
```python
print("Hola, mundo")
print(42)
print(3.14)
print(True)
```

### Múltiples valores separados por coma
```python
nombre = "Sofía"
edad = 30
print("Nombre:", nombre, "| Edad:", edad)
# Salida: Nombre: Sofía | Edad: 30
```

### Parámetro `sep` — cambia el separador
```python
print("2025", "03", "15", sep="-")   # 2025-03-15
print("a", "b", "c", sep=" / ")      # a / b / c
print("hola", "mundo", sep="")       # holamundo
```

### Parámetro `end` — cambia el fin de línea
```python
print("Cargando", end="")
print("...")
# Salida: Cargando...

print("Línea 1", end="\n\n")   # Agrega línea en blanco después
print("Línea 2")
```

### Imprimir una línea vacía
```python
print()   # Solo un salto de línea
```

---

## 2. Entrada con `input()`

`input()` pausa el programa, espera que el usuario escriba algo y presione Enter, y devuelve ese texto como **string**.

```python
nombre = input("¿Cómo te llamas? ")
print("Hola,", nombre)
```

### ⚠️ `input()` siempre devuelve un string

```python
edad = input("¿Cuántos años tienes? ")
print(type(edad))   # <class 'str'>  — aunque el usuario escriba 25
```

Para trabajar con números, debes **convertir** el resultado:

```python
edad = int(input("¿Cuántos años tienes? "))
altura = float(input("¿Cuál es tu altura en metros? "))

print("En 10 años tendrás", edad + 10, "años")
```

---

## 3. Flujo típico de un programa interactivo

```python
# 1. Pedir datos
nombre = input("Nombre: ")
precio = float(input("Precio del producto: "))
cantidad = int(input("Cantidad: "))

# 2. Procesar
total = precio * cantidad
iva = total * 0.19
total_con_iva = total + iva

# 3. Mostrar resultados
print("---------- Boleta ----------")
print("Cliente:", nombre)
print("Subtotal: $", total)
print("IVA (19%): $", round(iva, 2))
print("Total: $", round(total_con_iva, 2))
print("----------------------------")
```

---

## 4. Leer múltiples valores en una línea

```python
# El usuario escribe: 10 20 30
valores = input("Ingresa tres números separados por espacio: ")
a, b, c = valores.split()

print("Suma:", int(a) + int(b) + int(c))
```

---

## 5. Errores comunes

### Olvidar convertir el tipo
```python
numero = input("Ingresa un número: ")
resultado = numero + 10   # TypeError: no puedes sumar str con int
```
**Solución:** `numero = int(input("Ingresa un número: "))`

### No validar la entrada (por ahora simplificado)
```python
# Si el usuario escribe "hola" cuando esperas un número:
edad = int(input("Edad: "))   # ValueError
# En la sección de Excepciones aprenderás a manejarlo
```

---

## Ejemplo integrador

```python
print("=== Calculadora de propina ===")
print()

total_cuenta = float(input("Total de la cuenta ($): "))
porcentaje = float(input("Porcentaje de propina (ej: 10): "))

propina = total_cuenta * (porcentaje / 100)
total_final = total_cuenta + propina

print()
print("Cuenta original: $", round(total_cuenta, 2))
print("Propina (" + str(porcentaje) + "%): $", round(propina, 2))
print("Total a pagar:   $", round(total_final, 2))
```

---

## Ejercicio propuesto

Crea un programa que pida al usuario su nombre, año de nacimiento y ciudad. Luego calcula su edad aproximada (año actual - nacimiento) y muestra un resumen con todos los datos.

---

## Siguiente carpeta

➡️ [`04_Operadores_Aritmeticos`](../04_Operadores_Aritmeticos/README.md)