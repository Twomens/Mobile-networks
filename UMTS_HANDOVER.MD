# UMTS Handover

This document will go in detail over the different **handover methods** present in UMTS. 
## Handover
In cellular communication, the handover is the act of the UE **switching** from one cell or sector to another, to provide a **seamless experience** while in motion. One example would be to prevent a call between two users from dropping constantly if one of those users were to be moving to a different cell.
## UMTS handover types
UMTS defines several types of handover, depending on what the UE is switching to. All of those handovers happen only when the **UE is in traffic**. 

### Hard handover
The hard handover means that the old link is broken **before** the new one is established. This method is only selected when soft and softer handover is not feasible. Although the link is broken, the handover should still feel seamless to the user, but there is a possibility of the user noticing a short break.
This type of handover happens when 
+ Moving between adjacent cells that use **different frequencies**.
+ When moving to one cell to another where no capacity is available and a change of frequency is needed
+ When implementing a mode change

Here is a simplification of the process of a hard handover. 
+ The network decides a handover is required dependent upon the signal strengths of the existing link, and the strengths of broadcast channels of adjacent cells.
+  The link between the existing NodeB and the UE is broken.
+  A new link is established between the new NodeB and the UE.

> Since the link is broken first, if issues prevents the creation of the
> new link, like the new cell not having the capacity to support the new
> link, the connection **may be dropped.**

### Soft handover
Soft handover happens when the UE can connect to **multiple** cells at the same time, 
in other words when the UE is in a **overlapping coverage area** of multiple cells. In soft handover, links to new base station is established **before** breaking the link with the old one. This provides a more reliable and seamless way to perform the handover.

For soft handover to be possible, the two adjacent cells need to be using the **same frequency**. This type of handover has a few advantages and drawbacks, compared to the hard handover.
+ It has a better success rate.
+ It reduces connection drops.
+ But it uses more power, as the network needs to maintain two links and the UE also needs to combine the frames fron the two NodeBs.

### Softer handover
Softer handover is similar to soft handover. The only difference is that the new cell is from the **same NodeB** as the old one. This type of handover simplifies the combining of links in the network as they can be done at the NodeB level instead of higher in the chain.
Softer handover typically happen thanks to sector overlap or multipath propagation resulting from reflections from buildings.

### iRAT handover
There are also handovers between UMTS networks and other networks like GSM but they are out of scope for this project, so we won't talk about them here. 

## When to switch
All of the previously cited handover methods use similar methods for knowing when to execute the handover. The UE measures some RF criteria (signal level, Connection quality, power level propagation delay) and traffic criteria (e.g. current traffic loading per cell, interference levels, maintenance requests, etc.) of the different cells it can connect to, and sends the information to the network on a regular basis. When the network deems a handover needed, using parameters set by the operator, the procedures as described above are followed, according to the type of handover that can be executed. 

Here, we will use the RSCP (Received Signal Code Power) as our criteria for handover. The handover will be executed if one of those requirements is met :
+ The RSCP of another cell exceeds -12dB.

+ The RSCP of the attached cell falls below -100db and another cell is available.

+ The RSCP of another cell is better than the RSCP of the attached cell 10db.


## Sources
[1. Electronics-notes : UMTS WCDMA Handver: hard, soft, softer, inter-RAT](https://www.electronics-notes.com/articles/connectivity/3g-umts/handover-handoff-hard-soft-softer.php)
[2. IJSR : Comparison between Soft Handover and Hard Handover in UMTS](https://www.ijsr.net/archive/v4i5/SUB154505.pdf)
[3. 3g4g.co.uk : Handover principle and concepts](https://www.3g4g.co.uk/Tutorial/ZG/zg_handover.html)
[4. Precisions from Mohamed Hakim MABED](https://moodle.utbm.fr/mod/forum/discuss.php?d=10830)
[5. 3GPP TS 23.009 V16.0.0](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=732)
