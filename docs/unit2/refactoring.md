# Refactorización de Código

<img src="../images/refactor.png" alt="Banner del Curso" width="800" >



## Introducción

A medida que el software crece, el código tiende a volverse más complejo, repetitivo o difícil de mantener. **Refactorizar** es el proceso de reestructurar ese código —mejorando su legibilidad y diseño interno— **sin modificar su comportamiento externo**.

Refactorizar no es algo que se hace solo al final de un proyecto: es una práctica continua que distingue al desarrollador profesional. Este capítulo presenta los principios, técnicas y patrones comunes de refactorización en Python.

---

## ¿Qué es la refactorización?

La **refactorización** consiste en cambiar la estructura del código para que sea más limpio, comprensible y mantenible, **sin alterar lo que hace**. Es como reorganizar una habitación: todo sigue estando allí, pero es más fácil de usar.

> 💡 Refactorizar no es optimizar. Optimizar busca rendimiento. Refactorizar busca claridad.

---

## ¿Cuándo refactorizar?

- Antes de agregar nuevas funcionalidades
- Cuando detectas duplicación de código
- Al ver funciones/clases demasiado largas o acopladas
- Cuando otros no pueden entender tu código sin ayuda
- Como parte del ciclo: *escribe – prueba – refactoriza*

---

## Principios clave

- 🔁 **Pequeños pasos**: haz cambios incrementales, fáciles de testear.
- 🧪 **Red de seguridad**: asegúrate de tener pruebas automatizadas.
- 🧠 **Mantén la intención clara**: el código debe ser más legible después de refactorizar.
- ✋ **No refactorices mientras implementas funcionalidades nuevas.**

---

## Ejemplos comunes de refactorización

### ✅ Renombrar variables y funciones

❌ Antes:

```python
def calc(x, y):
    return x * y
```

✅ Después:

```python
def calcular_area(base, altura):
    return base * altura
```

---

### ✅ Extraer funciones

Cuando una función hace muchas cosas, sepárala en partes más claras:

```python
def procesar_usuario(usuario):
    if not usuario.get("activo"):
        return "Inactivo"
    enviar_bienvenida(usuario["email"])
    return "Activo"
```

Separado:

```python
def es_activo(usuario):
    return usuario.get("activo", False)

def enviar_bienvenida(email):
    print(f"Correo enviado a {email}")

def procesar_usuario(usuario):
    if not es_activo(usuario):
        return "Inactivo"
    enviar_bienvenida(usuario["email"])
    return "Activo"
```

---

### ✅ Eliminar duplicación

Antes:

```python
def area_rectangulo(base, altura):
    return base * altura

def area_paralelogramo(base, altura):
    return base * altura
```

Después:

```python
def calcular_area(base, altura):
    return base * altura
```

---

### ✅ Usar estructuras idiomáticas de Python

Antes:

```python
valores = []
for x in datos:
    if x > 0:
        valores.append(x)
```

Después:

```python
valores = [x for x in datos if x > 0]
```

---

## Refactorizaciones estructurales

### 🔹 Separar responsabilidades (Single Responsibility)

```python
class Factura:
    def calcular_total(self): ...
    def exportar_pdf(self): ...  # ❌ mezcla lógica de presentación
```

✅ Refactorizado:

```python
class Factura:
    def calcular_total(self): ...

class ExportadorFacturaPDF:
    def exportar(self, factura: Factura): ...
```

---

### 🔹 Reemplazar condicionales con polimorfismo

```python
def calcular_total(tipo, monto):
    if tipo == "normal":
        return monto
    elif tipo == "descuento":
        return monto * 0.9
```

✅ Refactorizado:

```python
class EstrategiaPrecio:
    def calcular(self, monto): ...

class Normal(EstrategiaPrecio):
    def calcular(self, monto):
        return monto

class ConDescuento(EstrategiaPrecio):
    def calcular(self, monto):
        return monto * 0.9
```

---

## Herramientas útiles

| Herramienta  | Uso principal                      |
|--------------|------------------------------------|
| `black`      | Reformatador automático            |
| `ruff`       | Linter y verificador de estilo     |
| `pytest`     | Pruebas antes/después de refactorizar |
| IDEs (VS Code, PyCharm) | Soporte para renombrar, extraer funciones, mover clases |

---

## Buenas prácticas

✅ Refactoriza **con intención**: mejora la claridad o extensibilidad  
✅ Haz refactorizaciones **pequeñas y reversibles**  
✅ Usa herramientas automáticas para detectar oportunidades (`ruff`, `flake8`)  
✅ Acompaña tus cambios con **tests automáticos**

---

## Errores comunes

❌ Refactorizar sin pruebas que respalden el comportamiento  
❌ Hacer refactorizaciones grandes sin revisar impacto  
❌ Cambiar nombres sin propósito (confunde al equipo)  
❌ Refactorizar al mismo tiempo que implementas una nueva feature

---

## Recursos recomendados

- 📘 [Refactoring (Martin Fowler)](https://refactoring.com/)
- 🧰 [Python Refactoring Toolkit (GitHub)](https://github.com/isidentical/refactor)
- 🐍 [Clean Code – Robert C. Martin]
- 🧪 [pytest](https://docs.pytest.org/) + [black](https://black.readthedocs.io/) + [ruff](https://docs.astral.sh/ruff/)

---

## Conclusión

Refactorizar no es una acción puntual, sino una práctica continua del desarrollo profesional. Mejora la salud del código, reduce el riesgo de errores y facilita que tu software pueda evolucionar con el tiempo. Al dominar la refactorización, conviertes código frágil en estructuras sólidas y adaptables.
