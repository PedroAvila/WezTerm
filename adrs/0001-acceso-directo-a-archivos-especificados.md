# Registro de Decisiones de Arquitectura (ADR)

## ADR 0001: Regla de Acceso Directo y Exclusivo a Archivos Especificados

* **Estado:** Aceptado
* **Fecha:** 2026-11-24
* **Ámbito:** Interacción de agentes de inteligencia artificial y desarrolladores en el espacio de trabajo `D:\WezTerm`.

---

### 1. Contexto y Problema

Cuando el usuario solicita una modificación, adición o consulta indicando de forma explícita el nombre de un archivo (por ejemplo, mediante rutas directas, nombres exactos o menciones tipo `@[nombre_archivo]`), en ocasiones el agente realiza lecturas exploratorias, inspecciones o búsquedas no solicitadas en otros archivos del repositorio.

Este comportamiento genera:
1. **Pérdida de tiempo:** Retrasos innecesarios en la ejecución y entrega de la respuesta requerida por el usuario.
2. **Gasto innecesario de tokens:** Consumo superfluo de tokens de entrada y de contexto con información irrelevante para la tarea en curso.
3. **Fricción operativa:** Sobrecarga el flujo de trabajo con operaciones innecesarias.

---

### 2. Factores Decisivos

* **Eficiencia máxima:** Minimizar los turnos y el consumo de tokens eliminando pasos exploratorios cuando el objetivo ya está determinado.
* **Precisión:** Cuando el usuario proporciona el archivo destino exacto, la intención es inequívoca y delimitada.
* **Respeto a las instrucciones del usuario:** Operar estrictamente sobre el alcance definido por el usuario.

---

### 3. Decisión Adoptada

Se establece la siguiente **regla obligatoria** para cualquier agente de IA o colaborador en este repositorio:

> **REGLA DE ACCESO DIRECTO:**
> **Si el usuario proporciona el nombre o la ruta exacta del archivo a intervenir o consultar:**
> 1. **Acceso directo y exclusivo:** El agente debe ir **única y directamente** a dicho archivo objetivo.
> 2. **Prohibición de búsquedas colaterales:** Queda estrictamente **prohibido** buscar, listar, leer o inspeccionar otros archivos del repositorio para "revisar contexto general", comparar estilos o verificar información no solicitada.
> 3. **Operación quirúrgica:** Ejecutar la lectura, edición o consulta exclusivamente sobre el archivo especificado y verificar los cambios de inmediato sin ampliar el alcance.
> 4. **Excepción única:** Solo se permite consultar otros archivos si el usuario lo pide de forma explícita en su mensaje o si una dependencia rota impide completar la tarea técnica sin dicha referencia.

---

### 4. Consecuencias

#### Positivas (Beneficios)
* **Ahorro drástico de tokens:** Cero desperdicio de tokens en lecturas no requeridas.
* **Mayor rapidez:** Respuestas instantáneas y modificaciones aplicadas sin demoras exploratorias.
* **Enfoque estricto:** Modificaciones precisas y contenidas exactamente en el archivo que el usuario indicó.

#### Consideraciones
* Si el archivo indicado requiere coordinación con otro archivo y el usuario no lo mencionó, el agente no inspeccionará ni modificará archivos secundarios de forma automática; se limitará al archivo solicitado o consultará al usuario si es estrictamente indispensable.

---

### 5. Documentos Relacionados

* [`AGENTS.md`](file:///D:/WezTerm/AGENTS.md) — Reglas y directivas fundamentales del proyecto.
