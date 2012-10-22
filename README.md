dmp
===

<b>Draw Me a Pipeline</b> (or "<b><i>Dessine Moi un Pipeline</i></b>" in French) is a python tool to generate
a graphical representation of a CPU pipeline behaviour during simulation.

It is being developped in parallel with this project <a href="https://github.com/fallen/milkymist-mmu-simulation">[1]</a> which aims at allowing simulation of [MMU | noMMU]
LatticeMico32 softcore CPU.

Draw Me a Pipeline uses the pydot library to generate a diagram representing the changes in each of the CPU pipeline
stages during the simulation of the execution of a given binary file.

<b>Draw Me a Pipeline</b> represents interesting wire/register values conditioning the pipeline state changes
as well as stage inputs and outputs.

[1] -- https://github.com/fallen/milkymist-mmu-simulation