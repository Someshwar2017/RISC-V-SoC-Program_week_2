# RISC-V-SoC-Program_week_2
<details>
  <summary>BabySoC Fundamentals & Functional Modelling </summary>
  <h3>Objective</h3>
  <p>To build a solid understanding of SoC fundamentals and practice functional modelling of
the BabySoC using simulation tools (Icarus Verilog & GTKWave). </p>
  <ol><li><h2>Theory (Conceptual Understanding)</h2></li>
    <ol><li><p><b>What is a System-on-Chip (SoC) ?</b></p></li>
      <p>A System-on-Chip (SoC) is an integrated circuit that combines all essential components of a computer system into a single chip. Unlike traditional boards with separate chips for processor, memory, and peripherals, an SoC brings them together to achieve:</p>
      <p><ul><li><i>Compactness </i>: Reduces physical size, enabling portable devices.</li>
<li><i>Energy Efficiency </i>: Shorter data paths and optimized power control.</li>
<li><i>High Performance </i>: Faster communication between components.</li>
<li><i>Cost-effectiveness & Reliability </i>: Fewer components, lower cost, fewer failure points.</li></ul></p>
<p>SoCs are used in smartphones, wearables, IoT devices, consumer electronics, and automotive systems.</p>
      <li><p><b>Components of a Typical SoC :</b></p></li>
      <p><ul><li><i>CPU (Processor Core) </i>: Executes instructions, manages data processing.</li>
<li><i>Memory </i>: RAM for temporary data, Flash/ROM for permanent storage.</li>
<li><i>Peripherals & I/O Ports </i>: Interfaces like UART, SPI, I²C, GPIO to connect with external devices.</li>
<li><i>Graphics / DSP Units </i>: Handle visuals, audio, and signal processing.</li>
<li><i>Power Management </i>: Ensures efficient use of energy, critical for battery-driven systems.</li>
<li><i>Interconnect (Bus/NoC) </i>: Links CPU, memory, and peripherals. Examples: AMBA AHB/APB/AXI.</li></ul></p>
      <p>Together, these components make the SoC a self-contained computing platform.</p>
      <li><p><b>Why BabySoC ?</b></p></li>
      <p>Modern SoCs are highly complex, making them difficult for beginners to study directly. BabySoC is a simplified, open-source model that captures the essence of SoC design while remaining small enough to understand.</p><p>Key features of BabySoC (VSDBabySoC):</p>
      <p><ul><li><i>RVMYTH CPU (RISC-V Core)</i> – open-source, simple, and customizable.</li>
<li><i>PLL (Phase-Locked Loop)</i> – generates stable clock signals to synchronize CPU and peripherals.</li>
<li><i>10-bit DAC (Digital-to-Analog Converter)</i> – converts digital values into analog signals for audio/video output to devices like TVs or phones.</li></ul></p>
      <p>This miniaturized system allows learners to explore :</p>
      <p><ul><li>How digital cores interact with analog components.</li>
<li>Data flow from instruction execution to external device output.</li>
<li>The importance of synchronization (via PLL) in SoC design.</li></ul></p>
<p>Thus, BabySoC acts as a learning bridge between theory and real-world chip integration.</p>
      <li><p><b>Role of Functional Modelling in SoC Design :</b></p></li>
      <p>Before moving into RTL design and physical implementation, SoC engineers create a functional model of the system. This step is critical because it allows verification of the SoC’s behavior at a higher level of abstraction, without being tied down to detailed hardware descriptions.</p>
      <p><ul><li><i>Defination</i> :-</li>
      <p>Functional modelling is the process of creating a software-level or high-level hardware description that mimics the intended behavior of the SoC. It focuses on what the system should do, not how it is implemented in gates or transistors.
        <p align="left"> 
  <img src="https://github.com/user-attachments/assets/b4a70579-b718-4cc7-9b65-d07c61ae1534" align="right" width="500" height="500">
</p>
        <li><i>Purpose</i> :-</li>
      <p><ul><li>Validate the architecture of the SoC before RTL coding.</li>
<li>Ensure that the CPU, memory, and peripherals interact correctly.</li>
<li>Provide a golden reference model for RTL designers to compare against.</li></ul></p>
        <li><i>Benefits</i> :-</li>
        <p><ul><li><i>Early Error Detection</i> : Functional issues are caught before expensive RTL or layout stages.</li>
<li><i>Faster Development</i> : Simulation is quicker at this stage compared to RTL or gate-level simulations.</li>
<li><i>Reduced Cost</i> : Avoids rework in later design stages, which is more time-consuming.</li>
<li><i>Clear Design Reference</i> : Acts as a blueprint for hardware engineers.</li></ul></p>
      </ul></p>
      <li><p><b>Conclusion :</b></p></li>
      <p>Understanding SoC design requires grasping the integration of CPU, memory, peripherals, interconnects, and analog components into one chip.</p>
      <p>The BabySoC project provides a practical and accessible platform to :</p>
      <p><ul><li>Learn SoC fundamentals in a manageable scope.</li>
<li>Explore the interaction between digital logic and analog interfacing.</li>
<li>Appreciate the role of functional modelling in bridging conceptual design and physical implementation.</li></ul></p>
    </ol>
    <li><h2>Labs (Hands-on Functional Modelling)</h2></li>
    <p>Lab Reference <br>
[VSDBabySoC Project by Hemanth Kumar DM]<br>(https://github.com/hemanthkumardm/SFAL-VSD-SoCJourney/tree/main/12.%20VSDBabySoC%20Project)</p>
      <p>Tools Used</p>
<table>
  <tr>
    <th>Tool</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td><b>Icarus Verilog (iverilog)</b></td>
    <td>Compile and simulate Verilog code</td>
  </tr>
  <tr>
    <td><b>GTKWave</b></td>
    <td>View and analyze simulation waveforms</td>
  </tr>
</table>
<p><b>Step 1: Clone the BabySoC Project</b> [VSDBabySoC](https://github.com/manili/VSDBabySoC.git)</p>
<p><pre>
git clone https://github.com/hemanthkumardm/SFAL-VSD-SoCJourney.git
cd SFAL-VSD-SoCJourney/12. VSDBabySoC Project</pre></p>
</p>
    <p><b>Step 2: Step 2 – Pre-Synthesis Simulation</b></p>
    Compile the design and run pre-synthesis simulation:
    <p><pre>iverilog -o output/pre_synth_sim/pre_synth_sim.out -DPRE_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v src/module/vsdbabysoc.v
cd output/pre_synth_sim
./pre_synth_sim.out
</pre> This generates a pre_synth_sim.vcd file for waveform viewing.</p>
   <p> <img src="https://github.com/user-attachments/assets/3ce1041d-b877-4820-b105-30f63a64a585" alt="Description"></p>
    <p>Observation:
<ul><li>The clock (CLK) signal shows regular periodic toggling.</li>
<li>The reset signal is asserted low at the beginning, holding the system inactive during initialization.</li>
<li>Once reset is released, data begins flowing from the RISC-V core (RV_TO_DAC[9:0]) to the DAC output.</li>
<li>The smooth increment in data values verifies the correct functioning of the core → DAC data path in the RTL design.</li></ul>This confirms that the BabySoC RTL modules are functionally correct before synthesis.</p>
    <p><b>Step 3 – View Waveforms in GTKWave</b></p>
    <p><pre>gtkwave output/pre_synth_sim/pre_synth_sim.vcd</pre>Analyze reset, clock, and dataflow behavior.</p>
    <p><b>Step 4 – Post-Synthesis Simulation</b></p>
    Run post-synthesis simulation using the synthesized netlist:
    <p><pre>iverilog -o output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v output/synthesized/vsdbabysoc.synth.v
cd output/post_synth_sim
./post_synth_sim.out</pre>Then view the resulting post_synth_sim.vcd file in GTKWave.</p>
     <p> <img src="https://github.com/user-attachments/assets/4ff91825-20bc-48d4-bb43-6635bb45b4d0" alt="Description"></p>
  <p>Observation:
  <ul><li>The post-synthesis waveform maintains consistent clock and reset behavior as in the pre-synthesis simulation.</li>
<li>The core output and DAC output match the RTL results, confirming logical equivalence between synthesized and behavioral designs.</li>
<li>Slight signal delay (timing difference) observed due to gate-level modeling — expected after synthesis.</li></ul>This verifies that synthesis preserved the intended BabySoC functionality.</p>
  </ol>
   <p align="center"><b>✨ Thank you for reading! ✨</b></p>
</details>
