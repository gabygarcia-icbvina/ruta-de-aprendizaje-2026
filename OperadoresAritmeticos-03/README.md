# 04 · Operadores Aritméticos

> **Objetivo:** Realizar cálculos matemáticos en Python usando todos los operadores disponibles.

---

## ¿Qué aprenderás aquí?

- Operadores aritméticos básicos y avanzados
- División entera y módulo
- Potenciación
- Operadores de asignación compuesta
- Precedencia (orden de operaciones)
- La función `round()` y el módulo `math`

---

## 1. Operadores básicos

| Operador | Nombre | Ejemplo | Resultado |
|----------|--------|---------|-----------|
| `+` | Suma | `5 + 3` | `8` |
| `-` | Resta | `10 - 4` | `6` |
| `*` | Multiplicación | `3 * 7` | `21` |
| `/` | División | `10 / 3` | `3.3333...` |
| `//` | División entera | `10 // 3` | `3` |
| `%` | Módulo (resto) | `10 % 3` | `1` |
| `**` | Potencia | `2 ** 8` | `256` |

```python
a = 17
b = 5

print(a + b)    # 22
print(a - b)    # 12
print(a * b)    # 85
print(a / b)    # 3.4      (siempre float)
print(a // b)   # 3        (descarta decimales)
print(a % b)    # 2        (resto de 17 / 5)
print(a ** b)   # 1419857  (17 elevado a 5)
```

---

## 2. División entera `//` y módulo `%`

Dos operadores muy útiles que trabajan juntos:

```python
# Dividir 100 caramelos entre 7 personas
total = 100
personas = 7

por_persona = total // personas   # 14 (enteros completos)
sobrantes = total % personas      # 2  (los que sobran)

print("Cada persona recibe:", por_persona)
print("Sobran:", sobrantes)
```

### Usos comunes del módulo `%`

```python
# Saber si un número es par o impar
numero = 15
if numero % 2 == 0:
    print("Par")
else:
    print("Impar")   # → Impar

# Saber si es divisible por otro número
print(100 % 10 == 0)   # True (100 es divisible por 10)
```

---

## 3. Potencia `**`

```python
print(2 ** 10)    # 1024
print(9 ** 0.5)   # 3.0   (raíz cuadrada)
print(27 ** (1/3))# 3.0   (raíz cúbica)
```

---

## 4. Operadores de asignación compuesta

Atajos para actualizar una variable con base en su valor actual:

```python
x = 10

x += 5    # x = x + 5  →  15
x -= 3    # x = x - 3  →  12
x *= 2    # x = x * 2  →  24
x /= 4    # x = x / 4  →   6.0
x //= 2   # x = x // 2 →   3.0
x **= 3   # x = x ** 3 →  27.0
x %= 5    # x = x % 5  →   2.0
```

---

## 5. Precedencia de operadores

Python sigue las mismas reglas que las matemáticas (PEMDAS):

| Prioridad | Operador |
|-----------|----------|
| 1 (mayor) | `**` |
| 2 | `*`, `/`, `//`, `%` |
| 3 (menor) | `+`, `-` |

```python
print(2 + 3 * 4)       # 14  (no 20) — multiplica primero
print((2 + 3) * 4)     # 20  — paréntesis primero
print(2 ** 3 + 1)      # 9   (8 + 1)
print(10 - 4 / 2)      # 8.0 (10 - 2.0)
```

> **Regla:** Cuando dudes, usa paréntesis. Hacen el código más legible.

---

## 6. Redondeo y precisión

```python
resultado = 10 / 3
print(resultado)            # 3.3333333333333335

# Redondear a N decimales
print(round(resultado, 2))  # 3.33
print(round(resultado, 0))  # 3.0
print(round(3.5))           # 4   (redondea al par más cercano en Python 3)
```

---

## 7. Módulo `math` para operaciones avanzadas

```python
import math

print(math.sqrt(144))     # 12.0  (raíz cuadrada)
print(math.pi)            # 3.141592653589793
print(math.ceil(3.2))     # 4     (redondear hacia arriba)
print(math.floor(3.9))    # 3     (redondear hacia abajo)
print(math.abs(-7))       # 7     (valor absoluto — también: abs(-7))
print(math.log(100, 10))  # 2.0   (logaritmo base 10)
```

---

## Ejemplo integrador

```python
radio = float(input("Radio del círculo: "))
import math

area = math.pi * radio ** 2
perimetro = 2 * math.pi * radio

print("Área:", round(area, 2))
print("Perímetro:", round(perimetro, 2))
```

---

## Ejercicio propuesto

Crea una calculadora básica: pide dos números y una operación (`+`, `-`, `*`, `/`). Muestra el resultado con dos decimales. (Pista: usa `input()` para la operación y `if/elif` para elegir qué hacer — los condicionales los verás en la siguiente carpeta.)

---

## Siguiente carpeta

➡️ [`05_Condicionales`](../05_Condicionales/README.md)