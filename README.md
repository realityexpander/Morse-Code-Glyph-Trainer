# Morse Glyph Trainer

A single-page HTML/JavaScript Morse code learning app that teaches **A–Z** and **0–9** using animated dots and dashes positioned directly over the strokes of each alphanumeric character.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/97e3a7f7-7644-4141-9dcf-cbaa8a37b5da" />

<img width="400" height="355" alt="Screen Recording 2026-09-19 at 6 13 23 PM" src="https://github.com/user-attachments/assets/b64e9a6f-3fd0-4e17-b836-9f552a0b6d0b" />

Deployed live here: https://realityexpander.github.io/Morse-Code-Glyph-Trainer/


The app combines a visual mnemonic approach with Morse audio, animation, drilling, and a full character reference chart. A separate **Glyph Editor** is included as an addendum tool for manually adjusting the exact position and angle of each Morse dot and dash.

## Features

- Supports all letters **A–Z**
- Supports digits **0–9**
- Animated Morse dots and dashes directly over each character
- Manually aligned glyph overlay coordinates
- Synchronized Morse audio tones
- Adjustable animation speed
- Adjustable audio tone frequency
- Optional automatic character advance
- Learn mode
- Drill mode
- Full reference chart
- Randomized character practice
- Dot/dash answer entry
- Immediate answer checking
- Accuracy tracking
- Keyboard controls
- Responsive layout for desktop and mobile browsers
- Light and dark mode support
- No external libraries or frameworks required
- No server required
- Works as a single standalone HTML page
- From this conversation with ChatGPT 5.6 High mode
  - https://chatgpt.com/share/6aaf07c5-a004-83ea-9d05-a56b096dad3d   

- Based on these Glyphs
<img width="400" alt="image" src="https://github.com/user-attachments/assets/d5640524-4f22-45d6-8162-d0f56298f524" />


## Files

The project consists primarily of two standalone HTML files:

```text
morse_glyph_trainer_aligned.html
morse_overlay_position_editor.html
README.md
```

### `index.html`

The main Morse learning and drilling application.

### `morse_overlay_position_editor.html`

A separate development utility for manually positioning the dots and dashes over each glyph.

---

# Installation

No build system, package manager, or web server is required.

## Option 1: Run Locally

1. Download or clone this repository.
2. Locate:

```text
index.html
```

3. Double-click the file, or open it with a modern web browser.

Recommended browsers include:

- Safari
- Chrome
- Firefox
- Edge

Because the application is completely self-contained, it can run directly from the local filesystem.

## Option 2: Clone with Git

```bash
git clone https://github.com/realityexpander/Morse-Code-Glyph-Trainer.git
cd Morse-Code-Glyph-Trainer
```

Then open:

```text
index.html
```

in your browser.

## Option 3: GitHub Pages

The app can also be hosted directly with GitHub Pages.

For the simplest setup, use:

```text
index.html
```

Then:

1. Push the repository to GitHub.
2. Open the repository's **Settings**.
3. Select **Pages**.
4. Under **Build and deployment**, choose:

```text
Deploy from a branch
```

5. Select the branch containing the application, usually:

```text
main
```

6. Select:

```text
/ (root)
```

7. Save the settings.

GitHub will provide the public URL for the application.

---

# Using the Morse Glyph Trainer

The main application has three modes:

- **Learn**
- **Drill Dots & Dashes**
- **Drill Glyphs **
- **Chart**

## Learn Mode

Learn mode displays one large alphanumeric character at a time.

The Morse sequence is represented by dots and dashes positioned directly over the strokes of the character.

Use:

```text
Animate
```

to play the Morse sequence.

Each Morse mark is highlighted in order while the corresponding tone is played.

### Navigation

Use:

```text
Previous
Next
Random
```

to move between characters.

### Keyboard Controls

While using Learn mode:

```text
Space       Animate / replay
Left Arrow  Previous character
Right Arrow Next character
```

## Animation Settings

The application includes several adjustable settings.

### Speed

Changes the speed at which the Morse animation and sound are played.

### Tone

Changes the audio frequency of the Morse signal.

### Play Morse Tone

Enables or disables audio.

### Auto-Advance

Automatically advances to the next character after the animation completes.

### Show Morse Code

Shows or hides the printed Morse sequence above the glyph.

---

# Drill Mode

Drill mode tests your ability to recall the Morse code for a displayed character.

The Morse sequence is hidden initially.

Enter the answer using:

```text
Dot
Dash
```

or with the keyboard:

```text
.
-
```

Then press:

```text
Check
```

or:

```text
Enter
```

to submit the answer.

Use:

```text
Reveal
```

to display and animate the correct sequence.

### Drill Keyboard Controls

```text
.           Enter dot
-           Enter dash
Backspace   Remove last symbol
Enter       Check answer
Space       Reveal and animate answer
```

## Accuracy Tracking

The drill panel records:

- Correct answers
- Total attempts
- Accuracy percentage

These values apply to the current browser session.

---

# Chart Mode

Chart mode displays the complete Morse reference set for:

```text
A–Z
0–9
```

Each character displays its corresponding Morse sequence.

Selecting a character returns to Learn mode and opens that character directly.

---

# Morse Overlay Data Format

The position of each dot and dash is stored in a JavaScript object named:

```javascript
const P = {
    A:[[220,127,-63],[220,258,0]],
    B:[[155,207,90],[219,127,0],[220,206,0],[222,296,0]]
};
```

Each Morse mark uses the format:

```text
[x, y, angle]
```

where:

- `x` = horizontal position in the SVG coordinate system
- `y` = vertical position in the SVG coordinate system
- `angle` = dash rotation angle in degrees

The application uses a:

```text
440 × 440
```

SVG coordinate system.

For dots, the angle value is normally:

```text
0
```

For dashes, the angle controls the dash orientation.

The order of the entries must match the Morse sequence for the character.

For example:

```text
A = .-
```

therefore:

```javascript
A:[
    [dot_x,dot_y,0],
    [dash_x,dash_y,dash_angle]
]
```

---

# Addendum: Glyph Editor

<img width="500" alt="image" src="https://github.com/user-attachments/assets/bcb6c2ec-cc7a-48b1-bc72-01b48b43b101" />


The repository includes a separate utility:

```text
morse_overlay_position_editor.html
```

This tool is used to manually position the Morse dots and dashes so that they align visually with the strokes of each letter or number.

The editor is not required for normal use of the trainer. It is intended for modifying or refining the glyph overlay data.

## Opening the Glyph Editor

Open:

```text
morse_overlay_position_editor.html
```

directly in a browser.

No installation or server is required.

## Selecting a Character

The editor supports all:

```text
A–Z
0–9
```

Use:

```text
Prev
Next
```

or select a character directly from the character list.

## Moving a Dot or Dash

Click a Morse mark to select it.

Then either:

- Drag it directly with the mouse or pointer
- Edit its exact X coordinate
- Edit its exact Y coordinate
- Use the keyboard arrow keys

### Keyboard Position Controls

```text
Left Arrow   Move left 1 pixel
Right Arrow  Move right 1 pixel
Up Arrow     Move up 1 pixel
Down Arrow   Move down 1 pixel
```

Hold:

```text
Shift
```

while using an arrow key to move:

```text
10 pixels
```

at a time.

## Rotating Dashes

Dashes can be rotated using:

- The Angle input
- The angle slider
- The `-5°` button
- The `+5°` button

You can also use:

```text
[   Rotate dash -1°
]   Rotate dash +1°
```

Dots do not require rotation.

## Grid

The editor includes an optional visual grid.

Enable:

```text
Grid
```

to display it.

Enable:

```text
Snap 5
```

to force positions to the nearest 5 coordinate units while dragging.

This can be useful for rough placement.

For final alignment, disabling snapping allows precise positioning.

## Selected Mark Number

Each Morse element is numbered.

For example, if a character has the Morse code:

```text
.-..
```

the editor displays four selectable marks:

```text
1: dot
2: dash
3: dot
4: dot
```

The ordering is important because it determines the animation sequence in the main application.

---

# Exporting Glyph Data

The editor automatically generates the complete JavaScript position map.

The output is shown in this form:

```javascript
const P = {
    A:[[220,127,-63],[220,258,0]],
    B:[[155,207,90],[219,127,0],[220,206,0],[222,296,0]],
    ...
};
```

Available export options include:

### Copy Current Line

Copies only the data for the currently selected character.

Example:

```javascript
A:[[220,127,-63],[220,258,0]],
```

### Copy All

Copies the complete:

```javascript
const P = { ... };
```

object.

### Download JS

Downloads the position data as:

```text
morse_positions.js
```

### Download JSON

Downloads the coordinate data as:

```text
morse_positions.json
```

---

# Importing Existing Glyph Data

The editor can also load previously generated position data.

Paste either:

```javascript
const P = {
    ...
};
```

or compatible JSON into the import area.

Then select:

```text
Load pasted data
```

The editor will validate that:

- All 36 characters are present
- Each character contains the correct number of Morse marks
- Each coordinate entry is valid

This makes it possible to save your work and continue editing later.

---

# Updating the Main Trainer with New Glyph Positions

After editing the glyph positions:

1. Open the Glyph Editor.
2. Adjust the desired characters.
3. Choose:

```text
Copy All
```

or:

```text
Download JS
```

4. Open the main trainer source.
5. Locate:

```javascript
const P = {
```

6. Replace the existing `P` object with the newly exported one.

Do not change the order of the Morse marks unless you also intend to change the Morse animation sequence.

The editor and trainer use the same:

```text
440 × 440
```

coordinate system, so coordinates can be transferred directly.

---

# Design Notes

The visual overlays are intended as a **mnemonic learning aid**.

They are not part of the official International Morse Code specification.

International Morse Code defines the dot-and-dash sequence for each character, but it does not define how those symbols should be positioned over the visual shape of a Latin letter or numeral.

The overlay positions in this project are therefore manually designed to visually associate the Morse sequence with the shape of each glyph.

---

# Technical Details

The application is implemented using:

- HTML5
- CSS
- Vanilla JavaScript
- SVG
- Web Audio API

No external JavaScript libraries are required.

The application does not require:

```text
Node.js
npm
React
Vue
Angular
jQuery
Python
a database
a web server
```

All application logic is contained in the HTML file.

---

# Browser Audio

Modern browsers may prevent audio from starting until the user interacts with the page.

If Morse tones do not initially play, click:

```text
Animate
```

or another application control once.

The browser should then allow audio playback.

---

# Project Structure

A minimal repository can use:

```text
/
├── index.html
├── morse_overlay_position_editor.html
└── README.md
```

If you prefer to preserve the original trainer filename:

```text
/
├── morse_glyph_trainer_aligned.html
├── morse_overlay_position_editor.html
└── README.md
```

For GitHub Pages, using:

```text
index.html
```

for the main application is recommended.

---

# License

Add the license appropriate for your repository here.

For example, if using the MIT License, add a:

```text
LICENSE
```

file to the repository and change this section to:

```text
This project is licensed under the MIT License. See the LICENSE file for details.
```

---

# Acknowledgment

Morse code character sequences follow the standard International Morse Code alphabet.

The visual glyph-overlay placement used by this application is a custom mnemonic representation designed for learning and practice.
