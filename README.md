# Breakaway

**Wireless mod for original Xbox controllers (Duke and Controller S).**

This repository is the home for Breakaway's help documentation, firmware downloads and issue reporting. Everything here describes the **rev 2** hardware and the firmware that ships with it.

Product page and ordering: [RetroDisks on SmallRun](https://smallrun.net/shop/retrodisks) · Build log: [Breakaway: Cutting the cord on the OG Xbox controller](https://smallrun.net/blog/nullvalue/breakaway-wireless-controller-mod-original-xbox)

<!-- Internal notes for Aron are in HTML comments like this one. They do not
     render on GitHub. Each one marks something to confirm before this goes
     public. Search for "CONFIRM". -->

## Contents

1. [What Breakaway is](#what-breakaway-is)
2. [What's in the box](#whats-in-the-box)
3. [Before you start](#before-you-start)
4. [Installation: Duke](#installation-duke)
5. [Installation: Controller S](#installation-controller-s)
6. [The dongle](#the-dongle)
7. [First power-up and pairing](#first-power-up-and-pairing)
8. [Status LEDs](#status-leds)
9. [Controller shortcuts](#controller-shortcuts)
10. [The config page](#the-config-page)
11. [Calibration, tuning and controller health](#calibration-tuning-and-controller-health)
12. [Bluetooth mode](#bluetooth-mode)
13. [Battery, charging and sleep](#battery-charging-and-sleep)
14. [Firmware updates](#firmware-updates)
15. [Enclosure files](#enclosure-files)
16. [Troubleshooting](#troubleshooting)
17. [Reversing the mod](#reversing-the-mod)
18. [Specifications](#specifications)
19. [Reporting a problem](#reporting-a-problem)

---

## What Breakaway is

Breakaway makes an original Xbox controller wireless while keeping the original controller. Two boards do the work:

- **The pack** mounts on the controller in place of the Memory Unit retainer, under a printed dome. It holds a LiPo cell, charges over USB-C, and acts as the console as far as the controller is concerned: it powers the controller, enumerates it over USB and reads it every 4 ms.
- **The dongle** plugs into a controller port on the console using a real breakaway-cable plug. To the console it is a wired Duke, byte for byte, so it works on an unmodified Xbox with no softmod, drivers or console changes.

Between them is a purpose-built 2.4 GHz link (ESP-NOW), not Bluetooth. The pack sends the complete controller state 250 times a second, including the full pressure value of all six analog face buttons, and rumble goes back the other way. Up to four pack/dongle pairs can play at once. The pack can also act as a Bluetooth gamepad for a PC, Mac, Android or Linux device (see [Bluetooth mode](#bluetooth-mode)).

The controller's own cable is cut and its four wires land in a screw terminal inside the pack. No soldering, nothing touches the controller's circuit board, and the mod is reversible with a replacement cable.

## What's in the box

**DIY kit**

- Pack, assembled and tested, in its printed dome, LiPo cell installed
- Dongle, assembled and tested, breakaway plug mounted, in its printed enclosure
- The pack and dongle come pre-paired to each other

**Pre-modded controller**

- A genuine Microsoft Duke or Controller S, refurbished, with the pack installed, paired to its dongle and tested end to end on a real Xbox. Skip to [First power-up and pairing](#first-power-up-and-pairing).
- Refurbishment: the shell, buttons, thumbsticks and button membrane are disassembled and washed; the mainboard is cleaned with isopropyl alcohol and the stick and trigger potentiometers with contact cleaner to restore their full range. Worn Controller S thumbsticks are replaced with new aftermarket parts that are virtually identical to the originals. No replacement thumbsticks exist for the Duke, so only Dukes with good original sticks are sold. These are 20-year-old controllers, so expect minor scuffs; nothing with cracks or noticeable damage is sold.
- Each pre-modded controller is **calibrated on the bench** before it ships. The calibration lives in the pack. **Restore defaults** on the Controller health card clears it; if you ever do that, redo it with **Capture center** and **Use as range** (see [Calibration, tuning and controller health](#calibration-tuning-and-controller-health)).

You must supply your own USB charger and USB-C cable for charging. The pack charges at up to 1 A, so any 5 V USB charger rated 1 A or more is ideal; a typical phone charger qualifies.

## Before you start

**Tools**

- Phillips screwdriver for the controller shell
- Wire cutters
- Wire stripper (the controller's conductors are thin, 26 to 28 AWG)
- Small flat-blade (jeweler's) screwdriver for the screw terminal
- Electrical tape for strain relief

**Read this first**

- The install is solderless. Neither controller has a pluggable cable connector; the cable is soldered to the mainboard, which is why it is cut rather than unplugged. Cutting it is the only step that cannot be undone with a screwdriver, and even that is reversible with a replacement cable and a soldering iron (see [Reversing the mod](#reversing-the-mod)).
- The pack contains a lithium-polymer cell. Do not puncture, crush or short it, and keep the pack away from heat. Charge with an ordinary USB-C phone charger.
- The pack occupies both memory unit bays. A modded controller cannot take a memory unit or a communicator.
- Verified on genuine Microsoft Dukes and Controller S's. Third-party and clone pads are untested and unlikely to fit or work.

## Installation: Duke

The final installation guide and video are being produced and will be released before the first orders ship. Until then the prototype videos show the same procedure: *Breakaway Prototype Installation for Duke* and *Breakaway Prototype Installation for Controller S*. <!-- TODO: link both videos -->

<!-- CONFIRM: screw count and whether any screw is under the label on the Duke. -->
<!-- CONFIRM: cable routing. The product page says cut 2 in outside the body
     (used below; DESIGN-NOTES had 10-15 cm). The enclosure's rear channel
     (rc_*) brings the stub in from the cable-exit side under the hood. Adjust
     step 7 to match the install video. -->

1. **Open the controller.** Remove the Phillips screws from the underside and separate the halves. Note how the cable's strain-relief grommet sits in the shell's cable notch.
2. **Unclip the Memory Unit retainer.** It is the plastic piece with the two memory unit slots. It just unclips. The pack takes its place. Keep it in case you ever reverse the mod.
3. **Cut the cable.** Cut the controller cable about 5 cm (2 in) outside the controller body. Lift the grommet out of the shell's cable notch; the short stub stays attached to the controller's mainboard. Put the long piece with the breakaway plug aside.
4. **Prepare the stub.** Strip about 30 mm of the outer jacket and shielding. Five wires come out. Fold the braided shield and the bare drain wire back and tape them flush. Cut off the **yellow** wire (VSYNC, not needed). You are left with **red, green, white and black**. Strip 5 mm from each and fold the stranded ends double so they grip in the terminal.
5. **Wire the screw terminal.** The 4-position terminal (J3) inside the pack is labeled. Land the wires in this order:

   | Terminal | Wire |
   |---|---|
   | 1 | Red (5 V) |
   | 2 | **Green** |
   | 3 | **White** |
   | 4 | Black (GND) |

   Follow the order marked on the pack's silkscreen beside the terminal. Tighten each screw firmly and tug-test every wire.
6. **Strain-relieve the stub.** Wrap a few turns of electrical tape around the stub where it turns up toward the pack, so that flexing never reaches the factory solder joints on the controller board.
7. **Seat the pack.** The pack's flange goes where the memory unit insert was: it fits from inside the top shell, with the flange captured under the shell at the parting line, and the dome rising through the opening. The hood at the rear of the dome covers the shell's old cable notch. The cable stub enters the pack through the channel under that hood. Check that the stub is not pinched anywhere.
8. **Close the controller.** Refit the top shell and screws.
9. **Test before you put the screwdriver away.** Go to [First power-up and pairing](#first-power-up-and-pairing). If the pack's LED triple-blinks, the controller is not enumerating: open it back up and check the terminal order and that every wire is gripped.

## Installation: Controller S

The procedure is the same as the Duke's with these differences:

- The S pack body fits the S's memory unit opening, which is a bowed rectangle rather than the Duke's oval. It installs the same way, from inside the top shell with the flange under the shell. <!-- CONFIRM on the first rev-2 S print -->
- The S shell's cable notch is covered by the bent cable cover at the rear of the pack instead of a hood.
- The S pack uses a smaller 1,500 mAh cell, the largest that fits, so expect about 4 hours of runtime.
- The S's PAIR button sits a little below the dome surface and is pressed with a pen tip through the hole in the top of the dome, not a fingertip. <!-- CONFIRM: 1.5 mm recess per the 2026-10-07 S sync -->
- One of the S's shell screws is under the label on the underside. <!-- CONFIRM -->

## The dongle

- Plug the dongle into any controller port. The port decides the player number; the pack and dongle do not.
- The enclosure hangs upward from the port and clears the DVD tray.
- The dongle is powered by the console. There is no battery and nothing to charge.
- The small plunger in the lid is the PAIR button. The window beside it is the status LED.
- The dongle raises its own config page for firmware updates; see [The config page](#the-config-page).

Bench check if a dongle ever stops enumerating: with the dongle seated and the console off, the plug's D+ and D− (Green & White) contacts should each read roughly 15 kΩ to ground (black). That is the console's own pull-down, and it proves both data contacts are making contact in the port.

## First power-up and pairing

1. Plug the dongle into the console and turn the console on.
2. Press the pack's PAIR button once if its LED is dark. The pack sleeps when it has nothing to do, and PAIR wakes it.
3. Within a few seconds both LEDs should go **solid**: the pack and dongle are linked and the console sees a controller.

**Pairing a new combination** (a replacement pack or dongle, or a fresh set): a pack and dongle that have never been paired find each other on their own. Power both up and they pair within about 30 seconds, retrying until they do. If you have several unpaired sets, power up **one set at a time** so they cannot cross-pair.

**Re-pairing a board that is already paired to something:** a paired board never pairs on its own, so a neighbor's dongle cannot steal it. Short-press PAIR on **both** boards within 30 seconds of each other; both LEDs blink fast while searching and go solid when done.

**Forget a pairing:** hold PAIR for 5 seconds. The board drops its stored partner and starts searching for a new one.

**Several players:** each pack/dongle pair is an independent link. Pair each set on its own, then plug the dongles into whichever ports you like.

## Status LEDs

Both boards show the same patterns. The pack's LED is an RGB light in the top of the dome; the dongle's is a single color.

<!-- CONFIRM: the rev-2 RGB color map below is the planned one from CLAUDE.md
     §5.1 (blue = link, red = low battery, amber = charging, green = full).
     As of 2026-10-12 the firmware still drives a single-color LED; the RGB
     driver, CHRG/STDBY reading and charge wake are not written. Edit or
     remove the color column if the map changes. -->

| Pattern | Pack color | Meaning |
|---|---|---|
| Solid | Blue | Linked. The console sees the controller. |
| Fast blink | Blue | Searching for a partner (pairing). |
| One short blink every second | Blue | Link lost. The dongle is reporting a centered, idle controller to the console. |
| Three blinks, pause | Blue | Linked, but **no controller** on the pack's USB. Check the screw terminal. Shown on both boards. |
| Two blinks every 2 seconds | Red | Low battery. Shown on both boards, so you can see it on the front of the console. |
| Breathing | Amber | Charging. |
| Solid | Green | Charge complete. |
| Off | | Asleep. Press PAIR to wake. |

On the pack, the no-controller pattern wins over every link state, because a miswired terminal would otherwise look exactly like a working link.

## Controller shortcuts

Hold each combination for **3 seconds**. The controller confirms with rumble pulses.

| Action | Hold | Confirmation |
|---|---|---|
| Rumble on | LT + RT + Black + D-pad Up | 2 short |
| Rumble off | LT + RT + Black + D-pad Down | 1 short |
| Open the pack's config page | LT + RT + Black + D-pad Left | 3 short |
| Open the dongle's config page | LT + RT + Black + D-pad Right | 4 short (1 long = dongle not reachable) |
| Switch to Bluetooth mode | LT + RT + White + D-pad Up | 2 long, then the pack restarts |
| Switch back to the Xbox dongle | LT + RT + White + D-pad Down | 3 long, then the pack restarts |
| Sleep | Back + Start | 1 long |

The combos always read the physical buttons, so a button remap can never move them.

## The config page

Every setting lives on a web page served by the pack itself. No app, no internet connection and no account.

1. Hold **LT + RT + Black + D-pad Left** for 3 seconds. The controller buzzes three times.
2. On your phone or laptop, join the open Wi-Fi network **Breakaway-Controller-XXXX** (the last four characters are unique to your pack).
3. The page opens on its own, like a hotel sign-in screen. If it does not, open **http://192.168.4.1** in your browser.

The hotspot turns itself off after 5 minutes without activity, or from the **Turn hotspot off** button. You can keep playing while the page is open; the link keeps streaming.

**What is on the page**

- **Status**: mode, link, controller model, battery voltage and percentage, charging, temperature, channel and signal strength, sent packets and errors, packet loss, USB faults, uptime, firmware version.
- **Controller**: a live visualizer of every input, showing exactly what the console is being handed.
- **Connection**: Xbox dongle or Bluetooth gamepad mode, Bluetooth identity and name.
- **Rumble**: on/off and strength.
- **Pairing**: pair with the dongle, forget the pairing.
- **Controller health**, **Sticks & triggers**, **Button mapping**, **Power**: see the next section.
- **Battery log**: download or clear the minute-by-minute log.
- **Firmware update**: see [Firmware updates](#firmware-updates).

**The dongle's page** is raised from the controller with **LT + RT + Black + D-pad Right** (four buzzes). Join **Breakaway-Dongle-XXXX** and the same address opens. It shows the state the dongle is handing the console, pair/forget, and the firmware update.

## Calibration, tuning and controller health

Defaults are neutral: an untouched pack behaves exactly like a wired controller, with no deadzone, no rescaling, no remapping and rumble at 100 %. Everything below is opt-in, and each card has its own **Save** and **Restore defaults** that touch only that card.

**Controller health** shows the raw values from the pad before any tuning: live position, min and max since the last reset, resting offset as a percentage of full scale, trigger travel, pressure-button maxima and which digital buttons have been seen. Circle both sticks to their limits and press every button. Anything that will not reach its range, or never lights up, is worn hardware rather than the mod.

**Stick calibration**

- **Capture center** stores each stick's resting position so a drifting stick reads as centered. Let go of both sticks first; a capture taken with a stick held is ignored.
- **Use as range** rescales a worn stick that no longer reaches full travel. Press **Reset stats**, circle both sticks fully, then press it. The smaller of the two deflections on each axis becomes full scale, so the weak side still reaches the rail.
- **Restore defaults** on this card clears center and range only.

**Sticks & triggers**

- **Stick deadzone** is round, and travel outside it is stretched back over the full range, so there is no step at its edge and full deflection still works.
- **Trigger deadzone** ignores small trigger values.
- **Swap sticks** and **Invert LX / LY / RX / RY**.

**Button mapping** lets you choose which physical button drives each of the six pressure buttons (A, B, X, Y, Black, White) and each of the eight digital buttons (D-pad, Start, Back, thumb clicks).

**Rumble** strength scales game rumble only. The shortcut confirmation buzzes stay at full strength so they are always noticeable.

**Power** sets the sleep timeouts: minutes without a link and minutes without input (0 = never). Defaults are 5 and 15.

Calibration, tuning and the rumble setting apply in both Xbox and Bluetooth modes.

## Bluetooth mode

The pack can present the controller to a PC, Mac, Android or Linux device as a Bluetooth LE gamepad. The dongle is not used in this mode.

- It appears as an **Xbox Wireless Controller** (Xbox Series X|S identity by default). Windows binds its XInput driver, Steam lists it as an Xbox controller, and Android, Linux and macOS use their stock Xbox mapping. Rumble and battery level work. No drivers or software needed.
- The face buttons are digital in this mode: a standard gamepad report has nowhere to carry pressure.
- Not possible: hosts that need Bluetooth Classic, such as the Nintendo Switch. Untested: iPhone and iPad.

**Switching modes:** hold **LT + RT + White + D-pad Up** for Bluetooth (two long buzzes) or **D-pad Down** for the Xbox dongle (three long buzzes). The pack restarts in the new mode and remembers it. The Connection card on the config page does the same.

**Pairing with a device:** in Bluetooth mode the pack is discoverable whenever no host is connected (fast-blinking LED). Add **Xbox Wireless Controller** in the device's Bluetooth settings. No PIN. The LED goes solid when connected.

**PAIR button in Bluetooth mode:** short press drops the current host so a different one can connect; hold 5 seconds to forget every host.

**Identity and name:** the Connection card can switch the identity to Xbox One S (a fallback for a host that only rumbles with that one; it is a plain gamepad on Windows) and can replace the stock name with a custom one. Keep the stock name unless you need to tell two packs apart: some games (Call of Duty Mobile, for one) only accept controllers named Xbox Wireless Controller. **After changing the identity or name, remove the pack from the host's Bluetooth list and pair again.** Hosts cache what they learned the first time.

## Battery, charging and sleep

- **Charging:** plug any USB-C phone charger into the pack. It charges at 1 A, so a flat Duke cell takes about 2.5 hours. The USB-C port is charge-only; firmware updates are wireless.
- **Runtime (Duke, 2,000 mAh cell):** about 5.5 hours with rumble off and 4.8 hours with rumble on, measured with the controller connected and streaming the whole time. The rumble-on figure is the cost of listening for rumble commands; games that rumble constantly will drain it faster, roughly 3.5 hours.
- **Runtime (Controller S, 1,500 mAh cell):** about 4 hours.
- **Low battery** shows as the red double-blink on both boards. Below the cutoff the pack shuts the controller down, blinks five times and sleeps to protect the cell. Charge it.
- **Sleep:** there is no power switch. The pack sleeps on its own after 5 minutes without a link or 15 minutes without controller input (both adjustable on the Power card), or immediately on **Back + Start** held 3 seconds. Asleep, it draws microamps.
- **Wake:** press PAIR. It also wakes briefly once a day on its own to log the cell voltage, then goes straight back to sleep.
- **Battery log:** the pack records a sample every minute (voltage, temperature, link state) to its own flash. Download it as a CSV from the config page. It is the first thing to attach to a battery-related issue report.

## Firmware updates

Firmware lives in this repository's [`firmware/`](firmware/) folder. Every release is two files, one per board, with the version in the name:

| File | Board |
|---|---|
| `xbc-tx_s3-<version>-app.bin` | Pack (controller) |
| `xbc-rx_s3-<version>-app.bin` | Dongle |

To download one, open the file on GitHub and use **Download raw file**. Keep the original file name: each board checks the name and the image before it installs.

The version is `major.minor.build`, for example `0.2.91`. The running version is on the Status card of the config page.

**Updating the pack**

1. Download the pack file to your phone or laptop.
2. Open the pack's config page (hold LT + RT + Black + D-pad Left). On a phone, open **192.168.4.1 in your normal browser**: the automatic sign-in popup cannot pick files.
3. On the **Firmware update** card choose the file and press **Upload**.
4. The pack checks that the file is for a pack, verifies it, and reboots into it. The LED goes dark for a few seconds and comes back.

**Updating the dongle** is the same through the dongle's page: hold **LT + RT + Black + D-pad Right**, join Breakaway-Dongle-XXXX, upload the dongle file.

Each board refuses a file built for the other board. An update never touches your pairing or settings, and a failed or interrupted upload leaves the current firmware in place.

## Enclosure files

The pack's printed parts are in this repository's [`enclosure/`](enclosure/) folder as STL files, for a replacement or your own print. Each controller has two parts: the **body**, the dome that sits in place of the Memory Unit retainer, and the **cradle**, the carrier inside it that holds the board and the cell.

| File | Controller | Part |
|---|---|---|
| `duke-pack-body.stl` | Duke | Dome |
| `duke-pack-cradle.stl` | Duke | Board and cell carrier |
| `controller-s-pack-body.stl` | Controller S | Dome |
| `controller-s-pack-cradle.stl` | Controller S | Board and cell carrier |

These are the rev 2 parts, matched to the rev 2 pack board: M2 screw bosses, the USB-C shaft centered on the edge, and the PAIR plunger and LED holes in the dome top. The Duke and Controller S parts are not interchangeable. The production parts are printed in black resin and sanded; the body has no flat face, so print it dome-up on supports under the flange or crest-down in a bowl of supports. Download a file the same way as firmware: open it on GitHub and use **Download raw file**. Print notes are in the folder's [README](enclosure/README.md).

<!-- CONFIRM: the rev-2 enclosure sync (2026-10-06/07) was unprinted as of
     the design notes. Replace the STLs once a print confirms fit. -->

## Troubleshooting

**Both LEDs triple-blink, nothing responds in a game.** The pack does not see the controller on its USB. Open the controller and check the screw terminal: 1 red, 2 green, 3 white, 4 black, every wire gripped. Green and white are the ones most often swapped.

**Pack LED blinks fast and never goes solid.** It is searching for a dongle. Make sure the dongle is plugged in and the console is on. If the two have never been paired, wait 30 seconds. If they were paired to something else, short-press PAIR on both.

**Pack LED blinks once a second.** Link lost. Walk back into range, or check that the console is still on and the dongle still seated.

**Pack LED is dark.** It is asleep. Press PAIR. If it stays dark, charge it.

**Red double-blink.** Low battery. Charge it.

**The controller froze mid-game but both LEDs are solid.** The pack recovers from a USB hiccup on its own, power-cycling the controller if it has to, so this should not persist. If it does, note the time, download the battery log from the config page (a `usb_fault` column marks the minute) and open an issue.

**The config page does not open on its own.** Open http://192.168.4.1 in a browser while joined to the Breakaway network. On some phones, mobile data must be off before the phone will use a network without internet.

**The dongle's page does not come up (one long buzz).** The pack could not reach the dongle. Make sure the link is up (solid LEDs) and try again.

**Windows or Android shows a driver error or disconnects in Bluetooth mode.** Remove the pack from the device's Bluetooth list and pair it again. Hosts cache the pack's description, and any identity or firmware change invalidates it.

**The console does not see the dongle at all.** Reseat it. If that does not help, see the resistance check in [The dongle](#the-dongle).

**Firmware upload refused.** The file is for the other board, or the file name was changed. Download it again and keep the original name.

## Reversing the mod

1. Open the controller and unscrew the four wires from the pack's terminal.
2. Lift the pack out and clip the original Memory Unit retainer back in.
3. Fit a replacement controller cable. Replacement cables are inexpensive and widely available, but the controller has no cable connector: fitting one means desoldering the factory stub from the mainboard and soldering the replacement in its place, so this is a job for someone comfortable with a soldering iron. The install never touches those joints, which keeps this option open.

## Specifications

| | |
|---|---|
| Supported controllers | Original Xbox Duke, Controller S (genuine Microsoft) |
| Console | Original Xbox, unmodified, any controller port |
| Radio link | 2.4 GHz ESP-NOW, 250 Hz full-state streaming, paired unicast |
| Players | Up to 4 pack/dongle pairs at once |
| Pack | ESP32-S3 (USB host), rev 2 board: USB-C charging at 1 A, RGB status LED, single PAIR button beside the USB-C, no power switch, low-quiescent power tree |
| Pack battery | Duke: 2,000 mAh 103450 LiPo · Controller S: 1,500 mAh 103443 LiPo |
| Runtime (Duke) | ~5.5 h rumble off · ~4.8 h rumble on · ~3.5 h rumble-heavy |
| Runtime (Controller S) | ~4 h |
| Sleep | Automatic after 5 min without a link or 15 min without input (adjustable); microamp standby; PAIR wakes |
| Dongle | ESP32-S3 (USB device, XID), powered by the console, PAIR plunger and status LED in the lid |
| Controller connection | Cut cable into a 4-position screw terminal (26 to 18 AWG), no soldering |
| Bluetooth mode | Bluetooth LE gamepad, Xbox Wireless Controller identity (Series X\|S or One S), rumble, battery level, 7.5 ms connection interval |
| Configuration | Web page over the pack's own hotspot, no app |
| Firmware updates | Over the air, both boards, from the config page |
| Enclosures | 3D printed in black resin, sanded |

## Reporting a problem

Open an issue on this repository's [Issues](../../issues) page. The more of this you include, the faster it gets fixed:

- Which board (pack or dongle), and whether the controller is a Duke or a Controller S
- Firmware version of both boards (Status card on each config page)
- What the LEDs were doing
- Exactly what you did and what happened, and whether it happens every time
- For battery, sleep or freeze problems: the battery log CSV from the pack's config page
- For Bluetooth problems: the host (Windows / Android / macOS / Linux and version) and whether you removed and re-paired the pack after the last firmware update

Feature requests are welcome in the same place.
