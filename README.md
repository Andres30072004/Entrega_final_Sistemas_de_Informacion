# Entrega Final – Sistemas de Información  
## Orbe Propiedad Raíz – Solución Tecnológica Implementada

## 1. Descripción General del Proyecto  
Este repositorio contiene la solución tecnológica desarrollada para optimizar el proceso de captación, validación y publicación de inmuebles en la empresa Orbe Propiedad Raíz.  
Como resultado del análisis BPM (“AS-IS” y “TO-BE”) y de la priorización de problemáticas, se construyó un sistema que automatiza:

- La captura de información del propietario e inmueble.  
- La validación automática de documentos.  
- La centralización de datos en un CRM.  
- La publicación (sindicación) del inmueble hacia portales inmobiliarios.  

Esta solución responde a los cuellos de botella detectados en la operación actual de la empresa: la validación manual realizada por el asesor comercial y la duplicidad de carga realizada por el equipo de marketing.

---

## 2. Objetivo  
Diseñar e implementar una solución digital que permita:

- Reducir el tiempo de publicación (Time-to-Market).  
- Eliminar errores derivados de doble digitación.  
- Aumentar eficiencia comercial y operativa.  
- Crear una fuente única de verdad donde se centraliza toda la información del inmueble.  
- Integrar la captación, validación y sindicación en un solo flujo.

---

## 3. Arquitectura de la Solución  
La solución se diseñó en cuatro capas principales:

### 3.1 Capa de Presentación  
- Portal del Propietario (captación de inmuebles).  
- Interfaz del CRM (gestión por parte del asesor comercial, legal y marketing).

### 3.2 Capa de Lógica de Negocio  
- Backend desarrollado en Python (FastAPI).  
- Módulo de Validación Automática.  
- Módulo de Sindicación.  
- Gestión de estados del inmueble.  

### 3.3 Capa de Integración  
- API del CRM.  
- Integración futura con APIs de Finca Raíz, Metrocuadrado, Ciencuadras.

### 3.4 Capa de Datos  
- Base de datos SQLite (modo desarrollo).  
- Migrable a PostgreSQL/MySQL para despliegue real.  

---

## 4. Funcionalidades Implementadas

### 4.1 Captación mediante Formulario Web (API)
El sistema recibe:

- Datos del propietario  
- Datos del inmueble  
- Documentos obligatorios (PDF/IMG)

Endpoint:  
POST /api/inmuebles/


### 4.2 Validación Automática  
Reglas implementadas:

- Verificación de documentos mínimos.  
- Coherencia entre área, precio y tipo de inmueble.  
- Actualización automática del estado.  
- Detección de valores atípicos (precio/m²).

### 4.3 CRM Básico  
Incluye:

- Listar inmuebles  
- Ver detalles  
- Ver documentos asociados  
- Estados: captada, validada, pendiente, publicada

### 4.4 Sindicación Automática  
El sistema publica el inmueble hacia portales (mock implementado) mediante un proceso en background.

Endpoint:  
POST /api/sindicacion/{id}


---

## 5. Tecnologías Utilizadas

- Python 3.10  
- FastAPI  
- SQLAlchemy  
- SQLite (modo desarrollo)  
- Uvicorn  
- API REST  
- Estructura modular para escalabilidad  

---

## 6. Estructura del Proyecto
orbe_crm/
├─ app/
│ ├─ main.py
│ ├─ models.py
│ ├─ database.py
│ ├─ schemas.py
│ ├─ crud.py
│ ├─ validation.py
│ ├─ sindication.py
│ └─ static_uploads/
├─ requirements.txt
└─ README.md


---

## 7. Instalación y Ejecución

### 7.1 Clonar el repositorio
git clone https://github.com/usuario/entrega_final_sistemas_de_informacion.git

cd entrega_final_sistemas_de_informacion


### 7.2 Crear entorno virtual
python -m venv venv
venv\Scripts\activate (Windows)
source venv/bin/activate (Linux/Mac)


### 7.3 Instalar dependencias
pip install -r requirements.txt

### 7.4 Ejecutar servidor
uvicorn app.main:app --reload

### 7.5 Acceder a la documentación interactiva
http://localhost:8000/docs

---

## 8. Endpoints Principales

### Crear un inmueble (con documentos)
POST /api/inmuebles/

### Ver todos los inmuebles
GET /api/inmuebles/

### Validar inmueble manualmente
POST /api/validacion/{id}

### Iniciar proceso de sindicación (publicación)
POST /api/sindicacion/{id}

---

## 9. Indicadores Mejorados

El sistema contribuye directamente a la mejora de los KPIs definidos en el análisis:

- Reducción del Time-to-Market.  
- Eliminación de carga duplicada.  
- Reducción de errores administrativos.  
- Mayor productividad del asesor comercial.  
- Mayor eficiencia del equipo de marketing.  

---

## 10. Lecciones Aprendidas

- Las soluciones tecnológicas deben integrarse al proceso real del cliente.  
- La arquitectura modular facilita la evolución del sistema.  
- La automatización elimina tareas de bajo valor operativo.  
- El prototipado permite validar con usuarios reales antes de una inversión mayor.  

---

## 11. Bibliografía

- Odoo: https://www.odoo.com/es_ES  
- TEC Evaluation: https://www3.technologyevaluation.com/es  
- FastAPI Docs: https://fastapi.tiangolo.com  
- SQLAlchemy Docs: https://docs.sqlalchemy.org  

---

## 12. Licencia  
Proyecto desarrollado con fines académicos para la Universidad EAFIT.  
No está autorizado su uso comercial sin permiso de los autores.
