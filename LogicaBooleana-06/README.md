# 07 · Lógica Booleana

> **Objetivo:** Entender cómo Python evalúa verdad y falsedad, y combinar condiciones de forma eficiente.

---

## ¿Qué aprenderás aquí?

- Tipo `bool` y valores `True` / `False`
- Operadores lógicos: `and`, `or`, `not`
- Tablas de verdad
- Valores "truthy" y "falsy"
- Cortocircuito lógico
- Operador `in` e `is`

---

## 1. El tipo `bool`

```python
es_mayor = True
tiene_licencia = False

print(type(es_mayor))    # <class 'bool'>
print(int(True))         # 1
print(int(False))        # 0
```

Las comparaciones siempre devuelven un `bool`:

```python
print(5 > 3)    # True
print(10 == 9)  # False
print("a" != "b")  # True
```

---

## 2. Operadores lógicos

### `and` — Ambas deben ser verdaderas

```python
True and True    # True
True and False   # False
False and True   # False
False and False  # False
```

```python
edad = 20
tiene_dni = True

if edad >= 18 and tiene_dni:
    print("Puede entrar")
```

### `or` — Al menos una debe ser verdadera

```python
True or True    # True
True or False   # True
False or True   # True
False or False  # False
```

```python
dia = "domingo"

if dia == "sábado" or dia == "domingo":
    print("Es fin de semana")
```

### `not` — Invierte el valor

```python
not True    # False
not False   # True
```

```python
logueado = False

if not logueado:
    print("Por favor inicia sesión")
```

---

## 3. Tablas de verdad completas

| `a` | `b` | `a and b` | `a or b` | `not a` |
|-----|-----|-----------|----------|---------|
| True | True | True | True | False |
| True | False | False | True | False |
| False | True | False | True | True |
| False | False | False | False | True |

---

## 4. Valores "truthy" y "falsy"

Python considera algunos valores como `False` aunque no sean el booleano `False` exacto:

### Falsy (se comportan como False)
```python
False
0
0.0
""          # string vacío
[]          # lista vacía
{}          # diccionario vacío
None
```

### Truthy (todo lo demás)
```python
True
1, -1, 42   # cualquier número distinto de 0
"hola"      # string no vacío
[1, 2]      # lista con elementos
```

### Uso práctico

```python
nombre = input("Tu nombre: ")

if nombre:   # True si nombre no está vacío
    print("Hola,", nombre)
else:
    print("No ingresaste ningún nombre")
```

```python
lista = []

if not lista:   # True si la lista está vacía
    print("La lista está vacía")
```

---

## 5. Cortocircuito lógico

Python es "perezoso": deja de evaluar en cuanto conoce el resultado.

```python
# Con and: si el primero es False, no evalúa el segundo
False and print("Esto nunca se imprime")

# Con or: si el primero es True, no evalúa el segundo
True or print("Esto tampoco se imprime")
```

### Aplicación práctica: valor por defecto

```python
nombre = input("Nombre (o Enter para omitir): ")
nombre = nombre or "Invitado"   # Si nombre está vacío, usa "Invitado"
print("Hola,", nombre)
```

---

## 6. Operador `in`

Verifica si un elemento está dentro de una secuencia:

```python
frutas = ["manzana", "pera", "uva"]

print("pera" in frutas)         # True
print("naranja" in frutas)      # False
print("naranja" not in frutas)  # True

# Con strings
print("pyt" in "python")        # True
print("z" in "python")          # False
```

---

## 7. Operador `is` vs `==`

```python
# == compara valores
a = [1, 2, 3]
b = [1, 2, 3]
print(a == b)   # True  (mismo contenido)
print(a is b)   # False (son objetos distintos en memoria)

# is se usa principalmente para comparar con None
resultado = None
if resultado is None:
    print("No hay resultado todavía")
```

---

## Ejemplo integrador

```python
print("=== Validador de contraseña ===")
password = input("Ingresa una contraseña: ")

tiene_longitud = len(password) >= 8
tiene_numero = any(c.isdigit() for c in password)
tiene_mayuscula = any(c.isupper() for c in password)

print("¿8+ caracteres?", tiene_longitud)
print("¿Tiene número?", tiene_numero)
print("¿Tiene mayúscula?", tiene_mayuscula)

if tiene_longitud and tiene_numero and tiene_mayuscula:
    print("✓ Contraseña fuerte")
elif tiene_longitud and (tiene_numero or tiene_mayuscula):
    print("~ Contraseña aceptable")
else:
    print("✗ Contraseña débil")
```

---

## Ejercicio propuesto

Crea un programa que pida año de nacimiento y determine si la persona puede votar (18+) Y si está en rango de jubilación (65+). Muestra un mensaje combinando ambas condiciones.

---

## Siguiente carpeta

➡️ [`08_Funciones_Basicas`](../08_Funciones_Basicas/README.md)