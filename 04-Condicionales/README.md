# 05 · Condicionales

> **Objetivo:** Hacer que tu programa tome decisiones según las condiciones que definas.

---

## ¿Qué aprenderás aquí?

- Estructura `if / elif / else`
- Operadores de comparación
- Condicionales anidados
- Operador ternario (condicional en una línea)
- Patrones comunes de decisión

---

## 1. Estructura básica: `if / else`

```python
edad = 20

if edad >= 18:
    print("Eres mayor de edad")
else:
    print("Eres menor de edad")
```

> **Importante:** La **indentación** (4 espacios) define qué código pertenece al bloque. Python es estricto con esto.

---

## 2. Múltiples condiciones: `elif`

```python
nota = 75

if nota >= 90:
    print("Sobresaliente")
elif nota >= 70:
    print("Aprobado")
elif nota >= 50:
    print("Suficiente")
else:
    print("Reprobado")
```

`elif` es la abreviación de "else if". Python evalúa de arriba a abajo y ejecuta el **primer bloque verdadero**.

---

## 3. Operadores de comparación

| Operador | Significado | Ejemplo | Resultado |
|----------|-------------|---------|-----------|
| `==` | Igual a | `5 == 5` | `True` |
| `!=` | Distinto de | `5 != 3` | `True` |
| `>` | Mayor que | `7 > 3` | `True` |
| `<` | Menor que | `2 < 8` | `True` |
| `>=` | Mayor o igual | `5 >= 5` | `True` |
| `<=` | Menor o igual | `4 <= 3` | `False` |

```python
# ⚠️ No confundir = (asignación) con == (comparación)
x = 10         # Asigna 10 a x
print(x == 10) # Compara: True
print(x == 5)  # Compara: False
```

---

## 4. Condicionales anidados

```python
temperatura = 28
lluvia = False

if temperatura > 25:
    if not lluvia:
        print("Buen día para salir al parque")
    else:
        print("Hace calor pero está lloviendo")
else:
    print("Hace fresco hoy")
```

> Evita anidar demasiado — más de 2 niveles dificulta la lectura. Considera usar `and`/`or` en su lugar.

---

## 5. Combinar condiciones con `and`, `or`, `not`

```python
edad = 22
tiene_licencia = True

# and: ambas deben ser verdaderas
if edad >= 18 and tiene_licencia:
    print("Puedes conducir")

# or: basta con que una sea verdadera
dia = "sábado"
if dia == "sábado" or dia == "domingo":
    print("Es fin de semana")

# not: invierte el resultado
esta_lloviendo = False
if not esta_lloviendo:
    print("No llueve, puedes salir")
```

---

## 6. Operador ternario

Una forma compacta de escribir `if/else` en una sola línea:

```python
# Forma larga
if edad >= 18:
    estado = "mayor"
else:
    estado = "menor"

# Forma corta (ternario)
estado = "mayor" if edad >= 18 else "menor"
print(estado)
```

Útil para asignaciones simples. No lo uses si la condición es compleja.

---

## 7. Comparar strings

```python
color = input("¿Cuál es tu color favorito? ").lower()

if color == "azul":
    print("El azul es tranquilidad")
elif color == "rojo":
    print("El rojo es energía")
else:
    print("Color interesante:", color)
```

> `.lower()` convierte a minúsculas para evitar problemas con mayúsculas del usuario.

---

## 8. Verificar si un valor está en un rango

```python
numero = 15

# Forma pythónica
if 10 <= numero <= 20:
    print("El número está entre 10 y 20")

# Equivalente con and
if numero >= 10 and numero <= 20:
    print("El número está entre 10 y 20")
```

---

## Ejemplo integrador

```python
print("=== Clasificador de IMC ===")
peso = float(input("Peso (kg): "))
altura = float(input("Altura (m): "))

imc = peso / altura ** 2
imc = round(imc, 1)

print("Tu IMC es:", imc)

if imc < 18.5:
    categoria = "Bajo peso"
elif imc < 25:
    categoria = "Normal"
elif imc < 30:
    categoria = "Sobrepeso"
else:
    categoria = "Obesidad"

print("Categoría:", categoria)
```

---

## Ejercicio propuesto

Crea un programa que pida una temperatura en Celsius y diga:
- Menor a 0°: "Bajo cero, posible nieve"
- 0–15°: "Frío"
- 16–25°: "Agradable"
- 26–35°: "Caluroso"
- Mayor a 35°: "Calor extremo"

---

## Siguiente carpeta

➡️ [`06_Bucles`](../06_Bucles/README.md)