dmp
===

<b>Draw Me a Pipeline</b> (or "<b><i>Dessine Moi un Pipeline</i></b>" in French) is a python tool to generate
a graphical representation of a CPU pipeline behaviour during simulation.

It is being developped in parallel with this project <a href="https://github.com/fallen/milkymist-mmu-simulation">[1]</a> which aims at allowing simulation of [MMU | noMMU]
LatticeMico32 softcore CPU.

<b>Draw Me a Pipeline</b> uses the pydot library to generate a diagram representing the changes in each of the CPU pipeline
stages during the simulation of the execution of a given binary file. Early releases of <b>Draw Me a Pipeline</b> will only
support HTML rendering.

<b>Draw Me a Pipeline</b> represents interesting wire/register values conditioning the pipeline state changes
as well as stage inputs and outputs.

Requirements: 

On a Debian Squeeze machine: 

    $ sudo apt-get install python2.6 python-pydot python-argparse

How to use it:

    $ git clone https://github.com/fallen/milkymist-mmu-simulation.git # Clone the simulation repository
    $ git clone https://github.com/fallen/dmp.git # Clone the dmp tool to analyse simulation output
    $ cd milkymist-mmu-simulation
    $ source /opt/Xilinx/14.3/ISE_DS/settings32.sh # Sets environment up to use Xilinx tools 
    $ export PATH=$PWD/tools/h2a/:$PATH # Adds h2a tool in PATH to convert binary files to ASCII hex files
    $ make tools # Builds h2a tool
    
Uncomment "`define CFG_DRAW_ME_A_PIPELINE" in lm32_include.v

Comment other defines which could lead to text being written to the console during simulation (e.g. CFG_PIPELINE_TRACES, CFG_UART_ENABLED, CFG_VERBOSE_DISPLAY_ENABLED)
    
    $ make dmp # Runs the actual simulation and saves pipeline informations to dmp.data file
    $ cd ../dmp
    $ ./dmp --starttime 2700 --endtime 3000 ../milkymist-mmu-simulation/dmp.data

And there you are, <b>Draw Me a Pipeline</b> has generated an HTML visualization of the pipeline states during your simulation
and saved it under "output.html".

You can now open it with your favorite web browser!


[1] -- https://github.com/fallen/milkymist-mmu-simulation