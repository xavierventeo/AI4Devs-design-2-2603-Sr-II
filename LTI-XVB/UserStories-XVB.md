# User Stories para LTI - Applicant Tracking System

## Infraestructura Mínima para MVP

**ID:** US-001

**Historia:**  
Como reclutador  
Quiero autenticarme en el sistema LTI  
Para acceder de forma segura a las funcionalidades del ATS

**Contexto:**  
Esta historia surge de la necesidad de autenticación básica para proteger el acceso al sistema, como se describe en las precondiciones de los casos de uso principales del PRD.

**Criterios de aceptación (Gherkin):**

  Escenario: Autenticación exitosa
    Dado que soy un reclutador registrado
    Cuando ingreso mis credenciales válidas (email y contraseña)
    Entonces soy autenticado y accedo al panel principal

  Escenario: Autenticación fallida por credenciales incorrectas
    Dado que soy un usuario no registrado o con credenciales inválidas
    Cuando intento autenticarme
    Entonces recibo un mensaje de error y no accedo al sistema

**Estimación de complejidad:** Small

**Definición de Completado (DoD):**  
- Endpoint de login implementado
- Validación de credenciales contra base de datos
- Sesión de usuario creada
- Pruebas unitarias y de integración pasan

## Caso de Uso 1: Creación de Ofertas de Empleo

**ID:** US-002

**Historia:**  
Como reclutador  
Quiero crear una nueva oferta de empleo con campos básicos  
Para definir perfiles de puestos de manera estructurada

**Contexto:**  
Esta historia se deriva del Caso de Uso 1 del PRD, permitiendo a los reclutadores definir ofertas con título, descripción, requisitos, salario y ubicación, utilizando la entidad JOB_POST.

**Criterios de aceptación (Gherkin):**

  Escenario: Creación exitosa de oferta
    Dado que estoy autenticado como reclutador
    Cuando ingreso título, descripción, requisitos, salario y ubicación válidos
    Entonces la oferta se guarda con un ID único y confirmación de creación

  Escenario: Creación fallida por datos inválidos
    Dado que ingreso datos incompletos o inválidos
    Cuando intento guardar la oferta
    Entonces recibo errores de validación y la oferta no se guarda

**Estimación de complejidad:** Small

**Definición de Completado (DoD):**  
- Formulario de creación implementado
- Validación de campos obligatorios
- Persistencia en entidad JOB_POST
- Pruebas de aceptación pasan

**ID:** US-003

**Historia:**  
Como reclutador  
Quiero usar plantillas predefinidas para ofertas  
Para acelerar el proceso de creación y asegurar consistencia

**Contexto:**  
Basado en el Caso de Uso 1, esta historia incluye plantillas para facilitar la creación, reduciendo tiempo manual.

**Criterios de aceptación (Gherkin):**

  Escenario: Selección y uso de plantilla
    Dado que hay plantillas disponibles
    Cuando selecciono una plantilla y la personalizo
    Entonces la oferta se crea con los campos prellenados

  Escenario: Creación sin plantilla
    Dado que no uso plantilla
    Cuando creo una oferta desde cero
    Entonces funciona igual que con plantilla

**Estimación de complejidad:** Small

**Definición de Completado (DoD):**  
- Plantillas definidas en sistema
- Opción de selección en UI
- Campos prellenados correctamente
- Pruebas unitarias pasan

## Caso de Uso 2: Publicación en Portales de Empleo, Sitios Web y Redes Sociales

**ID:** US-004

**Historia:**  
Como reclutador  
Quiero seleccionar canales para publicar una oferta  
Para elegir dónde distribuir la oferta

**Contexto:**  
Del Caso de Uso 2, permite elegir canales como LinkedIn, Indeed, sitio web, redes sociales, utilizando entidades PUBLICATION_CHANNEL y JOB_PUBLICATION.

**Criterios de aceptación (Gherkin):**

  Escenario: Selección de canales
    Dado que tengo una oferta creada
    Cuando selecciono canales disponibles
    Entonces los canales se marcan para publicación

  Escenario: Sin canales seleccionados
    Dado que no selecciono canales
    Cuando intento publicar
    Entonces recibo error indicando necesidad de selección

**Estimación de complejidad:** Small

**Definición de Completado (DoD):**  
- Lista de canales configurados
- UI para selección múltiple
- Validación de al menos un canal
- Pruebas de UI pasan

**ID:** US-005

**Historia:**  
Como reclutador  
Quiero publicar automáticamente en canales seleccionados  
Para maximizar alcance sin esfuerzo manual

**Contexto:**  
Automatiza la distribución, integrando con APIs de portales, actualizando estado en JOB_PUBLICATION.

**Criterios de aceptación (Gherkin):**

  Escenario: Publicación exitosa
    Dado que canales están configurados y válidos
    Cuando confirmo publicación
    Entonces la oferta se publica en todos canales y estado se actualiza

  Escenario: Fallo en publicación por credenciales inválidas
    Dado que credenciales de canal son inválidas
    Cuando intento publicar
    Entonces recibo error y publicación se cancela

**Estimación de complejidad:** Medium

**Definición de Completado (DoD):**  
- Integración con APIs simuladas
- Actualización de estado en base de datos
- Notificación de éxito/error
- Pruebas de integración pasan

## Caso de Uso 3: Recepción de Solicitudes de Empleo

**ID:** US-006

**Historia:**  
Como candidato  
Quiero enviar mi solicitud a través de formulario  
Para aplicar a una oferta publicada

**Contexto:**  
Del Caso de Uso 3, centraliza solicitudes en APPLICATION, asociada a CANDIDATE y JOB_POST.

**Criterios de aceptación (Gherkin):**

  Escenario: Envío exitoso de solicitud
    Dado que la oferta está activa
    Cuando ingreso datos personales, currículo y carta, y envío
    Entonces la solicitud se recibe y se confirma envío

  Escenario: Envío fallido por oferta inactiva
    Dado que la oferta no está activa
    Cuando intento enviar
    Entonces recibo error y no se procesa

**Estimación de complejidad:** Small

**Definición de Completado (DoD):**  
- Formulario público implementado
- Validación de campos
- Creación de APPLICATION
- Pruebas de formulario pasan

**ID:** US-007

**Historia:**  
Como sistema  
Quiero parsear automáticamente el currículo del candidato  
Para extraer datos clave como experiencia y habilidades

**Contexto:**  
Incluye parsing automático con IA, extrayendo experiencia, habilidades, almacenando en CANDIDATE y APPLICATION.

**Criterios de aceptación (Gherkin):**

  Escenario: Parsing exitoso
    Dado que recibo un currículo válido
    Cuando proceso automáticamente
    Entonces extraigo experiencia, habilidades y almaceno

  Escenario: Parsing fallido por formato inválido
    Dado que el currículo tiene formato no soportado
    Cuando intento parsear
    Entonces marco como pendiente manual y notifico

**Estimación de complejidad:** Medium

**Definición de Completado (DoD):**  
- Servicio de parsing implementado
- Extracción de atributos clave
- Manejo de errores
- Pruebas con datos de muestra pasan

# Product Backlog

# Prompt 1: Backlog Priorizado de User Stories para LTI

Dadas las User Stories definidas en @file:UserStories-XVB.md  y genera un backlog de tareas priorizandolas en basa a: criterio de impacto en el usuario y valor a negocio, complejidad y esfuerzo, riesgo y dependencias. Genera la salida en el fichero baclogPriorizado con titulo Prompt 1

## Criterios de Priorización
- **Impacto en el usuario y valor a negocio**: Historias que habilitan funcionalidades críticas para el flujo de reclutamiento, mejoran la experiencia del usuario y generan valor inmediato (e.g., autenticación como base, creación de ofertas para iniciar el proceso, recepción para cerrar el loop).
- **Complejidad y esfuerzo**: Historias Small requieren menos tiempo y recursos; Medium más.
- **Riesgo y dependencias**: Historias con integraciones externas tienen mayor riesgo; dependencias como autenticación deben ir primero.

## Backlog Priorizado

### Prioridad Alta (Debe hacerse primero - Alto impacto, bajo riesgo, dependencias críticas)
1. **US-001: Autenticación de usuario**  
   - **Impacto/Valor**: Crítico para seguridad y acceso; sin ella, ninguna funcionalidad es usable.  
   - **Complejidad**: Small.  
   - **Riesgo/Dependencias**: Bajo riesgo; dependencia para todas las demás historias.  
   - **Justificación**: Base del sistema; alto valor negocio al proteger datos.

2. **US-002: Creación de ofertas básicas**  
   - **Impacto/Valor**: Alto; inicia el proceso de reclutamiento, valor directo para reclutadores.  
   - **Complejidad**: Small.  
   - **Riesgo/Dependencias**: Bajo riesgo; depende de autenticación.  
   - **Justificación**: Esencial para el flujo principal; bajo esfuerzo.

3. **US-006: Envío de solicitud por candidato**  
   - **Impacto/Valor**: Alto; permite a candidatos aplicar, cerrando el loop del ATS.  
   - **Complejidad**: Small.  
   - **Riesgo/Dependencias**: Bajo riesgo; independiente de otras.  
   - **Justificación**: Impacto en usuario final (candidatos); valor negocio al atraer aplicaciones.

### Prioridad Media (Importante pero no crítico - Impacto moderado, mayor complejidad o riesgo)
4. **US-003: Uso de plantillas para ofertas**  
   - **Impacto/Valor**: Medio; acelera creación, mejora consistencia.  
   - **Complejidad**: Small.  
   - **Riesgo/Dependencias**: Bajo riesgo; depende de US-002.  
   - **Justificación**: Mejora eficiencia, pero no esencial para MVP básico.

5. **US-004: Selección de canales para publicación**  
   - **Impacto/Valor**: Medio; prepara para distribución.  
   - **Complejidad**: Small.  
   - **Riesgo/Dependencias**: Bajo riesgo; depende de US-002.  
   - **Justificación**: Paso intermedio; valor al permitir elección, pero no publicación aún.

6. **US-007: Parsing automático de currículos**  
   - **Impacto/Valor**: Medio; automatiza extracción de datos, valor para revisión.  
   - **Complejidad**: Medium.  
   - **Riesgo/Dependencias**: Medio riesgo (IA/parsing); depende de US-006.  
   - **Justificación**: Complejidad media; riesgo por tecnología externa.

### Prioridad Baja (Puede posponerse - Bajo impacto inmediato, alto riesgo o complejidad)
7. **US-005: Publicación automática en canales**  
   - **Impacto/Valor**: Alto potencial, pero bajo inmediato sin canales configurados.  
   - **Complejidad**: Medium.  
   - **Riesgo/Dependencias**: Alto riesgo (integraciones APIs); depende de US-004.  
   - **Justificación**: Mayor esfuerzo y riesgo; posponer para validar base primero.

# Prompt 2 - Generar Product Backlog.

Actúa como un Product Manager con amplia experiencia en metodologías ágiles y definición de producto orientado a MVP.

Analiza las User Stories definidas en @file:UserStories-XVB.md  Genera un Product Backlog listo para desarrollo en formato tabla. Para cada entrada, justifica brevemente por qué es prioritaria según la visión del PRD del ATS -LTI https://github.com/xavierventeo/AI4Devs-design-1-2026-03_srII/blob/LTI-XVB/LTI-XVB/LTI-XVB.md

| ID | Título | Prioridad | Estimación | Justificación |
|----|--------|-----------|------------|--------------|
| US-001 | Autenticación de usuario | Alta | Small | Base del sistema para seguridad y acceso, alineado con precondiciones de casos de uso en PRD, esencial para proteger datos en startups. |
| US-002 | Creación de ofertas básicas | Alta | Small | Inicia el proceso de reclutamiento, valor directo para reclutadores, reduce tiempo manual como en Caso de Uso 1 del PRD. |
| US-006 | Envío de solicitud por candidato | Alta | Small | Cierra el loop del ATS, centraliza aplicaciones, mejora organización según Caso de Uso 3, alto impacto en candidatos. |
| US-003 | Uso de plantillas para ofertas | Media | Small | Acelera creación y asegura consistencia, mejora eficiencia en startups, pero no crítico para MVP básico. |
| US-004 | Selección de canales para publicación | Media | Small | Prepara distribución automatizada, maximiza alcance sin esfuerzo manual, alineado con Caso de Uso 2. |
| US-007 | Parsing automático de currículos | Media | Medium | Automatiza extracción con IA, reduce sesgos y acelera evaluación, valor competitivo en PRD, pero complejidad media. |
| US-005 | Publicación automática en canales | Baja | Medium | Integra APIs para distribución simultánea, alto riesgo por dependencias externas, posponer para validar base primero según visión lean. |

# Prompt 3 - Generar Backlog de Tareas Priorizado en Tabla.

Dadas las User Stories definidas en @file:UserStories-XVB.md  y genera un backlog de tareas priorizandolas en formato tabla en basa a: criterio de impacto en el usuario y valor a negocio, complejidad y esfuerzo, riesgo y dependencias. Genera la salida en el fichero @file:backlogPriorizado.md  con titulo Prompt 3

| ID | Título | Prioridad | Impacto/Valor | Complejidad | Riesgo/Dependencias | Justificación |
|----|--------|-----------|---------------|-------------|---------------------|--------------|
| US-001 | Autenticación de usuario | Alta | Crítico para seguridad y acceso; sin ella, ninguna funcionalidad es usable. | Small | Bajo riesgo; dependencia para todas las demás historias. | Base del sistema; alto valor negocio al proteger datos. |
| US-002 | Creación de ofertas básicas | Alta | Alto; inicia el proceso de reclutamiento, valor directo para reclutadores. | Small | Bajo riesgo; depende de autenticación. | Esencial para el flujo principal; bajo esfuerzo. |
| US-006 | Envío de solicitud por candidato | Alta | Alto; permite a candidatos aplicar, cerrando el loop del ATS. | Small | Bajo riesgo; independiente de otras. | Impacto en usuario final (candidatos); valor negocio al atraer aplicaciones. |
| US-003 | Uso de plantillas para ofertas | Media | Medio; acelera creación, mejora consistencia. | Small | Bajo riesgo; depende de US-002. | Mejora eficiencia, pero no esencial para MVP básico. |
| US-004 | Selección de canales para publicación | Media | Medio; prepara para distribución. | Small | Bajo riesgo; depende de US-002. | Paso intermedio; valor al permitir elección, pero no publicación aún. |
| US-007 | Parsing automático de currículos | Media | Medio; automatiza extracción de datos, valor para revisión. | Medium | Medio riesgo (IA/parsing); depende de US-006. | Complejidad media; riesgo por tecnología externa. |
| US-005 | Publicación automática en canales | Baja | Alto potencial, pero bajo inmediato sin canales configurados. | Medium | Alto riesgo (integraciones APIs); depende de US-004. | Mayor esfuerzo y riesgo; posponer para validar base primero. |