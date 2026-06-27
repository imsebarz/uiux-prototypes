# Memora — inventario de componentes UI

## Átomos canónicos

| Componente | Path | Rol | Notas |
|---|---|---|---|
| ActionButton | `src/components/atoms/ActionButton` | CTAs y acciones tipo link/button | Variantes primary, secondary, ghost, dark, danger |
| SurfaceCard | `src/components/atoms/SurfaceCard` | Paneles/card base | Padding sm/md/lg; maxWidth md/lg/xl |
| TextField | `src/components/atoms/TextField` | Input texto | Label, helper, error, required, aria-invalid |
| TextareaField | `src/components/atoms/TextareaField` | Texto largo | Misma semántica de campos |
| SelectField | `src/components/atoms/SelectField` | Selects | Formularios y checkout |
| SegmentedControl | `src/components/atoms/SegmentedControl` | Toggle/rango discreto | Evitar radios custom locales |
| InlineNotice | `src/components/atoms/InlineNotice` | Mensajes inline | success/error/info; box/text |
| StatusPill | `src/components/atoms/StatusPill` | Estado visual | success/info/warning/danger/neutral |
| EmptyState | `src/components/atoms/EmptyState` | Estados vacíos | Icon/eyebrow/title/body/action |
| Skeleton | `src/components/atoms/Skeleton` | Loading | Respeta reduce motion |
| MediaActionChip | `src/components/atoms/MediaActionChip` | Acciones sobre fotos/media | Hit area 44px invisible |
| AccentText | `src/components/atoms/AccentText` | Acento naranja en títulos | Neulis + action primary |

## Moléculas relevantes

| Componente | Path | Rol |
|---|---|---|
| CouponCodeField | `src/components/molecules/CouponCodeField` | Cupón checkout/cart |
| DestinationCoverCard | `src/components/molecules/DestinationCoverCard` | Card de destino/portada |
| LandingDestinationCatalog | `src/components/molecules/landing/LandingDestinationCatalog` | Catálogo principal landing |
| LandingReviewCard | `src/components/molecules/landing/LandingReviewCard` | Testimonios |
| LandingWorkflowCard | `src/components/molecules/landing/LandingWorkflowCard` | Paso de flujo |
| LandingBundleTierCard | `src/components/molecules/landing/LandingBundleTierCard` | Paquetes/precios |
| SiteHeaderMobileMenu | `src/components/molecules/navigation/SiteHeaderMobileMenu` | Navegación móvil |
| AdminTabs | `src/components/molecules/admin/AdminTabs` | Tabs admin |

## Organismos/plantillas clave

| Área | Paths | Riesgo UX |
|---|---|---|
| Landing | `src/components/templates/LandingPage`, `src/components/organisms/landing` | Densidad y CTA hierarchy |
| Wizard | `src/components/templates/WizardPage`, `src/components/organisms/wizard` | Confianza, guardado, mobile upload |
| Checkout | `src/components/templates/CheckoutPage`, `src/hooks/checkout` | Errores, costos, seguridad |
| Cart | `src/components/templates/CartPage`, `src/hooks/cart` | Continuidad hacia pago |
| Review | `src/components/templates/ReviewPage`, `src/hooks/review` | Aprobación/rechazo claro |
| Account | `src/components/templates/AccountPage`, `src/components/organisms/account` | Historial y tracking |
| Admin | `src/components/templates/AdminPage`, `src/components/organisms/admin` | Densidad operativa |

## Recomendación de madurez

Nivel actual: **intermedio-alto**.

El sistema ya tiene tokens, dark mode, átomos, mixins y pruebas. Falta convertirlo en una fuente navegable y gobernada: ejemplos visuales, reglas de composición, guías por flujo y checklist de uso.
