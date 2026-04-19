# Prompt 1 - Generar las User Stories.

Actúa como un Product Manager con amplia experiencia en metodologías ágiles y definición de producto orientado a MVP.

Voy a darte el contexto de la siguiente definición de una aplicación ATS en https://github.com/xavierventeo/AI4Devs-design-1-2026-03_srII/blob/LTI-XVB/LTI-XVB/LTI-XVB.md. y que conforma un PRD básico (funcionalidades clave, casos de uso, modelo de datos...)

Tu objetivo es generar las User Stories para los 3 casos de uso principales:
- Caso de Uso 1: Creación de Ofertas de Empleo
- Caso de Uso 2: Publicación en Portales de Empleo, Sitios Web y Redes Sociales
- Caso de Uso 3: Recepción de Solicitudes de Empleo
Y las especificaciones mínimas de infraestructura para poner en marcha el MVP como la autenticación de usuario.

Las User Stories deben:

- Cumplir estrictamente los criterios INVEST
- Ser pequeñas, implementables y enfocadas a MVP
- Ser trazables directamente al contexto proporcionado
- NO inventen funcionalidades fuera del alcance descrito
- NO mezclen múltiples capacidades grandes en una misma historia
- Los criterios de aceptación deben contener tanto el escenario principal como escenarios alternativos como errores
- Tienen una primera estimación de complejidad
- En la descripción incluye los detalles que le correspondan y estén indicados en el caso de uso de la que está asociada e incluya las entidades y atributos que debe manejar

Para cada User Story, usa EXACTAMENTE la estructura de la siguiente plantilla: #file:UserStory-template.md 

El formato de salida es un fichero markdown UserStories-XVB.md con el contenido de las User Stories.

# Prompts 2 - Product Backlog

## Prompt 2.1: 
Dadas las User Stories definidas en @file:UserStories-XVB.md  y genera un backlog de tareas priorizandolas en basa a: criterio de impacto en el usuario y valor a negocio, complejidad y esfuerzo, riesgo y dependencias. 
Genera la salida en el fichero @file:backlogPriorizado.md con titulo Prompt 1

## Prompt 2.2:
Actúa como un Product Manager con amplia experiencia en metodologías ágiles y definición de producto orientado a MVP.

Analiza las User Stories definidas en @file:UserStories-XVB.md  Genera un Product Backlog listo para desarrollo en formato tabla. Para cada entrada, justifica brevemente por qué es prioritaria según la visión del PRD del ATS -LTI https://github.com/xavierventeo/AI4Devs-design-1-2026-03_srII/blob/LTI-XVB/LTI-XVB/LTI-XVB.md
Genera la salida en el fichero @file:backlogPriorizado.md con titulo Prompt 2

## Prompt 2.3 (Ganador):
Dadas las User Stories definidas en @file:UserStories-XVB.md  y genera un backlog de tareas priorizandolas en formato tabla en basa a: criterio de impacto en el usuario y valor a negocio, complejidad y esfuerzo, riesgo y dependencias. Genera la salida en el fichero @file:backlogPriorizado.md con titulo Prompt 3

## Explicación prompt con mejores resultados Prompt 2.3:
Tanto el prompt 2.1 como el 2.3 ofrecen mejores resultados, ya que especifican claramente los criterios de aceptación. En cambio, el prompt 2.2 deja mayor libertad al modelo para basarse en los objetivos del proyecto, lo que da lugar a respuestas más verbosas pero menos detalladas y precisas.

Finalmente, el prompt 2.3 es funcionalmente equivalente al 2.1; sin embargo, el uso de un formato en tabla mejora la claridad y facilita la visualización de la información. Además de dar una explicación de los criterios de priorización

Me llamó la atención que el promnpt 2.1 y 2.3 no le indiqué el rol y pareció funcionar mejor al especificar los criterios que no tanto el darle un rol.


# Prompt 3 - Desglosar "US-002 - Creación de ofertas básicas" en tareas
Actúa como un Technical Lead. Tu objetivo es desglosar la User Story "US-002 - Creación de ofertas básicas" en Tickets de Trabajo técnicos, granulares y listos para ser desarrollados en un Sprint.

Para cada ticket, utiliza estrictamente la siguiente estructura basada en las mejores prácticas de gestión de proyectos:

- ID del Ticket:
- Título: Un resumen breve que refleje la esencia de la tarea. Debe ser lo suficientemente descriptivo para que cualquier miembro del equipo entienda rápidamente de qué se trata el ticket.

- Descripción: 
  - Propósito: Explicación de por qué es necesaria la tarea y qué problema resuelve.
  - Detalles Específicos: Información adicional sobre requerimientos específicos, restricciones, o condiciones necesarias para la realización de la tarea.
Criterios de Aceptación: Lista de condiciones Checklist que deben cumplirse y pasos de validación.
  - Expectativas Claras: Lista detallada de condiciones que deben cumplirse para que el trabajo en el ticket se considere completado.
  - Pruebas de Validación: Pasos o pruebas específicas que se deben realizar para verificar que la tarea se ha completado correctamente.
- Prioridad: (Alta, Media, Baja).
- Estimación: En puntos de historia (serie de Fibonacci: 1, 2, 3, 5, 8).
- Asignación Sugerida: (Backend, Frontend, QA, o DevOps).
- Etiquetas/Tags: (Ej: UI, API, Database, Seguridad, Sprint).
- Comentarios/Notas: Advertencias técnicas o dependencias con otros tickets.
- Enlaces/Referencias: Referencia al PRD de LTI o documentación de APIs externas.
- Instrucción adicional: Asegúrate de que los tickets cubran tanto la lógica de negocio como la gestión de errores y la persistencia de datos

El resultado generalo en formato tabla y añadelo al contenido de @file:UserStories-XVB.md 
