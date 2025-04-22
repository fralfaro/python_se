# Validación moderna - Pydantic

<img src="../images/pydantic.svg" alt="Banner del Curso" width="600" >



## Introducción

Una de las grandes ventajas de Python moderno es su capacidad para trabajar con datos estructurados y validados sin perder legibilidad. Cuando se combinan **type hints** con validación automática, el desarrollo se vuelve más robusto y confiable. Aquí entra **Pydantic**, una biblioteca que convierte modelos de datos basados en clases en potentes herramientas de validación, serialización y parsing, todo usando anotaciones de tipo estándar.

Este capítulo introduce el uso de Pydantic en proyectos reales, explicando cómo crear modelos, validar entradas y aprovechar las ventajas del tipado estático para trabajar con datos externos.

---

## ¿Qué es Pydantic?

**Pydantic** es una biblioteca que permite definir y validar datos usando clases y anotaciones de tipo estándar de Python (`str`, `int`, `float`, `list`, etc.). Es ampliamente usada en frameworks como **FastAPI**, pero también es útil en cualquier aplicación que consuma datos de fuentes externas (APIs, formularios, archivos de configuración, etc.).

Características clave:

- Validación automática de tipos al crear instancias.
- Conversión (parsing) de tipos cuando es posible.
- Generación automática de esquemas JSON y documentación.

---

## Instalación

```bash
pip install pydantic
```

> Si usas Python 3.10+, puedes instalar Pydantic v2:  
> `pip install "pydantic>=2.0"`
>
> Para este capítulo se usan ejemplos de **Pydantic 1.10+**, compatible con FastAPI y ampliamente adoptado.

---

## Definiendo modelos con Pydantic

```python
from pydantic import BaseModel

class Usuario(BaseModel):
    nombre: str
    edad: int
    activo: bool = True
```

```python
u = Usuario(nombre="Ana", edad="30")
print(u.edad)  # 30 (conversión automática de str a int)
```

### Ventajas:

- Tipado explícito y validación inmediata.
- Conversión automática cuando el tipo es compatible.
- Atributos por defecto si no se especifican.

---

## Validación y manejo de errores

```python
from pydantic import ValidationError

try:
    Usuario(nombre="Ana", edad="no-es-numero")
except ValidationError as e:
    print(e.json())
```

Esto devolverá un error estructurado en formato JSON indicando qué campo falló y por qué.

---

## Campos opcionales y valores por defecto

```python
from typing import Optional

class Libro(BaseModel):
    titulo: str
    autor: str
    año: Optional[int] = None
```

---

## Validaciones personalizadas

Puedes agregar validaciones propias usando decoradores:

```python
from pydantic import validator

class Producto(BaseModel):
    nombre: str
    precio: float

    @validator("precio")
    def precio_debe_ser_positivo(cls, v):
        if v <= 0:
            raise ValueError("El precio debe ser mayor que cero")
        return v
```

---

## Anidación de modelos

```python
class Direccion(BaseModel):
    ciudad: str
    pais: str

class Empresa(BaseModel):
    nombre: str
    direccion: Direccion

e = Empresa(nombre="Seth&Nut", direccion={"ciudad": "Valparaíso", "pais": "Chile"})
print(e.direccion.ciudad)  # Valparaíso
```

---

## Exportar y serializar datos

```python
u = Usuario(nombre="Luis", edad=28)
print(u.dict())     # Diccionario de Python
print(u.json())     # Cadena JSON
```

---

## Integración con FastAPI y otras herramientas

Pydantic se integra naturalmente con **FastAPI**, donde se usa para validar automáticamente las entradas de una API.

```python
from fastapi import FastAPI
from pydantic import BaseModel

class Item(BaseModel):
    nombre: str
    precio: float

app = FastAPI()

@app.post("/items/")
def crear_item(item: Item):
    return {"resultado": f"{item.nombre} cuesta ${item.precio}"}
```

---

## Buenas prácticas

✅ Usa `BaseModel` como clase base para todos tus modelos  
✅ Valida datos externos lo antes posible (por ejemplo, al recibir una request)  
✅ Usa `Optional[...]` solo cuando el valor puede ser `None`  
✅ Divide modelos grandes en submodelos reutilizables  
✅ Agrega validadores personalizados para reglas de negocio específicas

---

## Errores comunes

❌ Usar `Any` en todos los campos (pierde sentido el modelo)  
❌ No capturar `ValidationError` si cargas datos de usuarios  
❌ Esperar que los modelos funcionen como `dataclasses` puras (Pydantic hace más que eso)  
❌ Modificar atributos directamente sin validación extra (usar `@root_validator` si es necesario)

---

## Referencias útiles

- 📘 [Documentación oficial de Pydantic](https://docs.pydantic.dev/)
- ⚙️ [Pydantic en FastAPI](https://fastapi.tiangolo.com/tutorial/body/)
- 🧪 [Validadores personalizados](https://docs.pydantic.dev/usage/validators/)

---

## Conclusión

Pydantic aporta una capa de seguridad y claridad en el manejo de datos en Python, especialmente cuando provienen de fuentes no confiables. Su combinación con type hints y validaciones automáticas hace que los modelos sean robustos, auto-documentados y fáciles de mantener. Es una herramienta fundamental para quienes buscan escribir software Python profesional, confiable y preparado para producción.
