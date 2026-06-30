# Decisiones de Diseño — Sistema de Gestión Académica (SGA)

## 1. Introducción

Este documento registra el racional de las decisiones de diseño tomadas durante el desarrollo de la interfaz y el modelo de navegación del SGA, conectando cada decisión con los principios de diseño de software (SWEBOK), patrones aplicados y cualidades de software gestionadas (accesibilidad, usabilidad, modificabilidad, interoperabilidad).

Las decisiones se organizan por componente y por vista, siguiendo la matriz de roles definida en el caso de estudio: Estudiante, Profesor, Administrador y Visitante.

---

## 2. Decisiones Globales del Sistema

### 2.1. Sidebar de navegación dinámico por rol

**Decisión:** un único componente de navegación lateral (`Sidebar`) que renderiza distintos ítems de menú según el rol autenticado, en lugar de crear un sidebar independiente por rol.

**Principio SWEBOK:** abstracción y alta cohesión — el componente encapsula la lógica de "qué mostrar" detrás de una sola responsabilidad (renderizar navegación), delegando el contenido específico a una estructura de datos (`NAV_ITEMS: Record<Rol, Item[]>`).

**Patrón aplicado:** Strategy simplificado — el comportamiento de renderizado cambia según el "tipo" (rol) sin duplicar el componente.

**Cualidad gestionada:** modificabilidad. Agregar un nuevo ítem de menú para un rol no requiere tocar el componente, solo la tabla de datos.

---

### 2.2. Indicador de foco visible global

**Decisión:** se define un estilo de foco global (`outline` de 3px en color primario) aplicado a todos los elementos interactivos del sistema, en lugar de estilos de foco particulares por componente.

**Principio SWEBOK:** separación de responsabilidades — la accesibilidad de navegación por teclado se centraliza en una sola hoja de estilos, no se repite en cada componente.

**Cualidad gestionada:** accesibilidad (WCAG 2.2 AA — criterio 2.4.7 Focus Visible) y modificabilidad (cambiar el color de foco en todo el sistema requiere editar un único punto).

**Relación con el rol Profesor:** este criterio responde directamente a la necesidad de accesibilidad de Carlos Mendoza (navegación exclusiva por teclado), garantizando que en cualquier vista del sistema sea visualmente claro qué elemento tiene el foco activo.

---

### 2.3. Componentes reutilizables (botón, input, card, tabla)

**Decisión:** se definieron componentes base (botón primario/secundario, input con label y mensaje de error, card de materia/curso, tabla de datos) reutilizados en las 5 vistas, en lugar de maquetar cada pantalla de forma independiente.

**Principio SWEBOK:** modularidad y abstracción — cada componente expone una interfaz simple (props) y oculta su implementación visual interna.

**Cualidad gestionada:** modificabilidad e interoperabilidad. Un cambio de estilo en el componente botón se refleja automáticamente en las 5 vistas sin edición manual repetida.

---

## 3. Decisiones por Vista

### 3.1. Login

**Decisión:** validación de formulario con mensajes de error asociados mediante `aria-describedby` y anunciados con `role="alert"`, en vez de solo cambiar el color del borde del input.

**Principio SWEBOK:** comprensibilidad (atributo de calidad ISO 25010 relacionado).

**Cualidad gestionada:** accesibilidad (WCAG 2.2 AA — 3.3.1 Error Identification). El color por sí solo no es suficiente señal de error (WCAG 1.4.1 Use of Color), por lo que cada error de validación se acompaña de texto explicativo.

**Relación con el rol Estudiante:** un usuario con baja visión que no perciba el cambio de color del borde aún recibe el mensaje de error mediante el lector de pantalla.

---

### 3.2. Dashboard Estudiante

**Decisión:** tipografía de cuerpo a 18px (en vez de los 16px estándar del resto del sistema) y bordes de 2px en cards y tablas.

**Principio SWEBOK:** la decisión prioriza la cualidad de **usabilidad** para un segmento específico de usuario por encima de la consistencia visual estricta.

**Cualidad gestionada:** accesibilidad (WCAG 2.2 AA — 1.4.4 Resize Text / 1.4.3 Contrast Minimum). Responde directamente a la necesidad de María/Alejandro (persona con baja visión que usa zoom de navegador 150–200%): un cuerpo de texto más grande reduce la necesidad de zoom adicional y los bordes marcados delimitan claramente cada bloque de información sin depender solo de sombras sutiles.

**Patrón aplicado:** Progressbar accesible — la barra de progreso de cada materia usa `role="progressbar"` con `aria-valuenow/min/max`, exponiendo el valor a tecnologías de asistencia y no solo visualmente.

---

### 3.3. Dashboard Profesor

**Decisión:** áreas de clic con mínimo 44×44px en todos los botones y acciones rápidas, y un aviso visible de "navegación por teclado activa" en la parte superior de la vista.

**Principio SWEBOK:** la decisión aplica el principio de diseño centrado en el usuario, priorizando el área de interacción sobre la densidad de información en pantalla.

**Cualidad gestionada:** accesibilidad (WCAG 2.2 AA — 2.5.8 Target Size Minimum) y usabilidad. Responde a la necesidad de Carlos Mendoza (limitación motora): áreas de clic más grandes reducen el riesgo de error al activar un control, tanto con mouse impreciso como con switches de accesibilidad.

---

### 3.4. Dashboard Administrador

**Decisión:** sección de reportes con estado de carga explícito (spinner + texto "Cargando reportes...") implementado con `role="status"`, `aria-live="polite"` y `aria-busy="true"`, en lugar de mostrar la tabla vacía mientras carga.

**Principio SWEBOK:** robustez — el sistema comunica su estado interno (cargando / cargado / error) en vez de presentar un estado ambiguo.

**Cualidad gestionada:** accesibilidad (WCAG 2.2 AA — 4.1.3 Status Messages) y usabilidad. Responde a la necesidad de Jorge Tamayo (conexión inestable): el usuario recibe confirmación de que el sistema está trabajando, evitando que interprete una carga lenta como un fallo.

**Decisión complementaria:** diseño visualmente plano, sin gradientes ni sombras pesadas, priorizando menor peso de renderizado sobre estética decorativa — coherente con el objetivo de optimizar la experiencia en dispositivos de gama baja.

---

### 3.5. Editar Perfil

**Decisión:** agrupación de campos relacionados mediante `fieldset` y `legend` ("Información personal", "Preferencias de accesibilidad"), en vez de una lista plana de inputs.

**Principio SWEBOK:** alta cohesión — los campos que pertenecen al mismo concepto semántico se agrupan estructuralmente, no solo visualmente.

**Cualidad gestionada:** accesibilidad (WCAG 2.2 AA — 1.3.1 Info and Relationships). Un lector de pantalla anuncia el nombre del grupo (`legend`) antes de cada campo, dando contexto que el agrupamiento visual por sí solo no transmite a tecnologías de asistencia.

**Decisión adicional:** inclusión de preferencias de accesibilidad configurables por el propio usuario (alto contraste, texto grande, optimización para lector de pantalla) dentro del formulario de perfil.

**Cualidad gestionada:** usabilidad y personalización — se traslada parte del control de la experiencia accesible al usuario final, en vez de imponer una única configuración fija para todos los roles.

---

## 4. Resumen de Trazabilidad: Decisión → Principio → Cualidad

| Decisión | Principio SWEBOK | Cualidad gestionada | Criterio WCAG 2.2 AA |
|---|---|---|---|
| Sidebar dinámico por rol | Abstracción / alta cohesión | Modificabilidad | — |
| Foco visible global | Separación de responsabilidades | Accesibilidad / modificabilidad | 2.4.7 |
| Skip link | Bajo acoplamiento | Accesibilidad | 2.4.1 |
| Componentes reutilizables | Modularidad / abstracción | Modificabilidad / interoperabilidad | — |
| Errores de formulario con texto + rol alert | Comprensibilidad | Accesibilidad | 3.3.1, 1.4.1 |
| Tipografía 18px y bordes marcados (estudiante) | Diseño centrado en usuario | Accesibilidad / usabilidad | 1.4.3, 1.4.4 |
| Áreas de clic 44×44px (profesor) | Diseño centrado en usuario | Accesibilidad / usabilidad | 2.5.8 |
| Estado de carga explícito (administrador) | Robustez | Accesibilidad / usabilidad | 4.1.3 |
| Fieldset/legend en formulario de perfil | Alta cohesión | Accesibilidad | 1.3.1 |
| Preferencias de accesibilidad configurables | — | Usabilidad / personalización | — |

---

## 5. Conclusión

Las decisiones documentadas muestran una relación directa entre las necesidades de accesibilidad de cada persona definida (Alejandro, Juan José Osorio, Jorge Tamayo) y las soluciones de diseño implementadas en cada vista, evidenciando que el cumplimiento de WCAG 2.2 AA no se trató como una capa añadida al final, sino como criterio de diseño desde el análisis de requisitos.
