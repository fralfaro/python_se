# Scripts en Python

<img src="../images/script.png" alt="Banner del Curso" width="300" >

## Introducción

Escribir funciones y clases es solo una parte del desarrollo en Python. Para que un programa funcione correctamente en la práctica, también debemos entender **cómo se ejecutan los scripts**, cómo se organizan los archivos y **cómo importar módulos** de forma efectiva.

Este capítulo presenta las convenciones y buenas prácticas relacionadas con la **ejecución de scripts**, **estructura mínima de proyectos Python** y **mecanismos de importación**, tanto para scripts pequeños como para proyectos más grandes.

---

## Ejecutar scripts en Python

El archivo más común de ejecución en Python es un script `.py`. Puedes ejecutarlo directamente desde la terminal:

```bash
python main.py
```

También puedes hacerlo desde un entorno como VS Code, PyCharm o Jupyter.

---

### `if __name__ == "__main__"`

Esta línea permite que un archivo Python se pueda ejecutar **tanto como script principal como módulo importado**.

```python
def main():
    print("Ejecutando script principal")

if __name__ == "__main__":
    main()
```

> 🔍 Cuando el archivo se ejecuta directamente, `__name__` toma el valor `"__main__"`. Si se importa como módulo, `__name__` es el nombre del archivo o paquete.

---

## Cómo importar módulos correctamente

Python permite reutilizar código importando funciones, clases o módulos desde otros archivos.

### Estructura básica:

```python
# archivo: utilidades.py
def saludar(nombre):
    return f"Hola, {nombre}"
```

```python
# archivo: main.py
from utilidades import saludar

print(saludar("Francisco"))
```

> 📂 Los archivos deben estar en el **mismo directorio** o en un **módulo disponible en el `PYTHONPATH`**.

---

## Importación absoluta vs relativa

### 🔹 Importación absoluta

Más legible, recomendada en proyectos medianos y grandes.

```python
from proyecto.modulo.util import funcion
```

### 🔸 Importación relativa

Útil dentro de paquetes internos, aunque menos explícita.

```python
from .util import funcion
from ..config import ajustes
```

> ✅ En la mayoría de los casos, **prefiere la importación absoluta**, especialmente si el proyecto es público o colaborativo.

---

## Estructura mínima de un proyecto Python

Aquí una estructura común y profesional:

```
mi_proyecto/
│
├── src/                     # Código fuente principal
│   ├── __init__.py
│   ├── main.py
│   └── modulo/
│       ├── __init__.py
│       └── operaciones.py
│
├── tests/                  # Pruebas unitarias
│   └── test_operaciones.py
│
├── requirements.txt        # Dependencias
├── README.md               # Documentación del proyecto
└── pyproject.toml / setup.py # Configuración del paquete
```

Para ejecutar correctamente desde `src/`, puedes usar:

```bash
PYTHONPATH=src python src/main.py
```

O agregar un `__init__.py` en cada subcarpeta para que Python lo reconozca como paquete.

---

## Buenas prácticas

✅ Siempre usa `if __name__ == "__main__"` en scripts ejecutables  
✅ Organiza tu código en módulos y paquetes, no todo en un solo archivo  
✅ Usa importaciones absolutas por claridad  
✅ Mantén una estructura consistente en todos tus proyectos  
✅ Usa `src/` si planeas distribuir tu código como paquete

---

## Errores comunes

❌ No usar `__name__ == "__main__"` y ejecutar scripts importados involuntariamente  
❌ Nombres de archivos que colisionan con módulos estándar (`random.py`, `json.py`)  
❌ Importaciones circulares entre módulos  
❌ Copiar/pegar código entre scripts en lugar de modularizarlo  
❌ Ejecutar módulos sin configurar el entorno (ej: sin definir `PYTHONPATH`)

---

## Recursos recomendados

- 📘 [The Module System – Python Docs](https://docs.python.org/3/tutorial/modules.html)
- 📁 [Structuring Your Project](https://docs.python-guide.org/writing/structure/)
- 🧪 [Effective Python – Brett Slatkin](https://effectivepython.com/)

---

## Conclusión

Comprender cómo se organizan, ejecutan e interconectan los archivos Python es un paso clave para escalar tu código de scripts simples a aplicaciones modulares y mantenibles. Un buen diseño empieza con una buena estructura de carpetas, archivos bien nombrados y un uso claro de `import` y `main`.
