ADR-003: Utilización de una librería o framework que permite una aplicación multiplataforma

### Estado
Proposed

### Contexto
La aplicación necesita un frontend para que los usuarios interactúen y pueden notificar de las incidencias.

### Opciones consideradas
1. React Native (TS)
2. Kotlin Multiplatform
3. Flutter

### Decisión
El equipo tiene experiencia con React y JS, por lo que un *frontend* basado en **React Native**, utilizando TypeScript como lenguaje.

### Consecuencias
+ Experiencia con la librería
+ Nativo
+ Ecosistema de paquetes gigante

- Rendimiento inferior