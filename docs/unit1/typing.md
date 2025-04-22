# Tipado moderno - Typing
<img src="../images/typing.png" alt="Banner del Curso" width="600" >



## Introducción

Aunque Python es un lenguaje de tipado dinámico, desde la versión 3.5 ha incorporado soporte para **tipado estático** mediante *type hints*. Esta funcionalidad permite a los desarrolladores declarar los tipos de variables, argumentos y retornos de funciones, lo cual mejora la legibilidad del código y permite la detección temprana de errores mediante herramientas externas.

En este capítulo aprenderás a usar anotaciones de tipo de forma práctica y progresiva, entendiendo su utilidad, sintaxis, beneficios y cómo integrarlas con herramientas como `mypy` y `Pyright`.

---

## ¿Qué es el tipado estático?

El **tipado estático** consiste en declarar los tipos de variables y funciones para que puedan ser verificados antes de ejecutar el código. En Python, esto es completamente **opcional**, pero se ha convertido en una práctica común en proyectos profesionales.

Python sigue siendo dinámico en tiempo de ejecución, pero con **type hints** puedes aplicar análisis estático con herramientas externas.

---

## Sintaxis básica de anotaciones de tipo

### Funciones con anotaciones

```python
def saludar(nombre: str) -> str:
    return f"Hola, {nombre}"
```

### Variables con anotaciones

```python
edad: int = 30
es_activo: bool = True
```

> ✅ Estas anotaciones no afectan la ejecución del programa, pero permiten a linters y editores ofrecer mejores sugerencias y validaciones.

---

## Tipos comunes

| Tipo Python | Descripción                  |
|-------------|------------------------------|
| `int`       | Números enteros              |
| `float`     | Números decimales            |
| `str`       | Cadenas de texto             |
| `bool`      | Booleanos (`True`, `False`)  |
| `list[str]` | Lista de cadenas             |
| `dict[str, int]` | Diccionario con claves `str` y valores `int` |

### Ejemplo

```python
def obtener_edades() -> dict[str, int]:
    return {"Ana": 25, "Luis": 32}
```

---

## Anotaciones avanzadas

### 1. `Union` y `Optional`

```python
from typing import Union, Optional

def procesar(valor: Union[int, str]) -> str:
    return str(valor)

def buscar(id: int) -> Optional[str]:
    return "dato" if id == 1 else None
```

- `Union[int, str]`: acepta uno u otro.
- `Optional[str]`: igual a `Union[str, None]`.

---

### 2. `Any` y `Literal`

```python
from typing import Any, Literal

def debug(valor: Any) -> None:
    print(valor)

def set_estado(estado: Literal["activo", "inactivo"]) -> None:
    pass
```

- `Any`: desactiva el chequeo de tipos.
- `Literal`: restringe a valores específicos.

---

### 3. `TypedDict`, `NewType`, `TypeAlias`

```python
from typing import TypedDict, NewType

class Usuario(TypedDict):
    nombre: str
    edad: int

UserID = NewType("UserID", int)
```

- `TypedDict`: estructuras con forma de diccionarios.
- `NewType`: define nuevos identificadores de tipo.

---

## Tipado en colecciones

```python
from typing import List, Tuple, Dict

nombres: List[str] = ["Ana", "Luis"]
coordenadas: Tuple[float, float] = (33.5, -70.6)
personas: Dict[str, int] = {"Ana": 25, "Luis": 32}
```

> A partir de Python 3.9 se puede usar la sintaxis corta: `list[str]`, `tuple[str, int]`.

---

## Uso con `mypy` y otros analizadores

### Instalación de `mypy`

```bash
pip install mypy
```

### Ejemplo de análisis

```bash
mypy archivo.py
```

Esto revisará si las anotaciones son coherentes con el uso del código. También puedes integrarlo en tu CI/CD.

### Alternativas:

- `pyright`: analizador rápido desarrollado por Microsoft (VS Code).
- `pyre`: analizador de tipos estático creado por Meta.

---

## Buenas prácticas

✅ Añade anotaciones especialmente en funciones públicas o de librerías  
✅ Usa `Optional` y `Union` para modelar correctamente entradas flexibles  
✅ Prefiere `list[int]` sobre `List[int]` si usas Python ≥ 3.9  
✅ Acompaña el tipado con herramientas como `mypy` o `ruff check`  

---

## Errores comunes

❌ Pensar que las anotaciones obligan el tipo en tiempo de ejecución  
❌ Usar `Any` en exceso (pierde valor el análisis)  
❌ Ignorar advertencias de `mypy` sin analizarlas  
❌ Mezclar anotaciones incompletas con funciones complejas

---

## Referencias útiles

- 📘 [PEP 484 – Type Hints](https://peps.python.org/pep-0484/)
- 🧰 [Typing – Módulo oficial](https://docs.python.org/3/library/typing.html)
- 📚 [mypy – Documentación oficial](https://mypy.readthedocs.io/en/stable/)
- 🚀 [pyright – Type Checker para Python](https://github.com/microsoft/pyright)

---

## Conclusión

El tipado estático en Python no es obligatorio, pero su adopción ha demostrado ser un recurso valioso para detectar errores antes de ejecutar el código, mejorar la documentación implícita y facilitar la colaboración en equipos. Usar `typing` junto con herramientas de análisis convierte tu código en una fuente más confiable y robusta, sin sacrificar la flexibilidad que caracteriza a Python.
