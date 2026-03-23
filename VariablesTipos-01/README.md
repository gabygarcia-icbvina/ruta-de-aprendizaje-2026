# 02 · Variables y Tipos de Datos

> **Objetivo:** Guardar información en variables y entender los tipos de datos fundamentales de Python.

---

## ¿Qué aprenderás aquí?

- Qué es una variable y cómo crearla
- Los tipos de datos básicos: `int`, `float`, `str`, `bool`
- Cómo saber el tipo de una variable con `type()`
- Conversión entre tipos (casting)
- Reglas para nombrar variables

---

## 1. ¿Qué es una variable?

Una variable es un **contenedor con nombre** donde guardas un dato para usarlo después.

```python
nombre = "Carlos"
edad = 28
altura = 1.75
es_estudiante = True
```

No necesitas declarar el tipo — Python lo detecta solo.

---

## 2. Tipos de datos básicos

### `int` — Números enteros
```python
edad = 25
año = 2025
temperatura = -10
cantidad = 0
```

### `float` — Números con decimales
```python
precio = 19.99
pi = 3.14159
peso = 72.5
descuento = 0.15
```

### `str` — Texto (strings)
```python
nombre = "Ana"
apellido = 'González'          # Comillas simples también funcionan
mensaje = "Hola, ¿cómo estás?"
vacio = ""                     # String vacío (válido)
```

### `bool` — Verdadero o Falso
```python
activo = True
pagado = False
mayor_de_edad = True
```

> `True` y `False` siempre van con la primera letra en mayúscula.

---

## 3. Verificar el tipo con `type()`

```python
x = 42
print(type(x))       # <class 'int'>

y = 3.14
print(type(y))       # <class 'float'>

z = "hola"
print(type(z))       # <class 'str'>

w = True
print(type(w))       # <class 'bool'>
```

---

## 4. Conversión de tipos (casting)

```python
# Texto a número
edad_texto = "25"
edad_numero = int(edad_texto)   # 25 (como entero)
print(edad_numero + 1)          # 26

# Número a texto
precio = 9.99
precio_texto = str(precio)      # "9.99"
print("El precio es: " + precio_texto)

# Entero a float y viceversa
entero = int(3.9)    # 3  (trunca, NO redondea)
decimal = float(5)   # 5.0
```

### Casting inválido genera error
```python
int("hola")   # ValueError: convierte solo si el texto es un número
```

---

## 5. Reglas para nombrar variables

| ✅ Válido | ❌ Inválido | Motivo |
|-----------|-------------|--------|
| `nombre` | `1nombre` | No puede empezar con número |
| `mi_variable` | `mi variable` | No puede tener espacios |
| `_privada` | `class` | No puede ser una palabra reservada |
| `precioTotal` | `precio-total` | No puede usar guión |
| `PI` | `2PI` | No puede empezar con número |

### Convención en Python: snake_case
```python
# ✅ Recomendado (snake_case)
nombre_completo = "Ana García"
precio_total = 150.0

# ❌ Evitar (camelCase se usa en otros lenguajes)
nombreCompleto = "Ana García"
```

---

## 6. Asignación múltiple

```python
# Asignar el mismo valor a varias variables
a = b = c = 0

# Asignar distintos valores en una línea
x, y, z = 1, 2, 3

# Intercambiar valores (¡sin variable temporal!)
a, b = 10, 20
a, b = b, a
print(a, b)  # 20 10
```

---

## 7. Variables especiales

```python
# None: ausencia de valor (similar a null en otros lenguajes)
resultado = None
print(type(resultado))   # <class 'NoneType'>
```

---

## Ejemplos integradores

```python
nombre = "Lucía"
edad = 22
altura = 1.68
es_mayor = edad >= 18

print("Nombre:", nombre)
print("Edad:", edad)
print("Altura:", altura)
print("¿Mayor de edad?", es_mayor)
print("Tipo de 'nombre':", type(nombre))
```

**Salida:**
```
Nombre: Lucía
Edad: 22
Altura: 1.68
¿Mayor de edad? True
Tipo de 'nombre': <class 'str'>
```

---

## Ejercicio propuesto

Crea variables para describir a una persona: nombre, apellido, edad, peso, altura y si está activo. Luego imprime cada una con su tipo de dato.

---

## Siguiente carpeta

➡️ [`03_Input_y_Output`](../03_Input_y_Output/README.md)