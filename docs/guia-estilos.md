# Guía de Estilos — SGA Universitario

## 1. Paleta de Colores

### Colores primarios

| Uso | Color | Código Hex | Contraste sobre blanco (#FFFFFF) |
|---|---|---|---|
| Primario (botones, links, foco) | Azul | `#2563EB` | 5.9:1  AA |
| Primario hover/activo | Azul oscuro | `#1D4ED8` | 7.2:1  AA |
| Texto principal | Casi negro | `#1A1A2E` | 16.1:1  AAA |
| Texto secundario | Gris medio | `#717182` | 4.6:1  AA |
| Fondo general | Gris muy claro | `#F8F9FA` | — |
| Fondo de tarjetas / inputs | Blanco | `#FFFFFF` | — |

### Colores de estado

| Estado | Color | Código Hex | Fondo asociado | Uso |
|---|---|---|---|---|
| Éxito | Verde | `#16A34A` | `#F0FDF4` | Confirmaciones, estado "Activo" / "Completada" |
| Advertencia | Naranja | `#D97706` | `#FFFBEB` | Estados "Pendiente", avisos de rendimiento |
| Error | Rojo | `#DC2626` | `#FEF2F2` | Validación de formularios, acciones destructivas |
| Información | Azul claro | `#1D4ED8` | `#EFF6FF` | Notas, estado "En progreso" |
| Inactivo / neutro | Gris | `#6B7280` | `#F8F9FA` | Estado "Inactivo", "Sin calificar" |

**Regla de accesibilidad aplicada (WCAG 2.2 AA — 1.4.1 Use of Color):** todo estado se identifica con color **y** texto simultáneamente (ej. badge verde con la palabra "Activo" dentro, no solo un punto de color). Ningún color se usa como única fuente de información.

### Colores por rol (identidad visual de cada dashboard)

| Rol | Color de acento | Código Hex |
|---|---|---|
| Estudiante | Azul | `#2563EB` |
| Profesor | Verde | `#16A34A` |
| Administrador | Naranja | `#D97706` |

---

## 2. Tipografía

**Familia tipográfica:** Inter (alternativa de sistema: -apple-system, Segoe UI, Roboto, sans-serif)

| Elemento | Tamaño | Peso | Uso |
|---|---|---|---|
| H1 (título de página) | 26–28px | 700 (Bold) | Títulos principales de cada vista |
| H2 (título de sección) | 20–22px | 700 (Bold) | Encabezados de sección dentro de una vista |
| H3 (subtítulo) | 17–18px | 600 (Semibold) | Títulos de tarjetas, nombres de materia/curso |
| Body estándar | 16px | 400 (Regular) | Texto de cuerpo general |
| Body ampliado (perfil Estudiante) | 18px | 400 (Regular) | Vistas optimizadas para baja visión (WCAG 1.4.4) |
| Texto secundario / metadatos | 13–14px | 400–500 | Fechas, descripciones cortas, ayudas de campo |
| Botones | 15–16px | 600 (Semibold) | Texto de botones primarios y secundarios |
| Etiquetas de formulario | 15–16px | 500–600 | Labels de inputs |

**Reglas de escalabilidad:** ningún tamaño de fuente del sistema es inferior a 13px. Todo el texto usa unidades relativas (rem/em en implementación final) para permitir el zoom del navegador sin romper el layout, requisito directo de la persona Estudiante (uso de zoom 150–200%).

---

## 3. Sistema de Espaciado

Espaciado base en múltiplos de 8px:

`4px · 8px · 12px · 16px · 20px · 24px · 32px · 40px · 48px`

| Contexto | Valor |
|---|---|
| Padding interno de tarjetas | 24px |
| Padding interno de inputs | 12px 16px |
| Separación entre secciones | 32–40px |
| Separación entre elementos de formulario | 16–20px |
| Gap entre tarjetas en grilla | 16–24px |

---

## 4. Componentes

### 4.1. Botón primario
- Fondo: `#2563EB` / Hover: `#1D4ED8`
- Texto: `#FFFFFF`, 16px, peso 600
- Border-radius: 8px
- Altura mínima: 52px (CTA principal) / 44px (acciones secundarias)
- Estado focus: outline 3px `#2563EB` con offset 2px

### 4.2. Botón secundario
- Fondo: transparente
- Borde: 1–2px `#1A1A2E` o color de marca
- Texto: color del borde, 16px, peso 600
- Mismas reglas de altura mínima y foco que el botón primario

### 4.3. Input de texto
- Borde: 1–2px `rgba(0,0,0,0.2)` (default) / `#DC2626` (error)
- Border-radius: 6–8px
- Altura mínima: 48px
- Label siempre visible arriba del campo, asociada vía `for`/`id`
- Mensaje de error en `#DC2626`, 13px, anunciado con `role="alert"`

### 4.4. Card (materia / curso / resumen)
- Fondo: `#FFFFFF`
- Borde: 1–2px (2px en vistas de alto contraste)
- Border-radius: 8px
- Barra de color superior o lateral identificando la entidad (materia, curso)
- Barra de progreso (cuando aplica): `role="progressbar"` con `aria-valuenow/min/max`

### 4.5. Tabla de datos
- Encabezado con fondo `#1A1A2E` (estudiante) o `#F8F9FA` (profesor/admin)
- Filas alternadas (`#FFFFFF` / `#F8F9FA`) para escaneo visual
- Encabezados con `scope="col"`
- Cada tabla con `aria-label` descriptivo

### 4.6. Badge de estado
- Forma: píldora (border-radius 999px)
- Combinación fondo claro + borde + texto del mismo tono (ej. `#F0FDF4` + `#16A34A` + texto `#15803D`)
- Nunca se usa solo como punto de color: siempre incluye la palabra del estado

### 4.7. Sidebar de navegación
- Ancho fijo: 240px
- Ítem activo: fondo `#2563EB`, texto blanco, `aria-current="page"`
- Ítem inactivo: fondo transparente, hover `#F3F4F6`
- Altura mínima por ítem: 44px

### 4.8. Skip link
- Oculto por defecto (`position: absolute; left: -9999px`)
- Visible al recibir foco: fondo `#2563EB`, texto blanco, posición fija superior izquierda

---

## 5. Iconografía

- Set de iconos: Lucide (line icons, peso visual consistente)
- Tamaño estándar: 18–20px en navegación, 14–16px en botones secundarios
- Todo ícono decorativo lleva `aria-hidden="true"`
- Todo ícono funcional (sin texto visible junto a él) lleva `aria-label` descriptivo

---