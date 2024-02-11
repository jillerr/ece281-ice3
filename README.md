# ECE 281 ICE 3: FullAdder with Top Level Design

**Fork** this repo.

[ICE 3 instructions](https://usafa-ece.github.io/ece281-book/ICE/ICE3.html)

Targeted toward Digilent Basys3. Make sure to install the [board files](https://github.com/Xilinx/XilinxBoardStore/tree/2018.2/boards/Digilent/basys3).

Tested on Vivado 2018.2.

---

## GitHub Actions Testbench

You can *optionally* enable Actions on your fork.

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

First, the workflow uses GHDL to **analyze** all `.vhd` files in `src/hdl/`.

Then it **elaborates** the *any* entity with the name `*_tb`.

Finally, the workflow **runs** the simulation. If successful then it will quietly exit with a `0` code.
If any of the `assert` statements fail **with** `severity failure` then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
Assert statements of other severity levels will be reported, but not fail the workflow.

![successful waveform of full adder](fulladderwaveform.png)

##documentation
Worked with C3C Alexander Sick who informed me of the syntax for the assert statments within the testbench. He also explained to me the difference between a port, an entity, and a source. Asked Col Trimble for assistance and he informed me that to fun the test bench you must include the corresponding .vhd file as a simulation source.