# Memora Cover Color Customizer — notas de entrega

## Qué incluye

- Prototipo HTML interactivo para personalizar color de fondo y color de letra de portada/contraportada.
- Preview en vivo de portada, contraportada y mock mobile.
- Paletas recomendadas como camino principal.
- Ajuste avanzado con color picker + HEX.
- Validación visual de contraste y modo “proteger legibilidad”.

## Decisión UX principal

La personalización no debe abrir con libertad total. En Memora, el usuario quiere un libro bonito, no convertirse en director de arte bajo presión. Por eso la UI prioriza:

1. Paletas curadas.
2. Preview inmediato.
3. Edición avanzada escondida/controlada.
4. Protección de contraste para impresión y lectura.

## Handoff frontend

### Modelo de datos sugerido

```ts
type CoverColorSettings = {
  front: {
    backgroundColor: string;
    textColor: string;
    paletteId?: string;
    isCustom?: boolean;
  };
  back: {
    backgroundColor: string;
    textColor: string;
    paletteId?: string;
    isCustom?: boolean;
  };
  protectLegibility: boolean;
};
```

### Estados mínimos

- Default por destino/plantilla.
- Preset seleccionado.
- Custom validado.
- Contraste insuficiente.
- Autosave pending/saved/error.
- Reset por lado.
- Aplicar a ambas caras.
- Disabled durante render/generación de PDF.

### Accesibilidad

- Mantener contraste mínimo 4.5:1 para textos principales.
- Inputs de color con label textual y campo HEX editable.
- Focus visible en tabs, presets, color pickers y acciones.
- Targets táctiles mínimos de 44px en mobile.

### Implementación recomendada

1. Agregar presets de color al modelo de portada.
2. Persistir `front/back backgroundColor/textColor` en draft.
3. Reusar preview actual de cover/back cover aplicando CSS variables.
4. Añadir validación de contraste antes de guardar/renderizar PDF.
5. Conectar el render PDF para respetar los colores finales.

## Caveat

Este prototipo no modifica Memora ni genera PDF real. Es una exploración de interacción y handoff visual para decidir el comportamiento antes de implementarlo.
