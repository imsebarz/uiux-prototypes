# Memora Cover Style Customizer — notas de adaptación

## Decisión principal

La personalización no debe venderse como “cambiar color de fondo” para todos los casos, porque Memora usa portadas y contraportadas como assets raster por destino. La solución user-facing correcta es:

- **Tratamiento / tinte de portada** sobre el asset real.
- **Color del año/subtítulo** con protección de legibilidad.
- **Presets curados** por tono/destino antes del ajuste avanzado.
- “Color de fondo” solo para covers generadas o fallback sin imagen.

## Fuente revisada

Repo local: `/home/openclaw/.openclaw/workspace/repos/memora`

Archivos relevantes:

- `src/styles/base/_tokens.scss`
- `src/styles/DESIGN_SYSTEM.md`
- `src/components/organisms/flipbook/ReviewBookFlipbookFaceContent.tsx`
- `src/components/organisms/wizard/location/CoverYearOverlay.tsx`
- `src/components/molecules/BackCoverSubtitle/BackCoverSubtitle.tsx`
- `src/components/organisms/admin/locationDetail/CoverYearStyleEditorModal.tsx`
- `src/components/organisms/admin/locationDetail/CoverEditorPanelFields.tsx`
- `src/components/molecules/DestinationCoverCard/DestinationCoverCard.tsx`

Producción revisada: `https://memorabooks.co/`

Assets reales usados en el prototipo:

- París cover/back cover
- Colombia cover/back cover
- Italia cover/back cover

## Hallazgos UX/UI

1. El admin ya tiene el patrón poderoso: color, fuente, peso, letter spacing, guías, recents y preview en vivo.
2. El usuario final no necesita ese nivel de libertad; necesita sentirse dueño sin destruir el arte.
3. La portada usa `CoverYearOverlay`; la contraportada usa `BackCoverSubtitle`.
4. El sistema debe compartir datos entre wizard, review, PDF y admin para evitar divergencias.

## Recomendación de producto

### Usuario final

- Paso “Diseño” en wizard.
- Destino visible.
- Tabs: Portada / Contraportada.
- Presets recomendados: Memora editorial, Luz postal, Pumpkin cálido, Baby pink recuerdo, Tapa sobria, Sin tinte.
- Ajuste fino colapsado o secundario.
- Protección de legibilidad activa por defecto.

### Admin

Mantener editor completo para calibrar asset por destino: guías, posición, font size, bottom ratio de contraportada.

### Dev handoff

Evaluar extender `CoverYearStyle` o crear `CoverTreatmentStyle` con:

```ts
type CoverTreatmentStyle = {
  tintColor: string;
  tintOpacity: number;
  textColor: string;
  presetId?: string;
  applyTo?: "front" | "back" | "both";
};
```

Regla: el PDF renderer debe consumir la misma data que review/flipbook.
