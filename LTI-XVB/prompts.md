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





