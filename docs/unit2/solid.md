# Principio SOLID


<img src="../images/solid.png" alt="Banner del Curso" width="600" >



## Introducción

Los principios **SOLID** son cinco directrices fundamentales del diseño orientado a objetos, formuladas para escribir software que sea **fácil de entender, mantener y escalar**. Aunque surgieron en lenguajes como C++ y Java, se aplican perfectamente a Python y son una base clave del diseño profesional de software.

Este capítulo presenta los principios SOLID con ejemplos concretos en Python, buenas prácticas y advertencias sobre errores comunes.

---

## ¿Qué significa SOLID?

Cada letra representa un principio:

| Letra | Nombre                                | Descripción breve                                      |
|-------|----------------------------------------|--------------------------------------------------------|
| S     | Single Responsibility Principle (SRP) | Una clase debe tener una sola razón para cambiar.     |
| O     | Open/Closed Principle (OCP)           | El código debe estar abierto a extensión, cerrado a modificación. |
| L     | Liskov Substitution Principle (LSP)   | Las subclases deben poder reemplazar a sus superclases. |
| I     | Interface Segregation Principle (ISP) | No forzar a los objetos a implementar métodos que no usan. |
| D     | Dependency Inversion Principle (DIP)  | Depender de abstracciones, no de implementaciones concretas. |

---

## 1. SRP – Principio de Responsabilidad Única

> "Una clase debe tener una sola razón para cambiar."

### ❌ No SRP

```python
class Reporte:
    def generar(self):
        # lógica de negocio
        pass

    def exportar_pdf(self):
        # lógica de presentación
        pass
```

Esta clase mezcla lógica de negocio con lógica de presentación.

### ✅ Con SRP

```python
class Reporte:
    def generar(self):
        return {"contenido": "datos"}

class ExportadorPDF:
    def exportar(self, data):
        print("Exportando PDF:", data)
```

---

## 2. OCP – Principio Abierto/Cerrado

> "El código debe estar abierto a extensión, pero cerrado a modificación."

### ❌ Sin OCP

```python
def calcular_precio(producto, tipo):
    if tipo == "normal":
        return producto.precio
    elif tipo == "descuento":
        return producto.precio * 0.9
```

Cada nuevo tipo rompe el código existente.

### ✅ Con OCP

```python
class EstrategiaPrecio:
    def calcular(self, producto):
        raise NotImplementedError()

class PrecioNormal(EstrategiaPrecio):
    def calcular(self, producto):
        return producto.precio

class PrecioConDescuento(EstrategiaPrecio):
    def calcular(self, producto):
        return producto.precio * 0.9
```

---

## 3. LSP – Principio de Sustitución de Liskov

> "Las subclases deben ser sustituibles por sus superclases sin romper el programa."

### ❌ Violación LSP

```python
class Pato:
    def volar(self):
        return "vuela"

class PatoDeGoma(Pato):
    def volar(self):
        raise Exception("¡No puede volar!")
```

### ✅ Cumplimiento LSP

```python
class Ave:
    def hacer_sonido(self):
        pass

class Pato(Ave):
    def hacer_sonido(self):
        return "cuac"

class PatoDeGoma(Ave):
    def hacer_sonido(self):
        return "chirriido"
```

---

## 4. ISP – Principio de Segregación de Interfaces

> "Una clase no debe estar obligada a implementar métodos que no necesita."

Python no tiene interfaces explícitas, pero este principio se aplica en **diseño de clases y herencias**.

### ❌ Mal diseño

```python
class Animal:
    def volar(self): ...
    def nadar(self): ...
```

No todos los animales hacen ambas cosas.

### ✅ Buen diseño

```python
class PuedeNadar:
    def nadar(self): ...

class PuedeVolar:
    def volar(self): ...
```

Cada clase implementa solo lo que necesita.

---

## 5. DIP – Principio de Inversión de Dependencias

> "Depende de abstracciones, no de implementaciones concretas."

### ❌ Acoplamiento fuerte

```python
class ServicioCorreo:
    def enviar(self, mensaje):
        print("Enviando correo:", mensaje)

class Notificador:
    def __init__(self):
        self.correo = ServicioCorreo()
```

### ✅ Inversión de dependencia

```python
class CanalNotificacion:
    def enviar(self, mensaje):
        pass

class ServicioCorreo(CanalNotificacion):
    def enviar(self, mensaje):
        print("Correo:", mensaje)

class Notificador:
    def __init__(self, canal: CanalNotificacion):
        self.canal = canal
```

Esto permite inyectar diferentes canales sin cambiar la clase `Notificador`.

---

## Buenas prácticas al aplicar SOLID

✅ Refactoriza clases grandes en responsabilidades más pequeñas  
✅ Usa composición y estrategias para evitar condicionales  
✅ Evita herencias innecesarias: prefiere interfaces y protocolos (composición > herencia)  
✅ Añade tests para validar comportamiento antes y después de aplicar SOLID  
✅ En Python 3.8+, puedes usar `Protocol` de `typing` como forma ligera de interfaces

---

## Errores comunes

❌ Aplicar todos los principios de forma rígida desde el día uno  
❌ Crear clases o jerarquías complejas sin necesidad real  
❌ No validar si la refactorización realmente mejora el diseño  
❌ Confundir "extensibilidad" con "generalización excesiva"

---

## Recursos recomendados

- 📘 [The Principles of OOP – SOLID](https://en.wikipedia.org/wiki/SOLID)
- 📚 *Clean Architecture* – Robert C. Martin
- 🧰 [Design Patterns in Python](https://refactoring.guru/design-patterns/python)
- 📗 [Real Python – SOLID principles](https://realpython.com/solid-principles-python/)

---

## Conclusión

Aplicar los principios SOLID en Python permite diseñar software más robusto, flexible y mantenible. No se trata de seguir reglas por seguirlas, sino de tener criterios sólidos para escribir clases y estructuras que puedan adaptarse a cambios con el menor impacto posible.

Piensa en SOLID como una brújula para el diseño profesional: no dicta el camino exacto, pero te ayuda a evitar muchos errores comunes.
