# Patrones de Diseño

<img src="../images/dp.png" alt="Banner del Curso" width="600" >


## Introducción

Los **patrones de diseño** son soluciones reutilizables a problemas comunes en el desarrollo de software. No son fragmentos de código listos para copiar y pegar, sino estructuras probadas que ayudan a diseñar sistemas más claros, extensibles y robustos.

En Python, gracias a su flexibilidad y naturaleza dinámica, muchos patrones pueden implementarse de manera más sencilla que en lenguajes más estáticos. Este capítulo explora algunos de los patrones más útiles y cómo aplicarlos en el contexto de desarrollo moderno con Python.

---

## ¿Por qué usar patrones de diseño?

- 💡 Estandarizan soluciones en equipos y comunidades.
- 🧩 Promueven la reutilización del conocimiento.
- 📐 Mejoran la arquitectura de sistemas complejos.
- 🚫 Ayudan a evitar malas prácticas como duplicación o acoplamiento innecesario.

---

## Clasificación de los patrones

Los patrones se suelen dividir en tres categorías principales:

| Tipo               | Propósito                            | Ejemplos comunes                |
|--------------------|----------------------------------------|---------------------------------|
| **Creacionales**   | Controlar la creación de objetos       | Singleton, Factory, Builder     |
| **Estructurales**  | Organizar relaciones entre clases      | Adapter, Decorator, Composite   |
| **Comportamiento** | Gestionar algoritmos y responsabilidades | Strategy, Observer, Command     |

---

## 1. Singleton – Un solo objeto global

### Uso típico:
Cuando necesitas garantizar que solo haya **una única instancia de una clase** (como una conexión global o una configuración).

### Ejemplo en Python:

```python
class Config:
    _instancia = None

    def __new__(cls):
        if cls._instancia is None:
            cls._instancia = super().__new__(cls)
        return cls._instancia

config1 = Config()
config2 = Config()
print(config1 is config2)  # True
```

> ☝️ Usa este patrón con precaución. A menudo se prefiere la **inyección de dependencias** sobre el acceso global.

---

## 2. Factory – Crear objetos según condiciones

### Uso típico:
Cuando quieres **delegar la creación de objetos** sin acoplarte a clases concretas.

```python
class Perro:
    def hablar(self):
        return "Guau"

class Gato:
    def hablar(self):
        return "Miau"

def fabrica_animal(tipo: str):
    clases = {"perro": Perro, "gato": Gato}
    return clases[tipo]()

animal = fabrica_animal("gato")
print(animal.hablar())  # Miau
```

> 🔍 El patrón Factory es muy útil cuando los tipos a crear pueden cambiar dinámicamente.

---

## 3. Strategy – Intercambiar algoritmos

### Uso típico:
Cuando tienes múltiples formas de realizar una tarea y quieres que el algoritmo sea **intercambiable** sin modificar el código que lo usa.

```python
class PagoEstrategia:
    def pagar(self, monto): pass

class PagoPaypal(PagoEstrategia):
    def pagar(self, monto):
        print(f"Pagando ${monto} con PayPal")

class PagoTarjeta(PagoEstrategia):
    def pagar(self, monto):
        print(f"Pagando ${monto} con Tarjeta")

class Tienda:
    def __init__(self, estrategia: PagoEstrategia):
        self.estrategia = estrategia

    def procesar_pago(self, monto):
        self.estrategia.pagar(monto)

t = Tienda(PagoTarjeta())
t.procesar_pago(100)
```

> 💡 Ideal para sistemas extensibles donde las reglas cambian según el contexto.

---

## 4. Decorator – Añadir funcionalidad sin modificar clases

### Uso típico:
Agregar comportamiento a objetos sin modificar su estructura original.

```python
def auditar(func):
    def envoltura(*args, **kwargs):
        print("Ejecutando:", func.__name__)
        return func(*args, **kwargs)
    return envoltura

@auditar
def saludar():
    print("¡Hola!")

saludar()
```

> 🧩 Python lo hace especialmente fácil gracias a su sintaxis con `@decorators`.

---

## 5. Observer – Reaccionar a cambios en tiempo real

### Uso típico:
Cuando múltiples objetos deben ser notificados automáticamente ante un cambio en otro.

```python
class Sujeto:
    def __init__(self):
        self._observadores = []

    def suscribir(self, obs):
        self._observadores.append(obs)

    def notificar(self, mensaje):
        for obs in self._observadores:
            obs.actualizar(mensaje)

class Observador:
    def actualizar(self, mensaje):
        print("Notificación:", mensaje)

sujeto = Sujeto()
obs1 = Observador()
sujeto.suscribir(obs1)
sujeto.notificar("Nuevo evento")
```

> 🔔 Muy usado en interfaces gráficas, sistemas de eventos o notificaciones.

---

## Buenas prácticas al usar patrones

✅ Usa patrones **cuando el problema lo justifique**, no por moda  
✅ Refactoriza código repetitivo o acoplado en torno a un patrón claro  
✅ Combina patrones si es necesario (ej. Strategy + Factory)  
✅ Documenta bien el propósito del patrón en tu código  

---

## Errores comunes

❌ Sobreingeniería: aplicar patrones innecesarios para problemas simples  
❌ Usar clases abstractas donde Python permite funciones o duck typing  
❌ Forzar herencia donde sería mejor composición  
❌ Implementar patrones “como en Java” sin aprovechar la idiomaticidad de Python

---

## Recursos recomendados

- 📘 [Refactoring.Guru – Design Patterns](https://refactoring.guru/design-patterns/python)
- 📚 *Head First Design Patterns* (adaptado a Python)
- 🧰 [Python Patterns (GitHub)](https://github.com/faif/python-patterns)
- 🐍 *Fluent Python*, Luciano Ramalho – Capítulos sobre diseño avanzado

---

## Conclusión

Los patrones de diseño no son reglas estrictas, sino soluciones flexibles para problemas frecuentes en la arquitectura de software. Aplicarlos correctamente en Python requiere entender tanto el patrón como las fortalezas del lenguaje. Con práctica y criterio, los patrones pueden ayudarte a escribir software más limpio, mantenible y preparado para crecer.
