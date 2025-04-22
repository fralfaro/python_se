# Convenciones y Estilo (PEP 8)

<img src="../images/pep8.png" alt="Banner del Curso" width="300" >

## Introducción

En el mundo del desarrollo de software, seguir convenciones no es simplemente una cuestión de estilo: es una práctica fundamental que mejora la legibilidad, mantenibilidad y colaboración dentro de los proyectos. En Python, estas convenciones están formalizadas a través de las **PEPs (Python Enhancement Proposals)**, una colección de documentos que definen tanto aspectos técnicos del lenguaje como sus prácticas de uso.

Dentro de este conjunto, la **PEP 8** se ha convertido en la guía de estilo por excelencia para escribir código Python limpio y legible. Comprender qué son las PEPs y por qué es tan importante adherirse a convenciones como la PEP 8 es el primer paso para escribir software profesional en Python.

---

## ¿Qué es una PEP?

Una **PEP (Python Enhancement Proposal)** es un documento oficial que propone nuevas funcionalidades, cambios o mejoras en el lenguaje Python, su estándar de biblioteca o sus procesos de desarrollo. Son propuestas públicas que se discuten, evalúan y, en muchos casos, adoptan como parte del desarrollo oficial del lenguaje.

Las PEPs pueden clasificarse en tres tipos principales:

| Tipo de PEP        | Descripción                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| **Estándar**       | Proponen cambios en la sintaxis o comportamiento de Python.                |
| **Informativas**   | Documentan buenas prácticas y convenciones aceptadas por la comunidad.     |
| **De proceso**     | Describen aspectos organizativos del desarrollo de Python.                 |

Algunos ejemplos notables:

- 📜 **PEP 8**: Guía de estilo para el código Python.
- 🧠 **PEP 20**: *The Zen of Python*, una colección de aforismos sobre la filosofía del lenguaje.
- 🔒 **PEP 484**: Introducción del tipado estático en Python con anotaciones.

> 📎 **Nota**: Todas las PEPs están disponibles en el sitio oficial: [https://peps.python.org](https://peps.python.org)

---

## La PEP 8 y la importancia del estilo

La **PEP 8** es una de las PEPs más influyentes. Define un conjunto de reglas de estilo para escribir código Python de forma clara, coherente y profesional. Aunque el intérprete de Python no obliga a seguir estas reglas, su adopción generalizada ha generado un *idioma común* entre los desarrolladores Python en todo el mundo.

### ¿Por qué seguir la PEP 8?

- ✅ **Legibilidad**: El código limpio y consistente es más fácil de leer y entender.
- 🤝 **Colaboración**: Cuando todos siguen el mismo estilo, se minimizan conflictos y malentendidos en equipos de trabajo.
- 🛠️ **Herramientas compatibles**: Muchas herramientas como `black`, `ruff`, `flake8` o incluso editores como VS Code están diseñadas para trabajar con estas convenciones.
- 📈 **Mantenibilidad**: El código bien estructurado es más fácil de mantener, refactorizar y extender con el tiempo.

---

## Ejemplos prácticos: Malas y buenas prácticas según PEP 8

### ❌ Código que no sigue PEP 8

```python
def add(x,y):return x+y
classmath:pass
```

- No hay espacios después de las comas.
- La función está en una sola línea sin claridad.
- El nombre de la clase no está en formato `PascalCase`.
- Falta un bloque `body` en la clase.

---

### ✅ Código que sigue PEP 8

```python
class Math:
    def add(self, x, y):
        return x + y
```

- La clase está correctamente capitalizada (`PascalCase`).
- La función tiene espacios adecuados y cada instrucción en su propia línea.
- El bloque `body` está correctamente indentado (4 espacios).

---

## Recomendaciones prácticas

### Buenas prácticas

- Usa 4 espacios por nivel de indentación (nunca tabulaciones).
- Limita la longitud de línea a 79 caracteres.
- Nombra tus variables, funciones y clases de manera descriptiva:
    - `snake_case` para variables y funciones.
    - `PascalCase` para clases.
    - `UPPER_CASE` para constantes.

### Errores comunes

- Escribir todo en una línea por brevedad (perdiendo claridad).
- No dejar espacios alrededor de operadores.
- Ignorar la consistencia entre módulos y funciones.
- Usar nombres genéricos como `x`, `data`, `temp` en exceso.

---

## Herramientas para seguir PEP 8 automáticamente

Utilizar herramientas de análisis y formateo puede ayudarte a mantener el estilo sin esfuerzo manual.

| Herramienta | Funcionalidad                         | Instalación                 |
|-------------|----------------------------------------|-----------------------------|
| **black**   | Formateador automático de código       | `pip install black`        |
| **ruff**    | Linter + formateador ultrarrápido      | `pip install ruff`         |
| **flake8**  | Linter tradicional basado en PEP 8     | `pip install flake8`       |

### Ejemplo de uso con `black`

```bash
black archivo.py
```

Esto reescribirá tu archivo `archivo.py` con formato estándar basado en PEP 8.

---

## Cómo configurar tu editor

### Visual Studio Code (VS Code)

1. Instala las extensiones:
    - Python (Microsoft)
    - Black Formatter
    - Ruff
2. Añade a tu configuración (`settings.json`):

```json
{
  "editor.formatOnSave": true,
  "python.formatting.provider": "black",
  "python.linting.ruffEnabled": true,
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  }
}
```

### PyCharm

1. Habilita el análisis de estilo en *Settings > Code Style > Python*.
2. Integra `black` y `flake8` desde *External Tools*.

---

## Referencias útiles

- 📝 [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/)
- 📚 [PEP Index oficial](https://peps.python.org/)
- ⚙️ [Black – The Uncompromising Code Formatter](https://black.readthedocs.io/)
- 🚀 [Ruff – Fast Python linter & formatter](https://docs.astral.sh/ruff/)
- 🧪 [Flake8 – Python style guide enforcement](https://flake8.pycqa.org/)

---

## Conclusión

Las PEPs son una piedra angular del ecosistema Python, y en particular, la PEP 8 ha sido clave para establecer una cultura de código limpio, legible y mantenible. Adoptar estas convenciones no es solo una cuestión de estilo, sino un compromiso con la calidad y la colaboración profesional.

Integrar estas prácticas desde el inicio no solo facilitará tu trabajo, sino que también te abrirá las puertas a participar eficazmente en equipos, contribuir en proyectos open source y desarrollar software que perdure y escale.

