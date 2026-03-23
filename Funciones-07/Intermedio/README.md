# 09 · Funciones Intermedias — Parámetros y Return

> **Objetivo:** Crear funciones que reciban datos, los procesen y devuelvan resultados.

---

## ¿Qué aprenderás aquí?

- `return`: devolver valores desde una función
- Parámetros con valor por defecto
- `*args` y `**kwargs` (parámetros variables)
- Múltiples valores de retorno
- Funciones que llaman a otras funciones
- Funciones lambda

---

## 1. `return` — devolver un valor

Sin `return`, una función hace algo pero no entrega nada:

```python
def sumar(a, b):
    resultado = a + b
    return resultado

total = sumar(5, 3)
print(total)         # 8
print(sumar(10, 20)) # 30
```

> Una función sin `return` (o con `return` vacío) devuelve `None`.

```python
def sin_retorno():
    print("Hola")

valor = sin_retorno()
print(valor)   # None
```

---

## 2. Retornar en cualquier punto

`return` detiene la función inmediatamente:

```python
def dividir(a, b):
    if b == 0:
        return None   # Sale de la función aquí
    return a / b

print(dividir(10, 2))  # 5.0
print(dividir(10, 0))  # None
```

---

## 3. Múltiples valores de retorno

Python permite retornar varios valores (como una tupla):

```python
def minmax(lista):
    return min(lista), max(lista)

minimo, maximo = minmax([4, 1, 9, 2, 7])
print("Mínimo:", minimo)   # 1
print("Máximo:", maximo)   # 9
```

---

## 4. Parámetros con valor por defecto

```python
def saludar(nombre, saludo="Hola"):
    print(saludo + ",", nombre)

saludar("Ana")              # Hola, Ana
saludar("Carlos", "Buenas") # Buenas, Carlos
```

> Los parámetros con valor por defecto deben ir **al final**.

```python
# ✅ Correcto
def crear_usuario(nombre, activo=True, rol="usuario"):
    pass

# ❌ Error
def crear_usuario(activo=True, nombre, rol="usuario"):
    pass
```

---

## 5. Argumentos por nombre (keyword arguments)

```python
def presentar(nombre, edad, ciudad):
    print(f"{nombre}, {edad} años, de {ciudad}")

# Sin keyword: orden importa
presentar("Ana", 25, "Santiago")

# Con keyword: orden no importa
presentar(ciudad="Lima", nombre="Luis", edad=30)

# Mezclar posicional + keyword
presentar("María", ciudad="Bogotá", edad=28)
```

---

## 6. `*args` — número variable de argumentos

```python
def sumar_todo(*numeros):
    total = 0
    for n in numeros:
        total += n
    return total

print(sumar_todo(1, 2, 3))          # 6
print(sumar_todo(10, 20, 30, 40))   # 100
print(sumar_todo(5))                 # 5
```

`*args` recibe los argumentos como una **tupla**.

---

## 7. `**kwargs` — argumentos de clave-valor variables

```python
def mostrar_info(**datos):
    for clave, valor in datos.items():
        print(f"{clave}: {valor}")

mostrar_info(nombre="Ana", edad=25, ciudad="Santiago")
# nombre: Ana
# edad: 25
# ciudad: Santiago
```

`**kwargs` recibe los argumentos como un **diccionario**.

---

## 8. Funciones que llaman a otras funciones

```python
def calcular_descuento(precio, porcentaje):
    return precio * (porcentaje / 100)

def precio_final(precio, porcentaje):
    descuento = calcular_descuento(precio, porcentaje)
    return precio - descuento

total = precio_final(100, 20)
print("Precio final:", total)   # 80.0
```

---

## 9. Funciones lambda

Funciones anónimas de una sola expresión:

```python
# Función normal
def doble(x):
    return x * 2

# Equivalente lambda
doble = lambda x: x * 2

print(doble(5))    # 10

# Lambda con múltiples parámetros
sumar = lambda a, b: a + b
print(sumar(3, 7)) # 10
```

Más útiles cuando se pasan como argumento a otras funciones:

```python
numeros = [3, 1, 4, 1, 5, 9, 2, 6]
ordenados = sorted(numeros, key=lambda x: -x)   # Orden descendente
print(ordenados)
```

---

## Ejemplo integrador

```python
def calcular_imc(peso, altura):
    """Calcula el Índice de Masa Corporal."""
    return round(peso / altura ** 2, 1)

def clasificar_imc(imc):
    """Retorna la categoría según el IMC."""
    if imc < 18.5:
        return "Bajo peso"
    elif imc < 25:
        return "Normal"
    elif imc < 30:
        return "Sobrepeso"
    else:
        return "Obesidad"

def evaluar_persona(nombre, peso, altura):
    """Evalúa y muestra el estado de salud de una persona."""
    imc = calcular_imc(peso, altura)
    categoria = clasificar_imc(imc)
    print(f"{nombre}: IMC {imc} → {categoria}")

evaluar_persona("Ana", 60, 1.65)
evaluar_persona("Pedro", 95, 1.70)
```

---

## Ejercicio propuesto

Crea una función `calcular_nota_final(parcial1, parcial2, examen, presentacion=0)` que devuelva el promedio ponderado (30%, 30%, 30%, 10%) y una segunda función `aprobo(nota)` que retorne `True` si la nota es >= 60.

---

## Siguiente carpeta

➡️ [`10_Listas`](../10_Listas/README.md)