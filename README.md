FIFO Verification using SystemVerilog
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Overview
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

A synchronous FIFO written in Verilog, verified with a layered SystemVerilog testbench (Generator, Driver, Monitor, Scoreboard). Randomized read/write transactions are applied through mailboxes and self-checked against expected FIFO behavior.

Design Under Test
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

Synchronous FIFO with parameterized data width and depth.

Write — stores data on wr_en when the FIFO is not full
Read — retrieves data on rd_en when the FIFO is not empty
Full/Empty flags — indicate FIFO status
Synchronous control — all operations gated by clock and reset


Verification Environment
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
| Component | Role |
|-----------|------|
| `fifo_if` | Interface bundling FIFO signals |
| `transaction` | Randomized stimulus object |
| `generator` | Produces randomized read/write transactions |
| `driver` | Drives transactions onto the DUT |
| `monitor` | Samples DUT inputs and outputs |
| `scoreboard` | Tracks expected FIFO contents and checks DUT output |
| `environment` | Connects generator, driver, monitor, and scoreboard |
| `tb` | Top-level: instantiates DUT, generates clock/reset, and starts the verification environment |
Components communicate through SystemVerilog mailboxes. The scoreboard maintains a reference model of FIFO contents and flags any mismatch between expected and actual data, along with full/empty behavior.


Verification Flow
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Generator → Driver → FIFO (DUT) → Monitor → Scoreboard

Simulation

Run on ModelSim/QuestaSim and EDA Playground; waveforms viewed in EPWave.
Waveform
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
<img width="1839" height="369" alt="fifo_waveform" src="https://github.com/user-attachments/assets/516e4653-ea40-44d2-9eb9-4af2ac480d9d" />


Signals of interest: clock, reset, write enable, read enable, input data, output data, full flag, empty flag

Sample Output
text
GENERATOR → DRIVER → MONITOR → SCOREBOARD
SCB: PASS
Expected = XX
Actual   = XX

Author
Suhani Deshmukh
suhani.deshmukh1612@gmail.com
7387568151

