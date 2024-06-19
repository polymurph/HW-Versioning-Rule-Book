# HW-Versioning-Rule-Book
Hardware Versioning Rule Book

This rule book definesthe rules and the philosophy on how to versioncontrol a Printed Circuit Boad Assemblied (PCBA).

## Versioning philosophy

Every Printed Circuit Boad Assemblied (PCBA) has two categorys of files.
-  Design Files
-  Production Files

The design files incorperates layout, schematics, Bill of Material (BOM) and possible additional documentation.
The produzction files incorperate gerber files, ODB++, PCB stackup definitions, etc.

To be able to achieve clarity in tracking the different versions of hardware a semantic code system is defined.
Any files related to the PCBA in later explained two categor categories must contain the respective semantic code.

These rules also inshure clarity towards any related firmware 


## Semantics

V0.0.0

Major.Minor.Patch

e.g.
Schema 	V0.0.0
BOM 		V0.0.0
PCB		V0.0

### Major

Form, fit and function change

The Major number indicates and changes which break backwards compatability with older versions.
The following lists show categorically differenciated examples of changes which are considered major.

Electromechanical and Mechanical changes.
-	removing or moving mounting holes
-	reshaping the outline of the PCB
-	changing the PCBA material and/or thickness
-	Moving connectors

Any changes to the design
-	Change of microcontroller
-	Adding or removing Connectors
-	Adding or removing features e.g. adding a Temperature sensor
-	Adding power input protection circuit

Any changes to the electronic interface
-	Changing connector pinouts

For any given major change the first digit in the version code must be iterated. This number must be applyed to all the files related to the PCBA. Even if certain changes do not affect certain files. This is done to prevent any confusion and maintains in clarity in the versioning history

### Minor

Changes which incorporate a difference int PCB 
e.g. PCBA V1.1 and V1.2 have the same functionality but the layout was changed due to a change of a resistor from 0805 to 1206 footprint. 
-	Any changes to Silkscreen
-	Changing component sizes
-	Footprint changes
-	Solving faulty footprint
-	Solving missing conenction
-	

Version change e.g.
Schema	V0.0.0		->	V0.1.0
BOM		V0.0.0		->	V0.1.0
PCB		V0.0  		->	V0.1

All PCBA V0.X are interchangeable form the implementation point of view.

### Patch

Only changes to the BOM or Schmeatics no changes to the PCBA in any form
e.g.
-	replacing a 100nF 25V X7R 1206 to a 220nF X7R 1206. This 
-	Replacing an OPAMP but keeping the footprint and pinout same. 

Version change e.g.
Schema	V0.0.0		->	V0.0.1
BOM		V0.0.0		->	V0.0.1
PCB		V0.0  		->	V0.0

For more rigerose tracking of the PCBA it is allowed to add by any means the possibility of adding the patch number on to the PCB after assembling or modification to be able to identify what path is implemented on the PCBA. One example is to add in silk an area for marking the patch version onto the PCB.

## Optional Topics

- adding serial numbers to PCBA which are linked to a specific semantic

## sources
[Versioning in Hardware Design: Tracking Iterations and Improvements](https://fastercapital.com/content/Versioning-in-Hardware-Design--Tracking-Iterations-and-Improvements.html)
