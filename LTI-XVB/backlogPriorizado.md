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
| US-005 | Publicación automática en canales | Baja | Alto potencial, pero bajo inmediato sin canales configurados. | Medium | Alto riesgo (integraciones APIs); depende de US-004. | Mayor esfuerzo y riesgo; posponer para validar base primero. |</content>
