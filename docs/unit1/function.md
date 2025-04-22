# Funciones en Python

<img src="../images/function.png" alt="Banner del Curso" width="800" >


## Introducción

Las funciones son bloques fundamentales de construcción en Python. Permiten encapsular lógica reutilizable, estructurar el código y mejorar su claridad. Desde simples scripts hasta aplicaciones complejas, el uso efectivo de funciones marca la diferencia entre código improvisado y software profesional.

En este capítulo exploraremos la definición, uso y buenas prácticas en torno a las funciones en Python, incluyendo funciones anónimas, de orden superior y mecanismos avanzados como `*args` y `**kwargs`.

---

## ¿Qué es una función?

Una **función** es un bloque de código que realiza una tarea específica. Se puede invocar (llamar) múltiples veces y permite pasarle entradas (argumentos) y obtener una salida (retorno).

### Ejemplo básico

```python
def saludar(nombre):
    return f"Hola, {nombre}!"
```

```python
print(saludar("Francisco"))  # Hola, Francisco!
```

---

## Sintaxis y estructura de funciones

```python
def nombre_funcion(param1, param2=valor_por_defecto):
    """Docstring: breve descripción de lo que hace la función."""
    # Cuerpo de la función
    return resultado
```

### Elementos clave:

- `def`: palabra clave para definir una función.
- `nombre_funcion`: identificador que usaremos para llamarla.
- `parametros`: entradas que puede recibir.
- `return`: valor que devuelve (puede ser omitido).
- `docstring`: comentario opcional que documenta la función.

---

## Tipos de funciones en Python

### 1. Funciones definidas por el usuario

Estas son funciones comunes que definimos con `def`.

```python
def sumar(a, b):
    return a + b
```

---

### 2. Funciones anónimas (lambda)

Permiten definir funciones pequeñas en una sola línea, sin nombre.

```python
cuadrado = lambda x: x ** 2
print(cuadrado(4))  # 16
```

> ⚠️ Las funciones `lambda` son útiles para casos simples. No reemplazan a las funciones completas con `def`.

---

### 3. Funciones de orden superior

Son funciones que aceptan otras funciones como argumentos o devuelven funciones.

```python
def aplicar(funcion, lista):
    return [funcion(x) for x in lista]

resultado = aplicar(lambda x: x * 2, [1, 2, 3])
print(resultado)  # [2, 4, 6]
```

---

## Parámetros y retorno

Python ofrece mucha flexibilidad para manejar argumentos:

| Tipo de parámetro   | Ejemplo                          | Descripción                                  |
|---------------------|----------------------------------|----------------------------------------------|
| Posicional          | `def f(x, y)`                    | Se pasan en orden                            |
| Nombrado            | `f(x=10, y=20)`                  | Se pasan con nombre explícito                |
| Por defecto         | `def f(x=5)`                     | Si no se pasa, se usa el valor por defecto   |
| `*args`             | `def f(*args)`                   | Recibe múltiples argumentos posicionales     |
| `**kwargs`          | `def f(**kwargs)`                | Recibe múltiples argumentos nombrados        |

### Ejemplo combinado

```python
def resumen(nombre, *actividades, **extras):
    print(f"Nombre: {nombre}")
    print("Actividades:", actividades)
    print("Extras:", extras)

resumen("Francisco", "Python", "Git", nivel="intermedio", pais="Chile")
```

---

## Tipado de funciones (Type Hints)

Las anotaciones de tipo ayudan a documentar el comportamiento esperado de una función:

```python
def multiplicar(x: int, y: int) -> int:
    return x * y
```

Estas anotaciones **no son obligatorias**, pero mejoran la claridad y permiten el uso de herramientas como `mypy`.

---

## Buenas prácticas

✅ Nombra tus funciones con verbos descriptivos (`obtener_datos`, `calcular_total`)  
✅ Mantén las funciones **pequeñas y enfocadas** en una sola tarea  
✅ Usa **docstrings** claros  
✅ Añade anotaciones de tipo cuando sea posible  
✅ Prefiere `def` sobre `lambda` si la lógica es compleja

---

## Errores comunes

❌ No retornar nada cuando se espera un valor  
❌ Tener demasiados efectos secundarios dentro de una función  
❌ Usar variables globales sin necesidad  
❌ Usar `lambda` para lógica compleja (dificulta la lectura)

---

## Referencias útiles

- 📘 [Funciones – Tutorial oficial de Python](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)
- 🧰 [PEP 8 – Nombres de funciones](https://peps.python.org/pep-0008/#function-and-variable-names)
- 🧪 [PEP 484 – Type Hints](https://peps.python.org/pep-0484/)

---

## Conclusión

Las funciones son esenciales para crear código modular y reutilizable. Usarlas correctamente mejora la organización del programa y facilita su mantenimiento. Python ofrece muchas herramientas para definir funciones de forma clara, concisa y expresiva, desde funciones simples hasta patrones más avanzados como funciones de orden superior o tipado estático.

Dominar este componente es clave en la transición de escribir scripts improvisados a desarrollar software profesional.
