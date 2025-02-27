## Description

### **The Cursed Console - 呪われたカセット**

Long ago, in the age of 8-bit warriors, there existed a legendary game cartridge said to grant ultimate gaming prowess. However, a great curse befell it, causing glitches, distortions, and bizarre anomalies. Some say the spirit of a forgotten developer haunts the code, whispering secrets through corrupted pixels.

A mysterious ROM has surfaced, along with a modified NES emulator to run it. The game is playable, but something is deeply wrong. Strange artifacts appear, controls feel off, and unexpected behaviors emerge. Within these mistakes, a hidden message lingers.

Can you navigate through the glitched world and uncover the hidden flag?

- **Author:** Afdul
- **Flag:** `apoorvctf{Br}OOk}`

---

## Setup Instructions

1. Ensure you have `Docker` installed on your system.
2. Clone the repository and navigate into the challenge directory:
   ```sh
   git clone <repo_url>
   cd nes_ctf
   ```
3. Build and run the Docker container:
   ```sh
   docker build -t nes_ctf .
   docker run --rm -p 8080:8080 nes_ctf
   ```
4. Access the emulator and game via `http://localhost:8080`.

For manual setup:
- An NES emulator (bundled) is required.
- Run the provided ROM file using the emulator.

---

## Misc
  
- This challenge is inspired by the "haunted game" urban legends.
- Prior knowledge of NES memory layout, debugging ROMs, and reverse engineering may be helpful.
- Recommended challenges to complete first:
  - [Intro to NES Reverse Engineering]
  - [Binary Exploitation Basics]

---

## Writeup

The challenge revolves around analyzing the broken NES ROM and the emulator to identify unintended behaviors. 

There are rendering issues in any NES game you run with the provided emulator, meaning the issue lies in the emulator itself. Flickering indicates the PPU is malfunctioning, but the true flag is hidden in the colors being added to the palette. The NES palette has a specific size, and the injected values contain the flag.

Load up your favorite game in Mesen, such as Super Mario Bros. Open the palette viewer and compare the background color values to those given in the challenge. The colors correspond to ASCII values of the flag, mod 64, to handle overflow.

![Pallete Viewer](images/palette.png)

---

**File Structure:**
- `setup/` - Contains setup scripts and Dockerfiles
- `files/` - Contains the NES ROM and emulator for participants

**Submission Deadline:** Wednesday, 26th

_Instance-based challenges only. Reach out if any clarification is needed._
