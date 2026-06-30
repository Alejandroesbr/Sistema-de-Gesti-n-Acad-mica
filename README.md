# SGA Universitario — SPA Accesible

Diseño de interfaz y modelo de navegación para una Aplicación de Página Única (SPA) de Sistema de Gestión Académica (SGA), desarrollado bajo los principios de las Pautas de Accesibilidad para el Contenido Web (WCAG 2.2 nivel AA).

**Autor:** Alejandro Escobar
**Universidad:** Universidad Manuela Beltrán
**Actividad:** Diseño de Interfaz y Modelo de Navegación para SPA Accesible

---

## Descripción del proyecto

El SGA Universitario permite que tres tipos de usuario — Estudiante, Profesor y Administrador — gestionen información académica (cursos, calificaciones, asistencias, perfiles y reportes) mediante una interfaz diseñada específicamente considerando necesidades de accesibilidad diversas:

| Persona | Rol | Necesidad de accesibilidad |
|---|---|---|
| Alejandro Escobar | Estudiante | Discapacidad visual — uso de lector de pantalla y zoom de navegador |
| Carlos Mendoza / Juan José Osorio | Profesor | Limitación motora — navegación exclusiva por teclado |
| Jorge Tamayo | Administrador | Conexión a internet inestable / dispositivo de gama baja |

Cada dashboard refleja visualmente las implicaciones de diseño correspondientes a la necesidad de su persona (ver `/docs/decisiones.md` para el detalle de cada decisión).

---

## Enlace de diseño en Figma

🔗 **Figma (share link):** *(https://www.figma.com/design/xnEp9or2IappHxIyc3Np93/SGA_Universitario?node-id=0-1&t=h9F3AGncSbe5JESv-1)]*

---

## Estructura del repositorio

```
/
├── README.md
├── /wireframes
│   ├── hoja1-login-dashboard-estudiante.jpeg
│   ├── hoja2-dashboard-profesor-admin.jpeg
│   ├── hoja3-editar-perfil.jpeg
│   └── notas-wireframes.md
│
├── /design
│   ├── especificaciones-pantallas.pdf
│   └── SGA_Universitario.fig
│
├── /docs
│   ├── decisiones.md
│   ├── diagramas.puml
│   └── guia-estilos.md
│
└── /demo
    └── demo-sga-accesibilidad.mp4 
```

## Resumen de contenido por carpeta

### `/wireframes`
Fotografías de los 5 wireframes de baja fidelidad dibujados en papel (Login, Dashboard Estudiante, Dashboard Profesor, Dashboard Administrador, Editar Perfil), con anotaciones de orden de tabulación y landmarks (header, main, footer, sidebar). Ver `notas-wireframes.md` para el detalle de cada hoja y los pendientes de validación.

### `/design`
PDF con las 5 pantallas exportadas desde Figma, mostrando componentes, colores y textos reales del sistema.

### `/docs`
- **decisiones.md** — racional de cada decisión de diseño, conectado a principios SWEBOK (abstracción, modularidad, separación de responsabilidades, bajo acoplamiento, alta cohesión) y a criterios WCAG 2.2 AA específicos.
- **diagramas.puml** — diagrama de componentes y diagrama de navegación en formato PlantUML.
- **guia-estilos.md** — paleta de colores con códigos hex y contraste verificado, tipografía, espaciado y especificación de componentes reutilizables.

### `/demo`
Carpeta con el video final de 5 a 7 minutos con voz en off explicando el flujo de navegación entre los 3 roles y las decisiones de accesibilidad tomadas en cada vista.

---

## Herramientas utilizadas

- **Figma** — modelado digital de interfaz
- **PlantUML** — diagramas de componentes y navegación
- **axe DevTools / Lighthouse / WAVE** — validación de accesibilidad

## Material de referencia

Vega, M., & García, J. (2022). Building accessible single-page applications: Best practices and challenges. *Journal of Web Engineering*, 21(3), 245–263.
