**Sequence Learning in a Spiking Neural Network** (Python Implementation)

This is a 100% Python implementation of the 2023 paper "Sequence learning in a spiking neuronal network with memristive synapses" (Bouhadjar et al.).

This project builds a complete Spiking Neural Network (SNN) from scratch to simulate how a brain-inspired system can learn sequences. It implements a Python-based "phenomenological model" of a memristive synapse and the biological STDP learning rules to replicate the paper's core findings on learning, memory, and robustness.

**Project Overview**

Traditional AI is powerful but energy-intensive. Brain-inspired (neuromorphic) computing aims to build new systems that mimic the brain's efficiency. This project explores a key model from this field by simulating two main components:

- SpikingNetwork (The "Brain" & "Controller"): A network of Leaky Integrate-and-Fire (LIF) neurons that communicate using "spikes." This class acts as the "Controller," implementing the paper's Spike-Timing-Dependent Plasticity (STDP) learning rule.

- BinarySynapse (The "Hardware"): An object that simulates a memristive (ReRAM) synapse. Instead of complex circuit physics, it implements the paper's behavioral model (Eq. 2 & 3), which includes an internal "memory" (Permanence) that "flips" the synapse ON or OFF.

**How the Learning Works (STDP)**

The network learns in an unsupervised, local way:

- Default: When a neuron fires, it sends a weak "depress" (weaken) signal to all its connections.

- Learning: If a "pre-neuron" fires and then a "post-neuron" fires just after it (within a 4-50ms "plasticity window"), that specific connection gets a strong "potentiate" (strengthen) signal that overrides the "weaken" signal.

Over time, only the connections that are part of the "correct" sequence are strengthened, while all other random connections fade away.

**Model Scope: A "Toy Model" for Clarity**

To clearly demonstrate the paper's core mechanisms, this project implements a simplified "toy model":

- This Notebook: Simulates a smaller, 3-club network (A-B-C) learning one simple, linear sequence (A->B->C).

- The Paper: Simulates a large, 12-club network (A-L) learning four complex, overlapping sequences (e.g., A->D->B... and F->D->B...).

This simplification is deliberate. It allows us to isolate and clearly visualize the STDP learning rule in action. The underlying principles and code logic are a faithful implementation of the paper's design.

