# change-colors-of-Cards-HA

🇬🇧 English · [🇪🇸 Español](README.es.md)

How to change the color or transparency of Home Assistant cards with **card-mod**.

[card-mod](https://github.com/thomasloven/lovelace-card-mod) is a **frontend plugin** (a dashboard resource loaded by the browser), not a backend integration. You add a `card_mod` block to the card or element you want to style and write CSS inside its `style` section.

## 1. Install card-mod

**With HACS (recommended)**
Search for `card-mod` in HACS and download it. HACS adds the dashboard resource automatically (a path like `/hacsfiles/lovelace-card-mod/card-mod.js?hacstag=...`); keep that entry as it is so HACS can track updates. Reload the browser (clear its cache if the styles don't show up).

**Manually**
Download `card-mod.js` from the [card-mod repository](https://github.com/thomasloven/lovelace-card-mod), copy it into your Home Assistant `www` folder and add it as a dashboard resource (`Settings → Dashboards → ⋮ → Resources`, type *JavaScript module*, URL `/local/card-mod.js`). The Resources menu requires *advanced mode* to be enabled in your user profile.

> ℹ️ card-mod is **not** installed in `custom_components`: that folder is for integrations.

## 2. Identify what you want to style

- **The whole card:** target the `ha-card` element.
- **An entity row inside an `entities` card:** add `card_mod` to that entity and style `:host`.
- **Other inner elements:** use your browser's developer tools (e.g. Chrome's *Inspect*) to find the element and its CSS selector. Many elements live inside a shadow root, so check the card-mod documentation for how to reach them.

## 3. Apply `card_mod`

Add it to the card's YAML (open the card's code editor; a small brush icon shows that a card has hidden card-mod code):

```yaml
type: entities
card_mod:
  style: |
    ha-card {
      /* Your CSS goes here */
    }
```

### Transparent background

```yaml
card_mod:
  style: |
    ha-card {
      background: transparent;
      border-style: none; /* removes the border for a cleaner look */
    }
```

### Semi-transparent background

```yaml
card_mod:
  style: |
    ha-card {
      background: rgba(0, 0, 0, 0.5); /* semi-transparent black */
    }
```

### Custom background color

```yaml
card_mod:
  style: |
    ha-card {
      --ha-card-background: teal; /* uses Home Assistant's theme CSS variable */
    }
```

### Styling a single entity row

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

You can also use Home Assistant theme variables inside card-mod, for example `color: var(--primary-color);`.

## Related resources

- [card-mod](https://github.com/thomasloven/lovelace-card-mod) — official repository and documentation
- [HACS](https://hacs.xyz) — Home Assistant Community Store
