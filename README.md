# Corne right-display artwork

This repository owns the Corge bitmap shown on the wireless Corne’s right nice!view display. The keyboard’s everyday layout and the matched left/right firmware come from [MarkBerube/zmk-config-corne](https://github.com/MarkBerube/zmk-config-corne).

## Change the artwork

1. Edit the bitmap or image descriptor in [zephyr/corge.c](zephyr/corge.c). The [module build rules](zephyr/CMakeLists.txt) connect the Corge image to the peripheral status widget. The standalone build and the consuming firmware can use different LVGL versions, so check image-format changes against both.
2. Commit the artwork here. Update the `corne-display-art` revision in the [firmware manifest](https://github.com/MarkBerube/zmk-config-corne/blob/master/config/west.yml) to that commit. The pin determines which artwork ships.
3. Verify the [firmware workflow](https://github.com/MarkBerube/zmk-config-corne/actions/workflows/build.yml) for the updated manifest. Check both half builds, the artifact merge, and the right-half log for `corge.c.obj`. Use the right UF2 from that firmware ZIP for the right display.

## Why this repo also has a keymap

The local `config/corne.keymap`, `build.yaml`, and workflow support this repository’s standalone build. When the firmware repository imports this project, it consumes the Zephyr artwork module and builds with its own keymap. Make changes to Space, Enter, Backspace, layers, and hold behaviors in the [firmware keymap](https://github.com/MarkBerube/zmk-config-corne/blob/master/config/corne.keymap).
