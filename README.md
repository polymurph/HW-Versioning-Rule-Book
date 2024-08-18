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

Here is an example of a packet which includes all production files for a PCBA

File name containing all the relevant design and production files

```bash

PCBA_name_V0_0_0_2024_08_18/
├── schema_PCBA_name_V0_0_0_2024_08_18.sch
├── prod_PCBA_name_V0_0_2024_08_18.zip
├── BOM_PCBA_name_V0_0_0_0_2024_08_18.xlsx
└── ALTLIST_PCBA_name_V0_0_0_0_2024_08_18.xlsx

```

Major.Minor.Patch.Year.Month.Day

e.g.
Schema 	  V0.0.0
BOM 		  V0.0.0.0
ALTLIST   V0.0.0.0
PCB		    V0.0

THe 

### Major

The Major number indicates the main version of the PCBA at hand. It changes with every break regarding backwards compatability with older versions.
The following lists show categorically differenciated examples of changes which are considered a major change.

**Electromechanical and Mechanical changes**
-	removing or moving mounting holes
-	reshaping the outline of the PCB
-	changing the PCBA material and/or thickness
-	Moving connectors

**Any changes to the design**
-	Change of microcontroller
-	Adding or removing Connectors
-	Adding or removing features e.g. adding a Temperature sensor
-	Adding power input protection circuit

**Any changes to the electronic interface**
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

E.g. exchanging a 100nF 0805 X7R 25V with a 220nF 1206 X7R 50V 

Schema	Vn.n.n		->	V[n].[n + 1].0 component change

BOM		Vn.n.n		->	V[n].[n + 1].0 componant change

PCB		Vn.n  		->	V[n].[n + 1] footprint change in layout

The minor change has an impact on the schema, BOM and the PCB.

E.g. exchanging an OPAMP LM358 from SOIC 8 to TSSOP 8

Schema	Vn.n.n		->	V[n].[n + 1].0 component change

BOM		Vn.n.n		->	V[n].[n + 1].0 componant change

PCB		Vn.n  		->	V[n].[n + 1] footprint change in layout

The minor change has an impact on the schema, BOM and the PCB.

For each Minor change the patch number is set to 0.

For a given PCB Version number V[n].[x] with the same Major version denoted with n and any minor version denoted as x, all PCBAs are compatible.

### Patch

The patch number indicates the patchwork version of the PCBA at hand. It changes with every change that does not alter the PCB. Any patch change will be compatible with the PCB version at hand.
The following lists show categorically differenciated examples of changes which are considered a patch change.

Only changes to the BOM or Schmeatics no changes to the PCBA in any form
e.g.
-	replacing a 100nF 25V X7R 1206 to a 220nF X7R 1206. This 
-	Replacing an OPAMP but keeping the footprint and pinout same. 


E.g. exchanging a 100nF 1206 X7R 25V with a 220nF 1206 X7R 25V

Date of change 2024.08.11

Schema   V0.0.0  ->	V0.0.1

BOM      V0.0.0  ->	V0.0.1

PCB      V0.0   ->	V0.0 no layout changes

The patch only has an impact on the Schema and the BOM. It has no implications with the PCB (no layout change).

E.g. excluding placement of certain circuitry without any functional limitations (e.g. debug pin, debug LED, etc.)

Schema	V0.0.0		->	V0.0.1 parts are marked as do not place (DNP) 

BOM		V0.0.0		->	V0.0.1  parts are excluded from BOM

PCB		V0.0  		->	V0.0 no layout changes

The patch only has an impact on the Schema and the BOM. It has no implications with the PCB (no layout change).


For more rigerose tracking of the PCBA it is allowed to add by any means the possibility of adding the patch number on to the PCB after assembling or modification to be able to identify what path is implemented on the PCBA. One example is to add in silk an area for marking the patch version onto the PCB.

### Last number for BOM and ALTLIST

The BOM ant the alternatve parts list have an additional number. This number represents how the bom is made up. for instance R&D creates a BOM for a medical application. This BOM is the first initial one e.g. V0.0.0.0. as it is still used as a prototype. The BOM may be representing the parts wanted functionally but neglecting the sourcing aspect. In this BOM there may be some issues e.g. not recomended for new designs, parts which are intended for the automotive market. These parts in this case mostly can be replaced by alternative parts which so not impy any design changes to e.g. pinout, footprint etc. If wanting to only change the

### Date

The date denotes when the files where published as an additional feature for clarity.
More important is the indication of redactional changes. These are changes which alter only the metadata of the PCBA. This means no changes to the design and production files technical content. It denotes only changes e.g. Typos, adding better documentation in schematics. This does not include typos in the BOM content. These typos will require an iteration if the last number.
When wanting to release the redactional changes the dates of all files must be changed including the file name. Like this it si possible to see that a file with the same version number but different date will be technically idential. the production of both will be identical.

Every time any form of new release is made the date will be changed to the publishing date. This includes all the major, minor, patch and last number changes.


## Optional Topics

- adding serial numbers to PCBA which are linked to a specific semantic

## sources
[Versioning in Hardware Design: Tracking Iterations and Improvements](https://fastercapital.com/content/Versioning-in-Hardware-Design--Tracking-Iterations-and-Improvements.html)
