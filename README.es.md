# change-colors-of-Cards-HA

[🇬🇧 English](README.md) · 🇪🇸 Español

Cómo cambiar el color o la transparencia de las tarjetas de Home Assistant con **card-mod**.

[card-mod](https://github.com/thomasloven/lovelace-card-mod) es un **plugin de frontend** (un recurso de dashboard que carga el navegador), no una integración de backend. Añades un bloque `card_mod` a la tarjeta o elemento que quieres personalizar y escribes CSS dentro de su sección `style`.

## 1. Instalar card-mod

**Con HACS (recomendado)**
Busca `card-mod` en HACS y descárgalo. HACS añade el recurso de dashboard automáticamente (una ruta del tipo `/hacsfiles/lovelace-card-mod/card-mod.js?hacstag=...`); déjalo tal cual para que HACS pueda seguir las actualizaciones. Recarga el navegador (y limpia su caché si los estilos no aparecen).

**Manualmente**
Descarga `card-mod.js` del [repositorio de card-mod](https://github.com/thomasloven/lovelace-card-mod), cópialo a la carpeta `www` de Home Assistant y añádelo como recurso de dashboard (`Ajustes → Dashboards → ⋮ → Recursos`, tipo *Módulo JavaScript*, URL `/local/card-mod.js`). El menú Recursos requiere tener activado el *modo avanzado* en tu perfil.

> ℹ️ card-mod **no** se instala en `custom_components`: esa carpeta es para integraciones.

## 2. Identificar qué quieres personalizar

- **Toda la tarjeta:** apunta al elemento `ha-card`.
- **Una fila de entidad dentro de una tarjeta `entities`:** añade `card_mod` a esa entidad y estiliza `:host`.
- **Otros elementos internos:** usa las herramientas de desarrollador del navegador (p. ej. *Inspeccionar* en Chrome) para encontrar el elemento y su selector CSS. Muchos elementos están dentro de un *shadow root*; consulta la documentación de card-mod para saber cómo alcanzarlos.

## 3. Aplicar `card_mod`

Añádelo al YAML de la tarjeta (abre el editor de código de la tarjeta; un pequeño icono de pincel indica que la tarjeta tiene código card-mod oculto):

```yaml
type: entities
card_mod:
  style: |
    ha-card {
      /* Tu CSS va aquí */
    }
```

### Fondo transparente

```yaml
card_mod:
  style: |
    ha-card {
      background: transparent;
      border-style: none; /* quita el borde para un aspecto más limpio */
    }
```

### Fondo semitransparente

```yaml
card_mod:
  style: |
    ha-card {
      background: rgba(0, 0, 0, 0.5); /* negro semitransparente */
    }
```

### Color de fondo personalizado

```yaml
card_mod:
  style: |
    ha-card {
      --ha-card-background: teal; /* usa la variable CSS del tema de Home Assistant */
    }
```

### Personalizar una sola fila de entidad

```yaml
type: entities
entities:
  - entity: light.bed_light
    card_mod:
      style: |
        :host {
          color: red;
        }
```

También puedes usar variables del tema de Home Assistant dentro de card-mod, por ejemplo `color: var(--primary-color);`.

## Recursos relacionados

- [card-mod](https://github.com/thomasloven/lovelace-card-mod) — repositorio oficial y documentación
- [HACS](https://hacs.xyz) — Home Assistant Community Store
