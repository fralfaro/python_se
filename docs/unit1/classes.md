# Clases en Python

<img src="../images/class.svg" alt="Banner del Curso" width="800" >


## Introducción

La programación orientada a objetos (OOP) es un paradigma ampliamente utilizado para modelar sistemas complejos y estructurar el código en componentes reutilizables. En Python, las **clases** permiten encapsular datos y comportamientos relacionados en una sola entidad: el objeto.

Este capítulo te introducirá a las clases en Python, cubriendo desde los conceptos fundamentales hasta prácticas avanzadas como herencia, métodos especiales y anotaciones. Verás cómo estructurar tu código de forma más mantenible, reutilizable y expresiva mediante clases.

---

## ¿Qué es una clase?

Una **clase** es una plantilla para crear objetos. Define atributos (datos) y métodos (funciones) que describen el comportamiento de los objetos.

### Ejemplo simple

```python
class Persona:
    def __init__(self, nombre):
        self.nombre = nombre

    def saludar(self):
        return f"Hola, soy {self.nombre}"

p = Persona("Francisco")
print(p.saludar())  # Hola, soy Francisco
```

---

## Estructura básica de una clase

```python
class NombreClase:
    def __init__(self, parametros):
        self.atributo = valor

    def metodo(self):
        # comportamiento
        pass
```

### Componentes clave

- `class`: palabra clave para definir una clase.
- `__init__`: método constructor, se ejecuta al crear un nuevo objeto.
- `self`: referencia al objeto actual.
- Métodos: funciones definidas dentro de una clase que operan sobre sus atributos.

---

## Atributos: de instancia vs de clase

### Atributos de instancia

Se definen en el constructor (`__init__`) y son únicos para cada objeto.

```python
class Vehiculo:
    def __init__(self, color):
        self.color = color
```

### Atributos de clase

Son compartidos por todas las instancias.

```python
class Vehiculo:
    ruedas = 4  # atributo de clase

    def __init__(self, color):
        self.color = color
```

---

## Métodos especiales

Python permite personalizar el comportamiento de los objetos usando métodos especiales (`__dunder__`).

| Método        | Función                                     |
|---------------|---------------------------------------------|
| `__init__`    | Constructor del objeto                      |
| `__str__`     | Representación amigable (`str(obj)`)        |
| `__repr__`    | Representación técnica (`repr(obj)`)        |
| `__eq__`      | Comparación de igualdad (`==`)              |

```python
class Producto:
    def __init__(self, nombre, precio):
        self.nombre = nombre
        self.precio = precio

    def __str__(self):
        return f"{self.nombre} - ${self.precio}"
```

---

## Métodos de clase y estáticos

### `@classmethod`

Accede a la clase en lugar de a la instancia.

```python
class Usuario:
    usuarios = []

    def __init__(self, nombre):
        self.nombre = nombre
        Usuario.usuarios.append(self)

    @classmethod
    def total_usuarios(cls):
        return len(cls.usuarios)
```

### `@staticmethod`

No accede ni a la clase ni a la instancia. Es como una función normal dentro del namespace de la clase.

```python
class Calculadora:
    @staticmethod
    def sumar(x, y):
        return x + y
```

---

## Herencia y polimorfismo

Python permite que una clase herede atributos y métodos de otra, lo que promueve la reutilización y extensión del código.

```python
class Animal:
    def hablar(self):
        return "Hace un sonido"

class Perro(Animal):
    def hablar(self):
        return "Ladra"

p = Perro()
print(p.hablar())  # Ladra
```

> 🧠 Esto es polimorfismo: el mismo método (`hablar`) se comporta diferente según la clase.

---

## Buenas prácticas

✅ Usa nombres en `PascalCase` para clases  
✅ Define solo lo necesario en `__init__`  
✅ Añade `__str__` para una representación legible  
✅ Prefiere `@classmethod` cuando necesites modificar atributos de clase  
✅ Aplica herencia solo si hay una verdadera relación jerárquica

---

## Errores comunes

❌ Olvidar el uso de `self` en métodos de instancia  
❌ Redefinir atributos de clase desde instancias sin intención  
❌ Crear jerarquías de herencia profundas e innecesarias  
❌ Sobrecargar `__init__` con demasiada lógica

---

## Recursos útiles

- 📘 [Clases – Tutorial oficial de Python](https://docs.python.org/3/tutorial/classes.html)
- 🧰 [PEP 8 – Nombres de clases y métodos](https://peps.python.org/pep-0008/#class-names)
- 📚 *Fluent Python* – Capítulos sobre clases y objetos avanzados

---

## Conclusión

Las clases son una herramienta poderosa en Python para modelar estructuras complejas del mundo real. Entender su sintaxis y principios te permitirá construir software más organizado, extensible y orientado a objetos.

Dominar las clases es un paso fundamental hacia el desarrollo de aplicaciones robustas y bien estructuradas en Python.
