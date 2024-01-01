---
title: Research topics and publications
short_title: Research
bibliography:
  - publications.bib
---

## Research interests

Design of asynchronous circuits, and in particular bundled-data protocols [@10.1109/SBCCI.2016.7724066] and verification of such circuits [@10.1109/ASYNC.2017.16].

High-level synthesis for event-based systems [@10.1109/EBCCSP.2016.7605252] and synchronous-to-asynchronous design conversion [@10.1109/ICECS.2017.8292047; @10.1007/978-3-030-60939-9_14]

Applications of event-driven circuits to signal processing, such as windowing techniques [@10.1109/EBCCSP.2017.8022807], and finite-impulse response filters [@10.1109/SAMPTA.2015.7148894; @10.1109/ISCAS.2017.8050379; @10.1109/EBCCSP.2019.8836742].

## PhD Thesis [-@simatic2017]

**Title** Design flow for ultra-low power: Non-uniform sampling and asynchronous circuits \
**Advisor** Laurent Fesquet \
**Co-advisor** Rodrigo Possamai Bastos

**Abstract**
Integrated systems are mainly heterogeneous systems with strong power consumption constraints. They embed actuators, sensors and signal processing units. To limit the energy consumption, they can exploit event-based techniques, namely non-uniform sampling and asynchronous circuits. Indeed, they allow cutting drastically the amount of sampled data for many types of signals and reducing the system activity. To help designers in quickly developing platforms that exploit those event-based techniques, we elaborated a design framework called ALPS. It proposes an environment to determine and simulate at algorithmic level the sampling scheme and the associated processing in order to select the most efficient ones depending on the targetted application. ALPS generates directly the analog-to-digital converter based on the chosen sampling parameters. The elaboration of the processing unit uses a synchronous high-level synthesis tool and a desynchronization method that exploits specific asynchronous protocols to optimize the circuit area and power consumption. Finally, gate-level simulations allow analyzing and validating the energy consumption before continuing with a standard placement and routing flow. The conducted evaluations show a reduction factor of 3 to 8 of the consumption of the automatically generated circtuis. The flow ALPS allow non-specialists to concentrate on the optimization of the sampling and the processing in function of their application and to reduce the circuit power consumptions by one to several orders of magnitude.
