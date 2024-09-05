# Habitats and Locations

Habitats and locations appear in the animal buy window below the animal name as show in the picture below.

![Habitats and Locations](./images/animal_buy_circle_habitat_location.jpg)

Zoo Tycoon comes with many inbuilt habitats and locations which can be referenced when making an animal, but prior to OpenZT modded locations or habitats were particularly hard to make. With OpenZT habitats and locations can be made and used with ease. They have a very similar config (in Vanilla ZT they are actually interchangeable, minus the UI looking wrong)

```toml
[locations.moon]
name="Moon"
icon_path="resources/moon/N"
icon_palette_path="resources/moon/moon.pal"

[habitats.swamp]
name="Swamp"
icon_path="resources/swamp/N"
icon_palette_path="resources/swamp/swamp.pal"
```

All values are mandatory here. The type is dicated by having the `locations` or `habitats` prefix in the section header. The suffix in the section headers (`moon` and `swamp` in this example) must be unique for each definition type within your mod, eg you can only have one `locations.moon` but you can have a `habitats.moon` too. You could have another `habitats.moon` in a separate mod, these will not conflict.

`name` is displayed as a tooltip when the player hovers over the habitat/location image in game.

`icon_path` is the path (within the resources) filepath to the icon file (in the ZT animation format) is located.

`icon_palette_path` is the path to the palette (`.pal`) file for the icon. 
!!! info 
    Vanilla ZT uses the `.pal` file referenced within the animation file, OpenZT ignores it and uses the file specified here.

## Adding habitats or locations to existing animals

!!! info "Coming Soon"
<!-- Coming Soon (brief example here, link to 'Patch' page for full details) -->
