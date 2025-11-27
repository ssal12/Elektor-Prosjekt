README – PCB Design Notes
————————————

The PCB layouts provided in this project are intended as educational prototypes and reference material. They were designed by students and, while they adhere to basic design rules (clearances, trace widths, two-layer routing with ground reference planes, mounting holes, etc.), they haven’t been reviewed or optimized by a professional PCB designer. Therefore, any reuse in a demanding application should involve a thorough redesign.

Board-specific comments
———————————

1. Microphone Preamplifier PCB

- This is the most refined of the three boards.
- The board is compact, with short signal paths between the input connector, the JFET bias network, the THAT1512 preamplifier, and the output connector.
- The routing is relatively clean and direct; analogue signal traces are separated from the DC-DC converter section, and decoupling capacitors are placed close to the NMA0515SC converter and the preamp IC.
- A largely continuous bottom-layer ground plane is used, with local pours around the supply section.
- Further improvements are possible (e.g., more explicit star-grounding at the input, additional shielding around high-impedance nodes), but this layout serves as a reasonable starting point for a low-noise preamp.

2. Single-Supply Class-D Amplifier PCB

- This board represents an intermediate level of quality between the preamp and the dual-supply amplifier.
- The high-current path from the supply connector, through the bulk capacitors, MOSFETs, and output inductor is routed with reasonably wide traces and kept on the upper half of the board. A vertical “VCC spine” along the left side distributes the supply to the power stage.
- The modulator (555, LM393, and associated components) is placed toward the lower edge, with shorter local traces but less shielding from the power section than would be ideal in a production design.
   - Copper pours are used sparingly; most return currents flow in a largely unbroken bottom-layer ground region.

For further iterations, the layout could benefit from tighter current loops around the half-bridge and output filter, clearer separation between power and small-signal areas, and more systematic stitching between the top traces and the ground plane.

3. Dual-Supply Class-D Amplifier PCB

- The dual-supply (bipolar) amplifier PCB is functionally complete but the least tidy of the three designs.

- Wide copper pours and broad traces are extensively used on the top layer to distribute both +V and –V rails from the fuse/connector area to the half-bridge and output filter. This provides low DC resistance but results in irregular current paths and large copper “islands” that are not always well-controlled.

- The central power stage and the lower-right modulator/driver section are relatively dense, with several long signal traces weaving through power copper. This is acceptable for a lab prototype but would be sub-optimal for EMI and reproducibility in a production context.

- The bottom layer is predominantly a ground/reference plane, but in some regions it is cut up by numerous vias and pours, which can fragment return paths.

- A future revision should rationalize the power distribution (clear, short high-current loops; well-defined star points), reduce unnecessary copper, and more clearly isolate the analogue/PWM circuitry from the high-di/dt switching node.

Summary
———

Overall, the PCBs are suitable for demonstrating the concepts discussed in the report and for laboratory prototyping, but they should not be regarded as optimized or production-ready layouts. Anyone reusing these designs is strongly encouraged to treat them as first-pass examples and to perform a full layout review and at least one additional revision cycle before deploying them in a more demanding setting.
