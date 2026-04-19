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