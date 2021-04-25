# OpenRAM Configuration for 4kB SRAM using sky130

* * *

[![A static RAM chip from nitendo Entertainment system clone 2K x 8 bits](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Hyundai_RAM_HY6116AP-10.jpg/440px-Hyundai_RAM_HY6116AP-10.jpg)](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Hyundai_RAM_HY6116AP-10.jpg/440px-Hyundai_RAM_HY6116AP-10.jpg)

**What is SRAM?**

- Static Random Access Memory(SRAM) is a type of random-access memory that uses latching circuitry(flip flop) to store each bit.
- SRAM is volatile memory, data is lost when power is removed.
- Does not require periodic refresh

# Introduction to OpenRAM

- OpenRAM is an open-source static random access memory (SRAM) compiler.
- Uses Python framework to create layout, netlists, timing and power models, placement and routing models, and other views necessary to use SRAMs in ASIC design.

**Dependencies**
The OpenRAM compiler has very few dependencies:

- [Ngspice](http://ngspice.sourceforge.net/) 26(or later) or Hspice or CustomSim 2017(or later)
- Python 3.5 or higher
    - Python numpy (`pip3 install numpy` to install)
    - Python scipy (`pip3 install scipy` to install)

If you want to perform DRC and LVS, you will need either:

- DRC
    - Calibre(for [FreePDK](https://www.eda.ncsu.edu/wiki/FreePDK45:Contents))
    - [Magic](http://opencircuitdesign.com/magic/) 8.3.27 or higher (for [SCMOS](https://www.mosis.com/files/scmos/scmos.pdf))
- LVS
    - Calibre 2017
    - [Netgen](http://opencircuitdesign.com/netgen/) 1.5 (for SCMOS)

**Supported Technologies**

- NCSU FreePDK 45nm
- MOSIS 0.35um (SCN4M_SUBM)
- NCUS FreePDJ 15nm & ASAP 7nm

For more information take a look at the detailed presentaion that serves as [documentation](https://docs.google.com/presentation/d/10InGB33N51I6oBHnqpU7_w9DXlx-qe9zdrlco2Yc5co/edit#slide=id.g4e915a9f17_2_4). This is the most up-to-date information.

# Environment Setup and Custom Cells Description

**OpenRAM Environment Setup**

Downloading the OpenRAM packages from [github](https://github.com/VLSIDA/OpenRAM):

```
git clone https://github.com/VLSIDA/OpenRAM.git
```

Adding OPENRAAM_HOME to PYTHONPATH:

```
export PYTHONPATH="$PYTHONPATH:$OPENRAM_HOME"
```

It includes the tech files necessory for SCMOS SCN4M_SUBM. The SCMOS spice models, however, are generic and should be replaced with foundry models. If you are using FreePDK45, you should also have that set up and have the environment variable point to the PDK. For example add this to your .bashrc:

```
export FREEPDK45="/bsoe/software/design-kits/FreePDK45"
```

You may get the [entire FreePDK45 PDK here](https://www.eda.ncsu.edu/wiki/FreePDK45:Contents). If you are using SCMOS, you should install Magic and Netgen. We have included the most recent SCN4M_SUBM design rules from [Qflow](http://opencircuitdesign.com/qflow/history.html).
