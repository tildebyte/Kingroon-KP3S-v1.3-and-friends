# Personal repo for Kingroon KP3S, Klipper, OctoPrint, PrusaSlicer & friends


This repo contains configs for using the
[Kingroon KP3S v1.3](https://kingroon.com/products/official-kingroon-kp3s-3d-printer)
(latest model as of 2022; the one with the Titan extruder) with the following

## WARNING

In no way is this an "installable" repo. Don't expect to be able to unpack it
somewhere and have it "just work". For one thing, the klipper config is *highly*
customized to my physical printer (which is likely *physically* different from
even another "identical" KP3S v1.3 due to manufacturing tolerances, etc.)

This is primarily a backup for me, *but it could certainly be useful as a reference
for someone looking for up-to-date configs for the components I use*, to wit:

## Primary tools

- [Klipper](https://www.klipper3d.org/) (source @ https://github.com/Klipper3d/klipper)
- [OctoPrint](https://octoprint.org/) (source @ https://github.com/OctoPrint/OctoPrint)
- [PrusaSlicer](https://github.com/prusa3d/PrusaSlicer)
- [ustreamer](https://github.com/pikvm/ustreamer)
- [moonraker](https://github.com/Arksine/moonraker) (used only for KAMP)

## Notable addons

> NOTE: These are all GitHub links

### For Klipper

- [KAMP](https://github.com/kyleisah/Klipper-Adaptive-Meshing-Purging) (only probe the bed in the area where a part will be)
- [preprocess_cancellation](https://github.com/kageurufu/preprocess_cancellation) (Klipper GCode Preprocessor for Object Cancellation; strictly for KAMP)
- [klipper_estimator](https://github.com/Annex-Engineering/klipper_estimator) (Klipper print time estimator: it's brilliant)

### For OctoPrint

- [Bltouch](https://github.com/jneilliii/OctoPrint-Bltouch)
- [MarlinGcodeDocumentation](https://github.com/costas-basdekis/MarlinGcodeDocumentation)
- [KlipperPlugin](https://github.com/thelastWallE/OctoprintKlipperPlugin)
- [PrintJobHistory](https://github.com/OllisGit/OctoPrint-PrintJobHistory)
- [PrintTimeGenius](https://github.com/eyal0/OctoPrint-PrintTimeGenius) (plays quite well with PrusaSlicer and klipper_estimator)
- [PrusaSlicerThumbnails](https://github.com/jneilliii/OctoPrint-PrusaSlicerThumbnails)
- [Tasmota](https://github.com/jneilliii/OctoPrint-Tasmota)
- [UICustomizer](https://github.com/LazeMSS/OctoPrint-UICustomizer) (obviates all other UI plugins)

## Older repos which I used as references

- https://github.com/9R/Klipper_KP3S
- https://github.com/bdwilson/KP3S
- https://github.com/nehilo/Klipper-KingRoon-Printers
