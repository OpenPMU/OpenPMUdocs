# OpenPMU

OpenPMU is the Open Source Phasor Measurement Unit.

What's a PMU?  Why would you want one?  Find out at www.openpmu.org/pmu-fundamentals  :)

We're also easy to get in touch with via www.facebook.com/OpenPMU - Say hi!  :D


![Three modules of OpenPMU](https://github.com/OpenPMU/OpenPMU/blob/master/images/Three%20Modules.PNG)
__*Fig. 1 - The three modules of the OpenPMU system*__

OpenPMU is a structured modular system.  Waveform **sampled values (SV)** are captured in the Data Acquisition module (red) and transported in an [open XML format](https://github.com/OpenPMU/OpenPMU/tree/master/XML_Datagrams) to the Phasor Estimation module (green).  The **estimated phasors** are transported in an [open XML format](https://github.com/OpenPMU/OpenPMU/tree/master/XML_Datagrams) to the Telecoms module (blue) for **onward communication** using protocols including IEEE C37.118.2, IEC 61850-90-5 and STTP.

The Data Acquisition stage is usually a hardware device measuring real data from a power system.  However, it is also possible to feed OpenPMU with simulated data from either our own [XML SV Simulator](https://github.com/OpenPMU/OpenPMU_XML_SV_Simulator) or from a simulation environment such as DIgSILENT.  The choice is yours!

### Repositories

Most of our code is written in Python and has been tested using Python 3.9.4.

We are organising a series of repos for various tools related to OpenPMU.  These include:

* **[OpenPMU Phasor Estimator](https://github.com/OpenPMU/OpenPMU_Phasor_Estimator):** A Python tool for producing synchrophasors from sampled values.  Presently private, you will need to request access.
* **[OpenPMU XML SV Simulator](https://github.com/OpenPMU/OpenPMU_XML_SV_Simulator):** Simulator which produces a stream of SV data as you would get from our BeagleBone Black GPS Disciplined ADC system.
* **OpenPMU Data SV Plotter:** A Python tool with a GUI for visualising sampled value data from either an ADC or simulation.


We'll be making these repos public soon once we have the source code well commented and explained.  In the meantime, [check out our papers](www.openpmu.org/publications).

If you're interested in collaborating, say hi on [Facebook](www.facebook.com/OpenPMU).

### Guide to PMU Technology

Read the [OpenPMU PMU Fundamentals](http://www.openpmu.org/pmu-fundamentals) guide to understand what a PMU is.

### Highlighted papers

* [GPS Disciplined Analogue to Digital Converter for Phasor Measurement Applications](http://ieeexplore.ieee.org/document/7931698/) (Open Access)
* [OpenPMU: Open source platform for Synchrophasor applications and research](https://ieeexplore.ieee.org/abstract/document/6039607/)
* [Synchronous islanded operation of an inverter interfaced renewable rich microgrid using synchrophasors](https://digital-library.theiet.org/content/journals/10.1049/iet-rpg.2017.0406)



