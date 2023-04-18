# TCL_Script_Modelsim
TCL template duolos for Modelsim

ModelSim Compile Script
This is a general script for compiling, recompiling and simulating VHDL/Verilog code using ModelSim. It is intended for rapid code writing and testing where small code modifications can be checked very quickly using few keystrokes. Once ModelSim is running in GUI mode and the script has been sourced then recompiling out-of-date files and rerunning a simulation requires two keystrokes: r for recompile and press the Enter key. The key features are:

Support for one or more libraries
Simple mechanism for recompiling out-of-date and dependent files
Easily specify waveforms for viewing
Easily specify waveform radices
Simple project time report
Specify SDF file for timing simulations
 
Notes
The Tcl variable library_file_list stores the library name(s) and files that should be compiled into each library. It is a two-dimensional Tcl formatted list. The first element is the name of a library, the second element is a list of files that should be compiled into that library. If there is more than one library then a third and fourth element should be written for the second library name and its list of files. And so on.

The order of libraries and files is significant, they should appear in order of dependency. The script will compile every file the first time. Subsequent recompiles will run through the list of files looking for a file that has been modified since the last compile time. The modified file and every file after it in the list will be recompiled.

The Tcl variable top_level keeps the library and name of the top level for elaboration. In fact the contents of this variable are used as the arguments to ModelSim's vsim command, so any valid options may be specified, for example:

set top_level {-t ps -sdftyp /uut=counter.sdf test_library.cfg_gate}
The Tcl variable wave_patterns can contain a list of signals or patterns that should be loaded into the wave window. For most block level testbenches just /* is enough. If no waves are required or the script is being used for command line simulations then this list can be left empty (nothing but white space).

The Tcl variable wave_radices is a two dimensional Tcl formatted list like library_file_list. The first element is a radix to use: hexadecimal, unsigned, binary etc. The second element is a list of wave signals for applying this radix to. There can be zero, one or more pairs of elements in this list.

To recompile out-of-date and dependent files type r and Enter. To force complete recompilation type rr and Enter. To quit without ModelSim confirming that you want to quit type q and Enter.

To start ModelSim and source this script from the command line, type this:

  vsim -do compile.tcl
Or, if ModelSim is already running with the correct working directory, type this in the ModelSim main window:

  source compile.tcl
You can save even more project time and become more productive when you learn more Tcl/Tk. Invest in your career development. Develop your scripting skills with Essential Tcl/Tk training from Doulos.
