# Eurorack PSU

DIY Eurorack power supply based on three **Mean Well IRM AC/DC modules**, with linear post-regulation using **LM350** and **LM337**.

The design was developed in **KiCad** specifically for Eurorack modular synthesizers, with separate power sources for the positive and negative rails and a dedicated +5 V supply.

## Features

- **+12 V / -12 V / +5 V** Eurorack power rails
- 3× isolated Mean Well IRM AC/DC modules
- Linear regulation of the ±12 V rails
- **LM350** positive voltage regulator
- **LM337** negative voltage regulator
- Dedicated +5 V supply
- Filtering and decoupling
- Heatsinks on the linear regulators
- KiCad schematic and PCB design

## Power supply architecture

The power supply uses three independent Mean Well AC/DC modules:

```text
                         AC MAINS
                            │
             ┌──────────────┼──────────────┐
             │              │              │
             ▼              ▼              ▼
        IRM-45-15       IRM-20-15       IRM-20-5
          15 V / 3 A      15 V / 1.4 A     5 V / 4 A
             │              │              │
             ▼              ▼              │
           LM350          LM337             │
             │              │              │
             ▼              ▼              ▼
           +12 V           -12 V           +5 V
             │              │              │
             └──────────────┴──────────────┘
                            │
                     Eurorack power bus
```

The two 15 V supplies are used independently for the positive and negative Eurorack rails.

The ±12 V outputs are obtained through linear regulation, providing additional filtering and regulation after the isolated AC/DC conversion stage.

## Mean Well modules

| Module | Output | Rated current | Rated power | Rail |
|---|---:|---:|---:|---|
| **IRM-45-15** | 15 V DC | 3 A | 45 W | +12 V |
| **IRM-20-15** | 15 V DC | 1.4 A | 21 W | -12 V |
| **IRM-20-5** | 5 V DC | 4 A | 20 W | +5 V |

The three AC/DC modules provide a combined nominal power of approximately **86 W** before linear regulation losses.

## Output specifications

| Rail | Regulation | Maximum current* | Maximum output power* |
|---|---|---:|---:|
| **+12 V** | LM350 | 3 A | 36 W |
| **-12 V** | LM337 | 1.4 A | 16.8 W |
| **+5 V** | IRM-20-5 | 4 A | 20 W |
| **Total** | | | **72.8 W** |

\* The values for the ±12 V rails are theoretical maximums based on the nominal output current of the corresponding Mean Well modules. Actual continuous output capability depends on thermal conditions, heatsink installation, PCB design and ambient temperature.

## Thermal considerations

The ±12 V rails use linear regulators, which dissipate the voltage difference between the 15 V input and the regulated 12 V output as heat.

## PCB

The PCB was designed using **KiCad**.

The repository contains the design files and manufacturing data for the power supply.

## Interactive BOM

The interactive Bill of Materials is available online:

**[🔧 Open Interactive BOM](https://jojo-monk.github.io/eurorack-psu/ibom.html)**


## Project status

**Built, tested and fully functional.**

The power supply has been successfully assembled, tested and validated in operation. All three output rails (**+12 V, -12 V and +5 V**) have been tested and the power supply is fully operational in a Eurorack system.
>>>>>>> Stashed changes

## Safety

> [!WARNING]
> **MAINS VOLTAGE**
>
> This power supply is directly connected to the AC mains.
>
> Mains voltage can cause serious injury or death. This project should only be built and tested by people familiar with mains electrical safety.
>
> The finished power supply must be installed in a suitable enclosure with:
>
> - proper mains insulation
> - protective earth where required
> - appropriate fusing
> - strain relief
> - adequate spacing between mains and low-voltage circuitry
> - protection against accidental contact with mains voltage
>
> Do not operate the PCB exposed when connected to the mains.

## Project status

This is a DIY Eurorack power supply developed for personal experimentation and modular synthesizer projects.

The design is provided as-is. Always verify the actual output voltages, current capability and thermal performance of the assembled unit before connecting Eurorack modules.

## License
[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

License
This project is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) license.
Copyright © 2026 Johann Moine
You are free to:
Share — copy and redistribute the material
Adapt — remix, transform and build upon the material
Under the following conditions:
Attribution — You must give appropriate credit to the original author, provide a link to the license, and indicate if changes were made.
NonCommercial — You may not use the material for commercial purposes.
ShareAlike — If you remix, transform, or build upon the material, you must distribute your contributions under the same license.
See the full license:
Creative Commons BY-NC-SA 4.0
