# Memora Design System — documentación base

Auditoría y consolidación UI/UX basada en el codebase local de Memora.

## Producto

Memora es una experiencia de creación y compra de álbumes/libros de recuerdos personalizados para Colombia, con foco comercial en Medellín y envíos nacionales.

**Prioridades UX del producto:**

1. Conversión de landing hacia `/create`.
2. Claridad del wizard de creación.
3. Carga mobile de fotos sin fricción.
4. Checkout confiable.
5. Percepción premium/artesanal sin perder velocidad.
6. Accesibilidad práctica.

## Fuentes revisadas

- `src/styles/base/_tokens.scss`
- `src/styles/DESIGN_SYSTEM.md`
- `src/styles/abstracts/_mixins.scss`
- `src/app/layout.tsx`
- `src/components/atoms/*`
- `src/components/templates/LandingPage/*`
- `src/components/templates/WizardPage/*`
- `src/components/organisms/wizard/*`
- `src/components/templates/CheckoutPage/*`
- `src/components/templates/CartPage/*`
- `src/i18n/es/*`

## Personalidad visual

Memora ya tiene una dirección clara:

- **Cálida**: crema, café, naranja, rosa y azul pálido.
- **Editorial/artesanal**: tipografía display para momentos de marca y portada.
- **Premium accesible**: superficies suaves, bordes cálidos, sombras de papel/tarjeta.
- **Emocional pero pragmática**: producto sentimental, flujo transaccional.

La marca no debe volverse “startup SaaS genérica”. Memora vende recuerdos físicos; la interfaz debe sentirse táctil, confiable y humana.

## Paleta base

Todos los colores del sistema derivan de cinco colores de marca:

| Nombre | Hex | Uso |
|---|---:|---|
| Floral White | `#F6F4EB` | Fondo principal, superficies cálidas |
| Coffee Bean | `#694A38` | Texto, paneles inversos, marca seria |
| Pumpkin Spice | `#EB7523` | CTA primario, acentos de acción |
| Pale Sky | `#C1E1F1` | Superficies informativas/acento suave |
| Baby Pink | `#FFB0CA` | Acento emocional, error suave, detalle editorial |

## Tokens semánticos clave

### Acción

- `--memora-color-action-primary`: CTA principal naranja.
- `--memora-color-action-primary-text`: texto sobre CTA.
- `--memora-color-action-primary-hover`: hover o énfasis oscuro.
- `--memora-color-action-primary-emphasis`: estado pressed/hover fuerte.

### Superficies

- `--memora-color-surface-page`: fondo global.
- `--memora-color-surface-card`: cards y paneles.
- `--memora-color-surface-neutral`: azul pálido adaptable.
- `--memora-color-surface-inverse`: panel premium café fijo.
- `--memora-color-surface-accent-sky`: azul pálido fijo.
- `--memora-color-surface-accent-pink`: rosa fijo.

### Texto

- `--memora-color-text-heading`: titulares.
- `--memora-color-text-body`: cuerpo.
- `--memora-color-text-secondary`: apoyo.
- `--memora-color-text-muted`: metadata/ayuda.
- `--memora-color-text-on-inverse`: texto sobre café.

### Bordes y sombras

- `--memora-color-border-default`
- `--memora-color-border-muted`
- `--memora-color-border-soft`
- `--memora-shadow-card-rest`
- `--memora-shadow-card-hover`
- `--memora-shadow-card-lifted`

## Tipografía

Declarada en `src/app/layout.tsx` con `next/font/local`.

| Familia | Variable | Rol |
|---|---|---|
| DM Sans | `--font-dm-sans` | UI, cuerpo, navegación, formularios |
| Neulis | `--font-neulis` | Marca, titulares editoriales, acentos |
| Neulis Alt | `--font-neulis-alt` | Variantes configurables de portada |
| Anton | `--font-anton` | Año/portada/back cover, voz de objeto impreso |

### Reglas de uso

- UI funcional: DM Sans.
- Marca y titulares con emoción: Neulis.
- Portadas y año: Anton o variantes configuradas.
- No cargar pesos no usados; el repo ya cuida performance de fuentes.

## Escala de spacing

Tokens `--memora-space-*`, derivados de `--spacing: .25rem`.

Uso recomendado:

- `1–2`: ajustes finos, labels, gaps pequeños.
- `3–4`: controles, padding compacto.
- `5–8`: cards, bloques, formularios.
- `10–16`: secciones internas.
- `24`: respiración grande/hero.

Regla: no inventar `calc(var(--spacing) * n)` en componentes. Usar tokens existentes.

## Radios

| Token | Uso |
|---|---|
| `--memora-radius-sm` | chips pequeños, ayudas compactas |
| `--memora-radius-md` | inputs, notices, cards compactas |
| `--memora-radius-lg` | paneles medianos |
| `--memora-radius-xl` | cards grandes premium |
| `--memora-radius-pill` | botones, pills, toggles |

## Componentes canónicos

### ActionButton

Fuente: `src/components/atoms/ActionButton`.

Variantes:

- `primary`: acción principal.
- `secondary`: acción alternativa.
- `ghost`: navegación/acción textual.
- `dark`: sobre superficies claras cuando se necesita peso.
- `danger`: acción destructiva textual.

Tamaños: `xs`, `sm`, `md`, `lg`.

Regla: no rediseñar links como pills localmente. Usar `ActionButton`.

### SurfaceCard

Fuente: `src/components/atoms/SurfaceCard`.

Uso: paneles, resúmenes, formularios, contenedores de confianza.

Props visuales: `padding`, `maxWidth`, `centered`.

### TextField / TextareaField / SelectField

Uso: formularios de checkout, datos de envío, contacto, auth.

Incluyen:

- label accesible.
- required marker.
- helper/error copy.
- aria-invalid.
- focus ring naranja.

### InlineNotice

Tonos: `success`, `error`, `info`.

Variantes:

- `box`: mensaje de estado visible.
- `text`: mensaje compacto dentro de layouts densos.

### StatusPill

Tonos: `success`, `info`, `warning`, `danger`, `neutral`.

Uso: órdenes, pagos, estados admin, tracking.

### EmptyState

Uso: listas vacías, drafts, órdenes inexistentes, estados sin contenido.

Debe incluir título, body y acción cuando el usuario pueda hacer algo.

## Patrones UX principales

### Landing

Estructura actual:

1. Hero visual con banners.
2. Catálogo de destinos.
3. Sugerencia de destino.
4. Cómo funciona.
5. Bundles/precios.
6. Showcase.
7. CTA de catálogo.
8. FAQ.
9. Reviews.
10. Newsletter.
11. Footer.

Recomendación: reducir competencia visual y mejorar jerarquía de CTA. La landing tiene buena materia prima, pero corre riesgo de densidad alta.

### Wizard `/create`

Fases observadas:

- Selección ubicación/portada.
- Upload de fotos.
- Diseño/editor.
- Revisión.
- Shipping/checkout.

Prioridad UI: el usuario no técnico debe saber siempre: dónde está, qué falta, qué se guardó y qué pasa si abandona.

### Mobile upload

Patrones relevantes:

- Stepper compacto.
- Indicadores de carga en background.
- Modales/sheets móviles.
- Targets táctiles mínimos de 44px.

Prioridad: confianza durante carga; evitar estados ambiguos tipo “¿mis fotos se subieron o morí aquí?”.

### Checkout

Debe verse menos como formulario triste y más como cierre confiable:

- Resumen persistente.
- Costos claros.
- Estados de cupón/envío explícitos.
- Errores de pago accionables.
- Indicadores de seguridad y tiempos sin inventar claims.

## Dark mode

El sistema tiene contrato explícito de dark mode. Trampas importantes:

- `--memora-color-ink-deepest` invierte a crema en dark mode: no usarlo para paneles café fijos.
- Para paneles café permanentes usar `--memora-color-surface-inverse` + tokens `on-inverse`.
- Para superficies que deben cambiar con tema usar `--memora-color-surface-card`.
- No fijar `#fff` bajo texto que cambia de tema.

## Accesibilidad mínima

- Focus visible con naranja.
- Targets táctiles de 44px.
- `prefers-reduced-motion` respetado globalmente.
- Labels reales en inputs.
- Estados invalid/error conectados por ARIA.
- Skip link disponible.

## Reglas de contribución UI

1. No hardcodear hex en SCSS de componentes.
2. No crear botones/input/card locales si existe átomo canónico.
3. Local SCSS solo debe controlar layout, densidad o excepción contextual.
4. Si un patrón aparece 2 veces cerca o 3 veces global, extraerlo.
5. Todo nuevo estado debe tener hover, focus, disabled/loading/error/empty cuando aplique.
6. Respetar dark mode antes de declarar final.

## Próxima documentación recomendada

- Guía específica de landing conversion.
- Guía de wizard mobile.
- Guía de checkout y confianza.
- Inventario visual de admin/dashboard.
- Matriz de estados de órdenes y pagos.
