nRF51x22 Barebones Development Board
====================================

![rendering of board front](https://raw.github.com/nocko/nRF51-devel/master/nRF51-top.png)

Make your own! ($9 for 3 boards + ~$10/ea. in parts) 
----------------------------------------------------

 1. In a web browser: Browse to [oshpark.com](http://oshpark.com),
    select "Get Started Now", then "Select a file on your
    computer". Select gerbers/nRF51.zip from the repo. Fill out the
    name, contact and billing information.

 1. Order the parts. Current BoM Shopping Cart (for three boards) @
    Mouser:
    http://www.mouser.com/ProjectManager/ProjectDetail.aspx?AccessID=88e3ea2c37

 1. Practice your [reflow soldering
    technique](https://www.sparkfun.com/tutorials/59) while you wait
    for parts and boards to show up.

 1. Fun!

Make it better
--------------

If you've never used gEDA before, start with this simple
[tutorial](http://hobby-electrons.sourceforge.net/tutorials/gEDA/index.html). Once
you're familiar with the gschem and pcb UI feel free to clone the repo
in github with the [fork button](https://github.com/nocko/nRF-devel/fork)
or clone the repo using the CLI:

    git clone https://github.com/nocko/nRF51-devel

Interesting Files in the Repo
-----------------------------

* nRF51.sch:

	gschem schematic. Edit this file with *gschem* to add or
	remove components or change the way the components are
	connected.

* nRF51.pcb:
 
  	pcb layout. Edit with *pcb* to change the locations of the
	components on the board or to place new components added in
	gschem.

* attrib:

	template files for the fields that should appear in a bill of
	materials file generated by *gnetlist*

* project:

	gsch2pcb project file. Setup options to import tdcs.sch into
	board.pcb. Options like path to pcb footprints, names of
	schematics to process, and output name.

* gafrc:
 
       Options for gschem. Primarily the location of local schematic
       symbols

* gerber/*:
	
	Gerber files generated from the *.pcb files. generate-gerbers
	builds the gerbers and creates a zipfile(s) that can be sent
	to [OSH Park](http://oshpark.com/) without modification.

* bom.txt:

	Bill of Materials, the components you need to buy to populate
	the board. Eventually this will auto generate via gnetlist,
	but for now the digikey part numbers are added manually.


General Workflow
----------------

1. Add new components or change the circuit diagram in nRF51.sch using
*gschem*.

1. Run: ```gsch2pcb project```

1. Follow the instructions provided by gsch2pcb to insert the new
components.

1. Adjust the pcb layout using *pcb* and save file

1. Make gerbers/oshpark zip files: ```cd gerbers; ./generate-gerbers.sh```

1. Recreate the BoM: ```gnetlist -g bom -o bom.txt <project>.sch```

License
-------

All files are licensed [CC-BY
3.0](http://creativecommons.org/licenses/by/3.0/) unless otherwise marked. Full text of the
CC license is available in LICENSE.txt
