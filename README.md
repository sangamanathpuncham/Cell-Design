# Cell-Design 


    ------->input------>GUNA----->OUTPUT

    TIMING CHAR.   POWER CHAR.  NOISE CHAR.


Reading the models

Extracted spaice netlist

Recognize the behavior of the buffer

Read the subcircuit of the inverter

Attach the required power sources

Apply the stimulus

Add the output load cap

Output Analysis


1)Timing Characterization
---

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/511a5c66-088d-45b2-99bd-8ea1a47b6fda)

Propogation Delay:
---
![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/4ffc80c3-6b3d-43a3-8f5b-70de5217c80b)


![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/7fb92e7e-97cd-44e7-bc80-b2ea8e612907)

Transition Time:

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/05208bd2-88ac-45d6-85af-4eec3ff74689)

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/4fbb0dc7-b317-4f32-8aa2-542c5225cef5)

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/52a1e6d8-571b-440e-bd7c-951da6772582)



16-MASK PROCESS OF INVERTER:
-----

1-) Selecting a substrate:
---

selecting body/substrate material (P-substrate)

2-) Creating active region for transistors:
---

first create isolation between active region pockets by SiO2, then perform Si3N4 deposition, then photoresist deposition, and then apply photolithography (part of photoresist is covered 

by mask to protect it against UV light). Areas that are not protected against UV light are then washed out using developing solution and etching is done, then photoresist is chemically 

removed. Then we place CMOS in oxidation furnace,and field oxide is grown (process is called LOCOS or Local Oxidation of Silicon). After that, Si3N4 is stripped using hot phospheric acid.

3-) N-well and P-well formation:
----

Photoresist is deposited and mask is used to define the protected area. UV light reacts with exposed area, and then we wash the area which is unprotected. After that, the mask is removed 

(this is lithography). Ion implemention by Boron for P-well is then done, followed by ion implementation of Phosphorous for N-well formation (after photoresist, mask application, and 

wash out). Then the CMOS is put in a high temperature furnace for a high temperature for a long time, which will diffuse the N-well and P-well (the pockets). In N-well the pmos will be 

created and in P-well the nmos will be created.

4-) Formation of gate terminal: 
----

the nmos and pmos gates are formed by depositing photoresist, using mask, exposing UV, applying wash out, removing the mask, doping with Boron to modify the doping concentration in the P-

well. Similar steps are repeated for P-well to control the threshold voltage or doping concentration in the N-well. Extra oxide is diluted then re-grown again to give high quality oxide. 

A polisilicon layer is then deposited to form the gate, then N-type material is doped on the gate to make it low resistance. Then photoresist is dumped, mask is used, unprotected 

material is washed out, mask is removed, and the remaining areas of polisilicon are etched away.

5-) Lightly Doped Drain (LDD) formation:
---

LDD is formed to prevent hot electron effect and short channel effect: P+, P-, P doping profile is needed for pmos and N+, N-, N profile is needed for nmos. Photolithography is applied, 

Phosphorous is doped to create N- implants on P-well side. The lithography is repeated for N-well side and we get P- implant after doping Boron. A thick Si3N4 or SiO2 is deposited on 

whole material and plasma anisotropic etching takes place to create the side-wall spacers where source and drain will be later affected in next step.

6-) Source and drain formation:
-----

think layer of screen oxide is added to avoid channelling during implantation. Then after photolithography, Aresenic implantation/doping takes place above P-well (below side-wall 

spacers). Then after photolithography, Boron implantation/doping takes place above N-well (below side-wall spacers). The material is put in high temperature furnace (called high 

temperature annealing).

7-) Contacts and local interconnect formation: 
----

Etching/removal of screen oxide by HF solution. Then Ti is deposited on material for low resistant contacts using sputtering (hitting Ti by Ar+ and the then Ti will be deposited on the 

substrate with heating). Then lithograpphy is used, and RCA cleaning is used to etch TiN. Result = TiN used only for local communication.

8-) Higher level metal formation: 
---

A thick layer of SiO2 doped with phosphorous or boron is deposited on the material. CMP is used for planarizing the wafer (polishing it), then 

photolithograpphy is used in areas where we want the metal to be formed, then TiN is deposited. Tungsten is then deposited, followed by CMP again. Al is then deposited on the material, 

and photolithography is used. Result is we get the first layer of metal. To get higher layers, SiO2 is deposited again, CMP is used, lithography is used, TiN is deposited, Tungsten is 

deposited, followed by CMP again. Al is then deposited on the material, and photolithography is used. The result is a metal layer which is higher and thicker (thicker Al). Si3N4 is 

deposited on top to protect the whole chip. Finally, mask16 is used to open contact holes on this top layer and connect the highest metal layer to the top.

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/ffe38428-8b8d-43e0-9e98-e9a5a18d3f58)


fabrication
---
In CMOS magic layout the first layer is called the local interconnect layer or Locali. The P diffusion and N diffusion regions with Polysilicon verify that this is the layout of a CMOS 

inverter. Also, drain and source connections are another sanity cehck: drains of both pmos and nmos are connected to output port (Y) and the sources of nmos/pmos are connected to GND/VDD 

respectively (moving cursor and clicking S twice helps us identify the connections in magic).

Library Exchange Format (LEF): A format that tells us about cell pins and boundaries, VDD and GND lines. It contains no information about the logic of circuit and is also used to protect the IP.

The technology file is a one setup file that tells magic everything it needs to know about a project (all layer types, patters, connectvitity, DRC rules, GDS generation rules, rules to 

read LEF and Def files, rules for interactive wiring, etc...). There are two sections: CIF and GDS styles. CIF is human readable.

Standard cell from the repo:

https://github.com/nickson-jose/vsdstdcelldesign.git


![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/96c4c6cf-997e-45f1-b551-2ffb6aa0bfae)

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/11bfaa54-0d18-4ef1-848a-a4a12de51f53)


Extract the Spice deck:
----

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/c05473f3-bc06-4f37-9e2b-ec887d8a0692)

Spice deck:
---

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/29d98063-f137-4ef9-abef-793713023fbb)


Changed spice deck:
--
![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/d5ba818e-daaa-420b-8720-c810edd7e780)

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/f14474c3-94c1-494a-be5c-dad9887fb975)

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/6968f295-a3f2-4c79-b25e-8315b82ae66d)


![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/7cc88019-c290-4843-8a19-293879d36029)

    Rise Trasition = 2.1800 - 2.1519 =0.0281ns(for 20%)
    Rise Transition=2.19633 - 2.12014=0.7619ns(for 80%)
    Fall Transition=4.0801 - 4.0398 = 0.403ns(for 80%)
    Fall Transition=4.06619 -4.01946= 0.0467ns(for 20%)

    Rise delay = 2.1774 - 2.1503 = 0.271ns ( for 50%)

    Fall delay = 4.0530 - 4.0497 = 0.0033ns (for 50%)

Extraction of LEF:
-----
1)for std cell input and output ports lies on the intersection of H and V tracks

2)width of the std cell in the odd multiple of no of tracks of horizontal pitch

3)height should be odd multiple of no of tracks of vertical  pitch

![image](https://github.com/sangamanathpuncham/Cell-Design/assets/132802184/b3ad6e7a-d7fa-46f5-97b7-d3c50be67165)


    




