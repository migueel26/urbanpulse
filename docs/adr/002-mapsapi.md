ADR-002: API de Geolocalización

### Estado
Proposed

### Contexto
Las incidencias de la ciudad deben estar bien localizadas. Para ello es necesario un *map-database*.

### Opciones consideradas
1. OpenStreetMap
2. OpenCage
3. LocationIQ

### Decisión
Hemos elegido **OpenCage**, API de geocodificación global basada en datos abiertos que permite convertir nombres de lugares o direcciones en coordenadas geográficas y viceversa. Ofrece compatibilidad y tutoriales para más de 40 lenguajes de programación.

### Consecuencias
+ Gratuito
+ JSONs estructurados
+ Datos fiables
+ Fácilmente integrable

- Menos peticiones diarias que otras alternativas