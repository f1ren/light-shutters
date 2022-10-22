# SVG files for light shutters (תריסי אור)
Set of SVG files that represents states of light shutters (תריסי אור).

![image](https://user-images.githubusercontent.com/2501137/197356807-5c20af40-cb13-4b48-9e07-cce7a63f78c2.png)

For use in home automation.
## Recommended usage
* In Home Assistant, you can use [hass-fontawesome](https://github.com/thomasloven/hass-fontawesome)'s [custom icons](https://github.com/thomasloven/hass-fontawesome#using-with-custom-icons) (e.g. `fapro:shutter-6-close-4`) in your buttons.
## Techincal details
* Formatted according to [Fontawesome icon requirements](https://fontawesome.com/v5/docs/web/use-kits/prep-icons-for-upload).
* The file name states close/open, depending whether the first level touched the ground or not, followed by the number of levels that are in this state.
* Due to the naming convention, `shutter-6-open-0.svg` is exactly the same as `shutter-6-close-1.svg`

## Home Assistant examples
### Get started
Notice that in this example, only the first button actually does something. You'll have to:
1. Set the entity in the first button
2. Copy the missing attributes to the rest of the buttons
```
type: grid
columns: 3
cards:
  - entity: cover.southern_roller
    show_name: false
    type: button
    tap_action:
      action: call-service
      service: cover.set_cover_position
      data:
        position: 0
        entity_id: cover.southern_roller
    icon: fapro:shutter-6-open-6
  - type: button
    icon: fapro:shutter-6-open-2
  - type: button
    icon: fapro:shutter-6-open-0
  - type: button
    icon: fapro:shutter-6-close-3
  - type: button
    icon: fapro:shutter-6-close-5
  - type: button
    icon: fapro:shutter-6-close-6
```

### Advanced: Popup card
* See `examples/cards.jinja`
* Render using Jinja2 engine. [Here's an online one](https://j2live.ttl255.com/).
* Requires [browser_mod 2](https://github.com/thomasloven/hass-browser_mod).
* The example is part of a Floorplan view.
* Loginc
  * It starts with a dictionary `roller_flip`, containing the "flip" position for each light shutter. That is, the maximal roller position at which the lowest level first touches the ground.
  * The template uses this position to calculate and render the other positions per each step defined in `OPEN_STEPS` and `CLOSE_STEPS`.
