# Estructura de Proyectos

<img src="../images/folders4.png" alt="Banner del Curso" width="300" >



## Introducción

A medida que los proyectos crecen, la forma en que organizamos archivos, módulos y paquetes se vuelve tan importante como el propio código. Una **estructura de proyecto clara y coherente** facilita el mantenimiento, la colaboración en equipo y la escalabilidad.

Este capítulo explora buenas prácticas de organización de proyectos Python, estructuras recomendadas y errores comunes a evitar.

---

## ¿Por qué importa la estructura?

- 🧠 Facilita la comprensión del proyecto por nuevos integrantes.
- 🔍 Mejora la navegación y la búsqueda de módulos específicos.
- 🛠️ Permite integrar herramientas de testing, linting, documentación y CI/CD de forma sencilla.
- 🚀 Prepara el proyecto para distribución, empaquetado o despliegue.

---

## Estructura mínima recomendada

Un esquema básico y profesional de proyecto Python es:

```
mi_proyecto/
│
├── src/                  # Código fuente principal
│   ├── __init__.py
│   ├── main.py
│   └── modulo/
│       ├── __init__.py
│       └── operaciones.py
│
├── tests/                # Pruebas automatizadas
│   └── test_operaciones.py
│
├── README.md             # Documentación inicial
├── requirements.txt      # Dependencias del proyecto
├── pyproject.toml        # Configuración del proyecto (estándar moderno)
└── .gitignore            # Exclusiones de control de versiones
```

---

## Detalle de carpetas y archivos

| Componente        | Propósito                                              |
|-------------------|---------------------------------------------------------|
| `src/`            | Código fuente real del proyecto.                       |
| `tests/`          | Código de pruebas unitarias y de integración.           |
| `README.md`       | Instrucciones básicas para usuarios y colaboradores.    |
| `requirements.txt` | Listado de dependencias (usado por `pip`).              |
| `pyproject.toml`  | Configuración de herramientas como linters, formatters y build. |
| `.gitignore`      | Archivos/carpetas que no deben ser versionados.          |

---

## Organización dentro de `src/`

A medida que crece el proyecto, dentro de `src/` es buena práctica agrupar el código en **módulos lógicos**:

```
src/
│
├── app.py              # Punto de entrada principal
├── services/           # Lógica de negocio (servicios)
├── models/             # Modelos de datos
├── utils/              # Utilidades auxiliares
└── config/             # Configuración y constantes
```

Cada carpeta debería tener un `__init__.py` (puede estar vacío) para indicar que es un paquete de Python.

---

## ¿Por qué usar carpeta `src/`?

- Evita problemas de importaciones accidentales al testear.
- Separa claramente el código fuente del resto del proyecto.
- Mejora la compatibilidad con herramientas modernas (Poetry, Hatch, etc.).

> 🧠 Sin `src/`, a veces los tests funcionan "por accidente" porque Python encuentra el módulo en el mismo nivel. Con `src/`, solo encuentran los módulos que realmente instalaste o configuraste.

---

## Recomendaciones adicionales

✅ Usa nombres de carpetas en **minúscula y snake_case** (`utils/`, `services/`)  
✅ Agrupa funciones/métodos relacionados en un mismo módulo  
✅ Prefiere múltiples módulos pequeños sobre uno monolítico gigante  
✅ Agrega un `README.md` mínimo también dentro de cada carpeta grande (`services/`, `models/`) explicando su rol  
✅ Mantén los tests espejados respecto al código fuente (ej: `src/modulo/operaciones.py` → `tests/modulo/test_operaciones.py`)

---

## Errores comunes

❌ Mezclar scripts ejecutables y lógica de negocio en un solo archivo  
❌ Tener importaciones circulares entre módulos  
❌ No separar configuraciones (`config/`) de lógica (`services/`)  
❌ No usar paquetes explícitos (`__init__.py`) en proyectos grandes

---

## Recursos recomendados

- 📘 [Python Application Layout – The Hitchhiker’s Guide to Python](https://docs.python-guide.org/writing/structure/)
- 📚 [Best Practices for Structuring Python Projects](https://realpython.com/python-application-layouts/)
- 🧰 [Modern Python Packaging with pyproject.toml](https://packaging.python.org/en/latest/tutorials/packaging-projects/)

---

## Conclusión

Una buena estructura de proyecto no es un lujo: es una necesidad para cualquier aplicación Python que aspire a crecer y mantenerse en el tiempo. Adoptar un esquema profesional desde el principio permite un desarrollo más ágil, colaborativo y organizado, haciendo que tu software sea más fácil de testear, desplegar y evolucionar.
