# UrbanPulse - Requisitos del sistema

## 1. Actores

| Actor | Descripción |
|---|---|
| Ciudadano | Registra incidencias y consulta el estado de sus propios reportes. |
| Operador | Revisa, valida, prioriza y asigna las incidencias. |
| Técnico | Atiende las incidencias asignadas y actualiza su progreso y resolución. |
| Administrador | Gestiona usuarios, roles, permisos y la configuración general de la plataforma. |

## 2. Requisitos funcionales

| ID | Actor principal | Requisito | Descripción |
|---|---|---|---|
| RF01 | Todos | Identidad y acceso | El sistema permitirá registrar cuentas, iniciar y cerrar sesión, recuperar el acceso y autenticar al personal autorizado. |
| RF02 | Administrador | Roles y permisos | El sistema aplicará permisos diferenciados para ciudadanos, operadores, técnicos, analistas y administradores. |
| RF03 | Ciudadano | Registrar incidencia | El ciudadano podrá registrar una incidencia indicando título, descripción, ubicación y categoría opcional. |
| RF04 | Ciudadano | Localización | La incidencia conservará coordenadas, dirección normalizada y precisión de la localización cuando estén disponibles. |
| RF05 | Ciudadano, operador, técnico | Evidencias | El sistema permitirá adjuntar fotografías u otros ficheros, validando su tipo, tamaño y relación con la incidencia. |
| RF06 | Ciudadano | Consulta y seguimiento | El ciudadano podrá consultar el detalle, estado, fechas, comentarios e historial visible de sus incidencias. |
| RF07 | Operador, Ténico | Búsqueda | El personal autorizado podrá buscar y filtrar incidencias por estado, categoría, fecha, prioridad, distrito y departamento. |
| RF08 | Todos | Mapa | El sistema mostrará las incidencias y las capas urbanas relevantes sobre un mapa, respetando los permisos de visibilidad. |
| RF09 | Operador | Validación | El operador podrá validar una incidencia, solicitar información adicional o rechazarla indicando el motivo. |
| RF10 | Operador | Prioridad | El sistema permitirá establecer una prioridad manual o asistida y conservará la justificación y el responsable de la decisión. |
| RF11 | Operador | Asignación | Una incidencia validada podrá asignarse a un departamento, equipo o técnico, registrando la fecha y el responsable de la asignación. |
| RF12 | Operador, técnico | Ciclo de vida | Los cambios de estado respetarán las transiciones permitidas y quedarán registrados en el historial de la incidencia. |
| RF13 | Operador, técnico | Colaboración | Operadores y técnicos podrán añadir comentarios, evidencias y datos de resolución a una incidencia. |
| RF14 | Sistema | Notificaciones | El sistema notificará los cambios relevantes mediante canales configurables según el tipo de usuario. |
| RF15 | Operador | Duplicados | El sistema podrá sugerir incidencias similares considerando proximidad, fecha y similitud semántica. |
| RF16 | Operario |Análisis zonal | Se podrán consultar incidencias y contexto agregado para una zona y periodo.|
| RF17 | Sistema | Auditoría | El sistema registrará acciones administrativas, decisiones asistidas y cambios relevantes, con su fecha, usuario y resultado. |
| RF18 | Sistema | Barrio y distrito | El sistema identificará el barrio y el distrito correspondientes a partir de la localización de la incidencia. |
| RF19 | Sistema | Activo urbano | El sistema podrá asociar una incidencia al activo urbano más próximo cuando exista información disponible. |
| RF20 | Sistema | Contexto externo | El sistema podrá obtener información contextual procedente de fuentes externas autorizadas. |
| RF21 | Operador | Vista contextual | El operador podrá visualizar el contexto urbano asociado a una incidencia. |
| RF23 | Ciudadano | Degradación controlada | La falta de disponibilidad de una fuente externa no impedirá al ciudadano crear una incidencia. |


## 3. Requisitos no funcionales

Los siguientes requisitos son objetivos iniciales de aceptación. Deberán confirmarse con el equipo antes de convertirlos en compromisos de nivel de servicio.


| ID | Categoría | Requisito | Criterio verificable |
|---|---|---|---|
| RNF01 | Rendimiento | Las operaciones habituales deberán responder con rapidez. | El 95 % de las consultas de listado, detalle y actualización responderá en menos de 2 segundos bajo la carga prevista; las búsquedas cartográficas responderán en menos de 3 segundos. 
| RNF02 | Escalabilidad | Los componentes podrán escalar horizontalmente cuando aumente la demanda. | La aplicación permitirá añadir instancias sin modificar el código y mantendrá el servicio durante el escalado. 
| RNF03 | Disponibilidad | El servicio estará disponible las 24 horas del día. | Disponibilidad mensual mínima del 99,5 %, excluyendo mantenimientos planificados y comunicados. 
| RNF04 | Fiabilidad | El sistema procesará correctamente las operaciones esperadas durante el tiempo de uso. | Al menos el 99,5 % de las operaciones críticas completará su resultado correctamente, sin pérdida ni duplicación de incidencias, durante las pruebas de aceptación y operación. 
| RNF05 | Capacidad | La plataforma soportará el crecimiento de usuarios e incidencias. | Soportará al menos 500 usuarios concurrentes y 100.000 incidencias almacenadas sin incumplir RNF01. 
| RNF06 | Resiliencia | El sistema continuará ofreciendo las funciones esenciales cuando falle un componente no crítico. | Ante la caída de una fuente externa o una instancia, la incidencia podrá crearse y los servicios afectados mostrarán un estado degradado; las peticiones a servicios recuperables usarán reintentos limitados y tiempo de espera. 
| RNF07 | Seguridad | El acceso a datos y funciones se controlará mediante autenticación y autorización. | Todas las operaciones protegidas exigirán autenticación; el servidor verificará permisos por rol y no confiará en controles realizados solo en el cliente. 
| RNF08 | Seguridad | Las comunicaciones y credenciales estarán protegidas. | Todo tráfico usará HTTPS/TLS; las contraseñas se almacenarán mediante un algoritmo de hashing resistente y nunca en texto plano.
| RNF09 | Privacidad | El tratamiento de datos personales respetará la normativa aplicable. | Se recogerán únicamente los datos necesarios, se informará de su finalidad, se permitirá solicitar su eliminación cuando proceda y se limitará el acceso a la localización y evidencias. 
| RNF10 | Mantenibilidad | El código será modular, documentado y verificable. | La lógica de negocio estará separada de la presentación y persistencia; las funcionalidades críticas tendrán pruebas automatizadas y revisión de código. 
| RNF11 | Observabilidad | El equipo podrá detectar y diagnosticar fallos. | Se registrarán errores, latencias, disponibilidad y métricas de recursos con correlación por petición. 
| RNF12 | Interoperabilidad | El sistema podrá integrarse con servicios municipales autorizados. | Expondrá una API documentada mediante OpenAPI, usará formatos JSON |
| RNF13 | Compatibilidad | La aplicación funcionará en los entornos habituales. | Será compatible con navegadores habituales (Chrome, Edge, Firefox y Safari), y con dispositivos Android e IOS. 
| RNF14 | Trazabilidad | Los datos de una incidencia conservarán un seguimiento. | El ciclo de vida de las incidencias tendrá una trazabilidad inmutable, conservando fechas de modificación, autor y personal que haya gestionado la incidencia. 
| RNF15 | Usabilidad | Los flujos principales serán comprensibles para usuarios no técnicos. | Un ciudadano podrá crear un reporte y consultar su estado sin asistencia; los formularios mostrarán validaciones y mensajes de error claros. 
| RNF16 | Accesibilidad | La interfaz será accesible para personas con diversidad funcional. | La aplicación cumplirá WCAG 2.1 nivel AA en navegación por teclado, contraste, foco, formularios, textos alternativos y avisos de estado.
| RNF17 | Coste | El coste de operación se mantendrá dentro del presupuesto aprobado. | El sistema registrará mensualmente el consumo de infraestructura y servicios externos, emitirá una alerta al alcanzar el 80 % del presupuesto y permitirá identificar el coste por entorno.


## 4. Prioridad.

### Matriz de Priorización (Importancia vs. Facilidad)

| | **BAJA FACILIDAD**  | **ALTA FACILIDAD**  |
|:---|:---|:---|
| **ALTA IMPORTANCIA** |  |  |
| **BAJA IMPORTANCIA** |  |  |
