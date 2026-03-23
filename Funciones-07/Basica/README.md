# 08 · Funciones Básicas

> **Objetivo:** Organizar tu código en bloques reutilizables usando funciones.

---

## ¿Qué aprenderás aquí?

- Definir y llamar funciones con `def`
- Por qué usar funciones
- Scope: variables locales vs globales
- Documentar funciones con docstrings
- Funciones sin parámetros y sin retorno

---

## 1. ¿Qué es una función?

Una función es un **bloque de código con nombre** que puedes ejecutar cuando quieras, las veces que necesites.

```python
# Sin función (código repetido)
print("==========")
print("Bienvenido")
print("==========")

print("==========")
print("Hasta luego")
print("==========")

# Con función (código reutilizable)
def separador():
    print("==========")

separador()
print("Bienvenido")
separador()

separador()
print("Hasta luego")
separador()
```

---

## 2. Definir una función

```python
def nombre_de_la_funcion():
    # cuerpo de la función (indentado)
    instruccion_1
    instruccion_2
```

### Llamar (ejecutar) una función

```python
def saludar():
    print("¡Hola!")
    print("Bienvenido al programa.")

# Llamar la función
saludar()
saludar()   # Puedes llamarla cuantas veces quieras
```

> Definir una función **no la ejecuta**. Solo la llamas cuando escribes `nombre()`.

---

## 3. Funciones con parámetros básicos

```python
def saludar(nombre):
    print("Hola,", nombre)

saludar("Ana")     # Hola, Ana
saludar("Carlos")  # Hola, Carlos
```

### Múltiples parámetros

```python
def presentar(nombre, edad):
    print(nombre, "tiene", edad, "años")

presentar("Lucía", 25)
presentar("Pedro", 30)
```

---

## 4. Scope: variables locales y globales

Las variables **locales** solo existen dentro de la función:

```python
def mi_funcion():
    x = 10   # Variable local
    print(x)

mi_funcion()
# print(x)   # NameError: x no existe fuera de la función
```

Las variables **globales** existen en todo el programa:

```python
mensaje = "Hola desde fuera"   # Variable global

def mostrar():
    print(mensaje)   # Puede leer la variable global

mostrar()   # Hola desde fuera
```

### Modificar una variable global (evitar cuando sea posible)

```python
contador = 0

def incrementar():
    global contador   # Declara que usará la global
    contador += 1

incrementar()
incrementar()
print(contador)   # 2
```

> Usar `global` hace el código difícil de seguir. Prefiere siempre retornar valores (lo verás en la siguiente carpeta).

---

## 5. Docstrings — documentar funciones

```python
def calcular_area(base, altura):
    """
    Calcula el área de un rectángulo.
    
    base: ancho del rectángulo (número)
    altura: alto del rectángulo (número)
    """
    area = base * altura
    print("El área es:", area)

# Ver la documentación
help(calcular_area)
print(calcular_area.__doc__)
```

---

## 6. Buenas prácticas al nombrar funciones

```python
# ✅ Buenas prácticas
def calcular_descuento():    # verbo + sustantivo, snake_case
def mostrar_menu():
def validar_edad():
def obtener_precio():

# ❌ Evitar
def cd():                    # nombre críptico
def MiF():                   # no snake_case
def funcion1():              # sin contexto
```

---

## Ejemplo integrador

```python
def mostrar_bienvenida():
    """Muestra el encabezado del programa."""
    print("=" * 30)
    print("   SISTEMA DE REGISTRO")
    print("=" * 30)

def mostrar_despedida():
    """Muestra el mensaje de cierre."""
    print()
    print("Gracias por usar el sistema. ¡Hasta pronto!")

def pedir_nombre():
    """Solicita y muestra el nombre del usuario."""
    nombre = input("¿Cuál es tu nombre? ")
    print("Nombre registrado:", nombre)

mostrar_bienvenida()
pedir_nombre()
mostrar_despedida()
```

---

## Ejercicio propuesto

Crea tres funciones:
1. `mostrar_titulo()` — imprime un título con decoración
2. `contar_hasta(n)` — imprime los números del 1 al n
3. `despedida()` — imprime un mensaje de cierre

Llama las tres funciones en orden.

---

## Siguiente carpeta

➡️ [`09_Funciones_Intermedias`](../09_Funciones_Intermedias/README.md)