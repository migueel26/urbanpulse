ADR-001: Modelo de base de datos utilizando PostgreSQL

### Estado
Proposed

### Contexto
Se necesita almacenar todos los datos necesarios para la aplicación: desde incidencias hasta usuarios o distritos.

### Opciones consideradas
1. Supabase (BaaS)
2. Docker

### Decisión
Utilizar un archivo **docker-compose** con persistencia de datos.

### Consecuencias
+ Facilidad de implementación
+ Offline
+ Gratuito

- Más complicado de centralizar
- Gasta recursos locales
