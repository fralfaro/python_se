# Paradigmas de programación

<img src="../images/paradigms.svg" alt="Banner del Curso" width="500" >


## Introducción

En el desarrollo de software, existen múltiples formas de organizar y estructurar el código. Estas formas se conocen como **paradigmas de programación**, y cada uno ofrece una manera distinta de pensar y resolver problemas. Python es un lenguaje multiparadigma, lo que significa que admite varios enfoques, permitiéndonos elegir la mejor estrategia según el contexto del proyecto.

Comprender los distintos paradigmas es fundamental para escribir código más expresivo, modular y mantenible. Este capítulo presenta los principales paradigmas compatibles con Python, sus características distintivas y cómo implementarlos de forma efectiva.

---

## ¿Qué es un paradigma de programación?

Un **paradigma de programación** es un modelo o estilo de programación que define cómo se estructuran y ejecutan las instrucciones en un lenguaje. Influye en cómo pensamos los problemas, diseñamos las soluciones y escribimos el código.

Cada paradigma tiene sus propias reglas, estructuras y formas de abstraer el comportamiento del programa. Python, al ser flexible, permite adoptar varios de estos estilos en un mismo proyecto, aunque hacerlo sin criterio puede llevar a una mezcla confusa y difícil de mantener.

---

## Principales paradigmas en Python

### 1. Programación Imperativa

La programación **imperativa** se basa en dar instrucciones paso a paso para modificar el estado del programa. Es el paradigma más cercano a cómo funcionan los computadores internamente.

#### Características

- Uso explícito de variables y estructuras de control (`for`, `if`, `while`)
- Énfasis en *cómo* hacer las cosas (secuencia de acciones)
- Cambios de estado mutables

#### Ejemplo en Python

```python
numbers = [1, 2, 3, 4, 5]
squared = []

for n in numbers:
    squared.append(n * n)

print(squared)
```

---

### 2. Programación Funcional

La programación **funcional** trata a las funciones como ciudadanos de primera clase y evita cambios de estado. Favorece el uso de expresiones puras y operaciones inmutables.

#### Características

- Uso de funciones puras (sin efectos colaterales)
- Uso de `map`, `filter`, `reduce`, y comprensiones
- Enfoque declarativo: se describe *qué* hacer, no *cómo*

#### Ejemplo en Python

```python
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x * x, numbers))
print(squared)
```

> 💡 Python no es un lenguaje funcional puro, pero soporta muchos elementos funcionales.

---

### 3. Programación Orientada a Objetos (OOP)

La **OOP** organiza el código en torno a objetos que combinan datos y comportamiento. Es útil para modelar sistemas complejos y reutilizables.

#### Características

- Uso de clases y objetos
- Encapsulamiento, herencia y polimorfismo
- Agrupación de datos y funciones relacionadas

#### Ejemplo en Python

```python
class SquareCalculator:
    def __init__(self, numbers):
        self.numbers = numbers

    def square_all(self):
        return [n * n for n in self.numbers]

calc = SquareCalculator([1, 2, 3, 4, 5])
print(calc.square_all())
```

---

## Comparación entre paradigmas

| Característica        | Imperativo           | Funcional             | Orientado a Objetos       |
|------------------------|----------------------|------------------------|----------------------------|
| Enfoque                | Secuencia de pasos   | Evaluación de funciones | Modelado con objetos      |
| Estado                 | Mutable              | Inmutable              | Mutable o encapsulado     |
| Composición            | Instrucciones        | Funciones              | Clases y métodos           |
| Claridad               | Alta (procedimientos simples) | Alta (operaciones declarativas) | Alta (modelos complejos) |
| Ideal para             | Algoritmos básicos   | Transformaciones de datos | Sistemas modulares y extensibles |

---

## Buenas prácticas

- ✅ Elige el paradigma adecuado según el problema. No todos los problemas necesitan clases; algunos se resuelven con funciones puras.
- ✅ En proyectos grandes, define un estilo dominante para evitar mezclas caóticas.
- ✅ Usa comprensión de listas (`[x for x in iterable]`) y generadores como forma limpia y eficiente de aplicar estilo funcional en Python.
- ✅ Refactoriza código imperativo a funcional cuando busques mayor expresividad o menor mutabilidad.

---

## Errores comunes

- ❌ Mezclar paradigmas sin estructura clara.
- ❌ Usar programación orientada a objetos para problemas que solo requieren funciones simples.
- ❌ Aplicar funciones lambda complejas que afectan la legibilidad.
- ❌ Abusar del estado global en estilos imperativos.

---

## Recursos recomendados

- 📄 [PEP 8 – Guía de estilo Python](https://peps.python.org/pep-0008/)
- 📘 [Functional Programming HOWTO – Python Docs](https://docs.python.org/3/howto/functional.html)
- 📘 [Object-Oriented Programming – Python Docs](https://docs.python.org/3/tutorial/classes.html)
- 📚 *Fluent Python*, Luciano Ramalho – Capítulos sobre estilos funcional y orientado a objetos.

---

## Conclusión

Python es un lenguaje versátil que permite programar de muchas formas. Conocer y dominar los distintos paradigmas te permite escribir código más expresivo, modular y adecuado a cada tipo de problema.

En vez de adoptar un único paradigma rígidamente, aprende a combinar los estilos con intención y claridad. Ser consciente del paradigma que estás usando —y por qué— es una de las señales más claras de madurez como desarrollador Python.
