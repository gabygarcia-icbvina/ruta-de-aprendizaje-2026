# 14 · F-Strings

> **Objetivo:** Crear strings dinámicos de forma clara y eficiente con f-strings.

---

## ¿Qué aprenderás aquí?

- Qué es un f-string y por qué usarlo
- Insertar variables y expresiones
- Formatear números: decimales, ancho, relleno
- Formatear fechas
- Comparación con formas anteriores

---

## 1. ¿Qué es un f-string?

Un f-string es un string prefijado con `f` que permite insertar variables y expresiones directamente dentro del texto, entre llaves `{}`.

```python
nombre = "Ana"
edad = 28

# F-string (Python 3.6+) ✅
mensaje = f"Hola, {nombre}. Tienes {edad} años."

# Formas anteriores (más engorrosas)
mensaje = "Hola, " + nombre + ". Tienes " + str(edad) + " años."   # ❌
mensaje = "Hola, {}. Tienes {} años.".format(nombre, edad)         # Aceptable
```

---

## 2. Insertar variables y expresiones

```python
precio = 150.0
cantidad = 3

# Variables
print(f"Precio: ${precio}")

# Expresiones matemáticas
print(f"Total: ${precio * cantidad}")

# Llamadas a funciones
nombre = "carlos"
print(f"Nombre: {nombre.capitalize()}")

# Condicionales (ternario)
edad = 20
print(f"Estado: {'mayor' if edad >= 18 else 'menor'} de edad")

# Operaciones
numeros = [3, 1, 4, 1, 5]
print(f"Suma: {sum(numeros)}, Máx: {max(numeros)}")
```

---

## 3. Formatear números

### Decimales
```python
pi = 3.14159265

print(f"{pi:.2f}")    # 3.14   (2 decimales)
print(f"{pi:.4f}")    # 3.1416 (4 decimales)
print(f"{pi:.0f}")    # 3      (sin decimales)
```

### Separadores de miles
```python
poblacion = 8000000
print(f"{poblacion:,}")    # 8,000,000
print(f"{poblacion:_.0f}") # 8_000_000 (guion bajo)
```

### Porcentajes
```python
aprobados = 0.75
print(f"{aprobados:.1%}")   # 75.0%
print(f"{aprobados:.0%}")   # 75%
```

### Notación científica
```python
numero = 0.000123
print(f"{numero:.2e}")   # 1.23e-04
```

---

## 4. Alineación y relleno

```python
# Ancho mínimo
print(f"{'Nombre':<15} {'Edad':>5}")   # Alinear a la izquierda / derecha
print(f"{'Ana':<15} {25:>5}")
print(f"{'Carlos':<15} {30:>5}")

# Centrar
print(f"{'Título':^30}")       # Centrado en 30 caracteres

# Rellenar con caracteres
print(f"{'='*30}")
print(f"{'TOTAL':=^30}")       # TOTAL con = alrededor
print(f"{42:0>5}")             # 00042  (relleno con ceros)
print(f"{42:*<8}")             # 42*****
```

---

## 5. Formatear enteros

```python
n = 255
print(f"{n:b}")    # 11111111 (binario)
print(f"{n:o}")    # 377      (octal)
print(f"{n:x}")    # ff       (hexadecimal minúscula)
print(f"{n:X}")    # FF       (hexadecimal mayúscula)
print(f"{n:08b}")  # 11111111 (binario con 8 dígitos)
```

---

## 6. F-strings multilínea

```python
nombre = "Ana"
total = 2500.50
descuento = 500.0

factura = f"""
========== FACTURA ==========
Cliente:   {nombre}
Subtotal:  ${total:,.2f}
Descuento: ${descuento:,.2f}
Total:     ${total - descuento:,.2f}
=============================
"""
print(factura)
```

---

## 7. Depuración con `=` (Python 3.8+)

```python
x = 42
y = 3.14
nombre = "test"

print(f"{x=}")        # x=42
print(f"{y=}")        # y=3.14
print(f"{nombre=}")   # nombre='test'
print(f"{x * 2 =}")   # x * 2 =84
```

Muy útil para debugging rápido.

---

## 8. Resumen de formatos

| Formato | Descripción | Ejemplo | Resultado |
|---------|-------------|---------|-----------|
| `:.2f` | 2 decimales | `f"{3.14159:.2f}"` | `3.14` |
| `:,` | Miles con coma | `f"{1000000:,}"` | `1,000,000` |
| `:.1%` | Porcentaje | `f"{0.75:.1%}"` | `75.0%` |
| `:<10` | Alinear izq, ancho 10 | `f"{'hi':<10}"` | `hi        ` |
| `:>10` | Alinear der, ancho 10 | `f"{42:>10}"` | `        42` |
| `:^10` | Centrar, ancho 10 | `f"{'hi':^10}"` | `    hi    ` |
| `:05d` | Rellenar con ceros | `f"{7:05d}"` | `00007` |

---

## Ejemplo integrador

```python
productos = [
    ("Laptop", 999.99, 5),
    ("Mouse", 29.50, 20),
    ("Teclado", 79.00, 12),
]

print(f"{'Producto':<15} {'Precio':>10} {'Stock':>7} {'Total':>12}")
print("-" * 48)

gran_total = 0
for nombre, precio, stock in productos:
    subtotal = precio * stock
    gran_total += subtotal
    print(f"{nombre:<15} ${precio:>9,.2f} {stock:>7} ${subtotal:>11,.2f}")

print("-" * 48)
print(f"{'TOTAL':<15} {'':>10} {'':>7} ${gran_total:>11,.2f}")
```

---

## Ejercicio propuesto

Crea una función `generar_recibo(cliente, productos)` que reciba el nombre del cliente y una lista de tuplas (nombre, precio, cantidad) y genere un recibo formateado y alineado con f-strings.

---

## Siguiente carpeta

➡️ [`15_Sets`](../15_Sets/README.md)