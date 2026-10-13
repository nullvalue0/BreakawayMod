# Enclosure files

STL files for the pack's two printed parts, for each controller. These are the parts that ship with the kit and the pre-modded controllers, exported from the rev 2 enclosure design (synced to the rev 2 pack board on 2026-10-06 and 2026-10-07).

<!-- CONFIRM: as of the 2026-10-07 design notes neither rev-2 sync had been
     printed. Re-export and replace these files once a print confirms fit. -->

| File | Controller | Part |
|---|---|---|
| `duke-pack-body.stl` | Duke | Dome. Sits in place of the Memory Unit retainer, on top of the controller shell. |
| `duke-pack-cradle.stl` | Duke | Carrier inside the dome. Holds the pack board and the 103450 cell. |
| `controller-s-pack-body.stl` | Controller S | Dome, shaped to the Controller S shell. |
| `controller-s-pack-cradle.stl` | Controller S | Carrier for the pack board and the smaller 103443 cell. |

The Duke and Controller S parts are not interchangeable: the openings, shell contour and cell pocket are different.

**Printing**

- The production parts are printed in black resin and sanded.
- The body has no flat face. Print it dome-up with supports under the flange, or crest-down in a bowl of supports.
- The cradle prints on its floor.
- The board is fixed to the cradle with three M2 × 6 wafer-head self-tapping screws into printed bosses (1.7 mm pilots).

**Downloading**

Open a file on GitHub and use **Download raw file**. STLs are binary; a browser "Save page as" on the preview will not give you a printable file.

The design source (OpenSCAD) is not in this repository. In the design files these are `xbc-tx-pack-<part>.stl` (Duke) and `xbc-tx-pack-s-<part>.stl` (Controller S).
