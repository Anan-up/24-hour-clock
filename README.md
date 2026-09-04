[English](README.md) | [简体中文](README_Simplified_Chinese.md) | [繁體中文](README_Classical_Chinese.md)

## I. Overall Features
- **Dual clock display**: Shows both an analog pointer clock (dial) and a digital clock (hours, minutes, seconds) simultaneously.
- **Time format switching**: Switch between 12-hour and 24-hour formats. When switching, the dial numbers (1–12 or 1–24) and the digital clock display update synchronously.
- **Real-time updates**: Updates every second (actually refreshes every 50ms for smooth second-hand movement), displaying the current time, date, day of week, and time zone.
- **Fullscreen mode**: Click the "Fullscreen" button to enter or exit browser fullscreen.

---

## II. Interface Layout
- Vertically centered and stacked from top to bottom:
  1. **Title**: "WEB CLOCK"
  2. **Clock area**: Analog clock on the left (diameter 300px), digital clock on the right (large font for hours/minutes/seconds, with date and time zone shown below).
  3. **Control bar**: Includes the 12/24-hour toggle button (slider style) and the fullscreen button.

---

## III. Analog Clock (Dial)
- **Hands**: Hour, minute, and second hands, driven by CSS `transform: rotate()`. The second hand has a smooth effect (due to the 50ms timer interval).
- **Ticks**: 60 tick marks are generated, with every 5th being a long tick (major tick).
- **Numbers**: Dynamically generated 1–12 or 1–24 numbers based on the current format, evenly distributed around the circle via trigonometric calculations (24-hour numbers are smaller and inset).
- **Center decoration**: A small dot as the center axis.

---

## IV. Digital Clock
- Displays hours, minutes, and seconds using a monospace font (`tabular-nums`); the colon has a blinking animation (every 2 seconds).
- Shows AM/PM in 12-hour format; hides AM/PM in 24-hour format.
- Below displays the date (year, month, day, weekday) and the time zone name with its UTC offset.

---

## V. Interaction & Control
- **12/24-hour switching**:
  - Uses a "slider" design. When a button is clicked, the highlighted background (`thumb`) smoothly slides to the clicked button position (calculated via `offsetLeft` and `offsetWidth`).
  - After switching, the dial numbers are regenerated and the current time display is updated immediately.
- **Fullscreen**: Calls the browser Fullscreen API (`requestFullscreen` / `exitFullscreen`).

---

## VI. Technical Implementation Notes
- **Pure native JavaScript**, no external dependencies.
- **CSS variables** (`:root`) define the color scheme for easy theme extension.
- **Responsive**: Uses `flex` layout; the control bar wraps automatically.
- **Performance**: `setInterval` with a 50ms interval achieves a smooth second hand while updating both the digital clock and the dial.
- **Time zone retrieval**: Uses `Intl.DateTimeFormat().resolvedOptions().timeZone` to get the current time zone name and compute the UTC offset.

---

## VII. Style
- Minimalist, rounded, frosted-glass feel (`radial-gradient` background, semi-transparent card background).
- Hands distinguished by color: hour hand dark, minute hand gray, second hand red.
- Subtle interaction feedback (color transitions, slider animation).

![project-screenshot](24-hour-clock.png)

## License

[MIT](LICENSE)
