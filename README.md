# change-colors-of-Cards-HA
In this repository you can view how to change the color cards in HA

To change the color or transparency of Home Assistant cards, you must install the Card-Mod integration and then add the card_mod parameter to the specific card or element you want to style. You can then use CSS properties within the style section, such as background: transparent; for transparency or background: rgba(255, 255, 255, 0.5); for a semi-transparent white background. 
1. Install the Card-Mod Integration
Using HACS:
If you use HACS (Home Assistant Community Store), search for "Card-Mod" and install it. 
Manual Installation:
If you don't use HACS, you can manually install the integration from its GitHub repository by adding it to your custom_components folder. 
2. Identify the Card or Element to Style
For the entire card:
Target the <ha-card> element. 
For individual elements within a card:
Use a browser's developer tools (like Chrome's Inspect) to find the specific HTML element and its corresponding CSS selector. You can often access these elements via :host if they are within a shadow root. 
3. Apply the card_mod Styling 
Add card_mod to your card's YAML configuration:
 
yaml
type: entities
card_mod:
  style: |
    ha-card {
      To change the color or transparency of Home Assistant cards, you must install the Card-Mod integration and then add the card_mod parameter to the specific card or element you want to style. You can then use CSS properties within the style section, such as background: transparent; for transparency or background: rgba(255, 255, 255, 0.5); for a semi-transparent white background. 
1. Install the Card-Mod Integration
Using HACS:
If you use HACS (Home Assistant Community Store), search for "Card-Mod" and install it. 
Manual Installation:
If you don't use HACS, you can manually install the integration from its GitHub repository by adding it to your custom_components folder. 
2. Identify the Card or Element to Style
For the entire card:
Target the <ha-card> element. 
For individual elements within a card:
Use a browser's developer tools (like Chrome's Inspect) to find the specific HTML element and its corresponding CSS selector. You can often access these elements via :host if they are within a shadow root. 
3. Apply the card_mod Styling 
Add card_mod to your card's YAML configuration:
 
yaml
type: entities
card_mod:
  style: |
    ha-card {
      # Your CSS goes here
    }
For background transparency:
 
yaml
card_mod:
  style: |
    ha-card {
      background: transparent;
      border-style: none; /* Removes border for cleaner transparency */
    }
For a semi-transparent background:
 
yaml
card_mod:
  style: |
    ha-card {
      background: rgba(0, 0, 0, 0.5); /* Semi-transparent black */
    }
For custom background color:
 
yaml
card_mod:
  style: |
    ha-card {
      --ha-card-background: teal; /* Uses the HA theme CSS variable */
    }
For styling within an entity:
 
yaml
type: entities
entities:
  - entity: light.bed_light
    card_mod:
      style: |
        :host {
          color: red;
        }Your CSS goes here
    }
For background transparency:
 
yaml
card_mod:
  style: |
    ha-card {
      background: transparent;
      border-style: none; /* Removes border for cleaner transparency */
    }
For a semi-transparent background:
 
yaml
card_mod:
  style: |
    ha-card {
      background: rgba(0, 0, 0, 0.5); /* Semi-transparent black */
    }
For custom background color:
 
yaml
card_mod:
  style: |
    ha-card {
      --ha-card-background: teal; /* Uses the HA theme CSS variable */
    }
For styling within an entity:
 
yaml
type: entities
entities:
  - entity: light.bed_light
    card_mod:
      style: |
        :host {
          color: red;
        }
