# Wireframes en Papel — Notas de Contenido

Este directorio contiene las fotografías de los wireframes de baja fidelidad dibujados a mano para las 5 vistas principales del SGA Universitario.

## Distribución de archivos

### `hoja1-login-dashboard-estudiante.jpeg`
Contiene 2 vistas:

**Vista 1 — Inicio / Login**
- Anotaciones de landmark: `<Header>` (logo SGA), `<Main>` (formulario), `<Footer>` (contacto, política, accesibilidad)
- Orden de tabulación numerado: 1. Login, 3. Correo, 4. Contraseña, 5. Recordar, 6. Iniciar sesión
- Nota funcional: "Según el rol logear" (redirección post-login según perfil)
- Nota de accesibilidad: "Señalar error" en el campo de contraseña

**Vista 2 — Dashboard Estudiante**
- Anotaciones de landmark: `<Header>` (saludo + datos del estudiante), `<Main>` (materias + calendario), `<Sidebar>`
- Nota funcional: "Mostrar materia" (las tarjetas de materia son interactivas)
- Nota funcional: "Organizar tareas en el calendario" (la grilla agrupa entregas por fecha)

### `hoja2-dashboard-profesor-admin.jpeg`
Contiene 2 vistas:

**Vista 3 — Dashboard Profesor**
- Sidebar: Home, Cursos, Calificaciones, Asistencias, Material, Horarios, Bandeja, Cerrar sesión
- Indicadores resumen: Cursos, Total estudiantes, Entregas
- Sección Acciones (3 botones de acción rápida)
- Tabla Estudiantes: Nombre, Curso, Estado
- Nota funcional: "Mostrar actividad" (el estado enlaza al detalle de la entrega)

**Vista 4 — Dashboard Administrador**
- Sidebar: Home, Users, Roles, Reportes, Configuración, Cerrar sesión
- Indicadores resumen: Total users, Activos, Reportes
- Sección Reporte con estado de carga ("cargando" + spinner)
- Tabla Gestión Users: Nombre, Correo, Rol, Estado
- Nota funcional: "Modificar rol" (edición de rol directamente desde la fila)

### `hoja3-editar-perfil.jpeg`
**Vista 5 — Módulo Editar Perfil (compartido para todos los roles)**
- Sidebar: Home, Materia, Horario, Calificaciones, Perfil, Cerrar sesión
- Sección Info: Nombre, Apellido, Correo, Teléfono, Ciudad
- Sección Accesibilidad: 3 checkboxes de preferencias
- Nota de diseño: única vista reutilizada entre los 3 roles, cambiando solo los ítems del sidebar (ver `/docs/decisiones.md`, sección 2.1)

---

## Elementos de accesibilidad documentados (criterio de la rúbrica)

| Elemento requerido | Vistas donde se anotó |
|---|---|
| Orden de tabulación numerado | Login |
| Skip link | Implícito en landmark `<Header>` de Login (saltar al `<Main>`) |
| Landmarks ARIA (header/main/footer/sidebar) | Login, Dashboard Estudiante |
| Breadcrumbs | Pendiente de anotación explícita — ver nota abajo |

