# Multi-Turtle Command Controller

A command-line interpreter designed to control multiple Python Turtle graphics instances simultaneously using formatted string commands. It features closures for isolated state management, regular expression command parsing, command history search, and customizable scaling[cite: 1].

---

## User Drawing Manual

Commands can be executed one at a time or chained together using a semicolon (`;`)[cite: 1].

When prompted, enter your command string, followed by which turtle you want to control (`1` for full scale, `2` for half scale)[cite: 1].

### Command Reference

| Command | Syntax | Description | Example |
| :--- | :--- | :--- | :--- |
| **Move Forward** | `F<distance>` | Moves the turtle forward by the specified pixel distance (scaled)[cite: 1]. | `F100`[cite: 1] |
| **Turn Left** | `L<angle>` | Rotates the turtle counterclockwise by `<angle>` degrees[cite: 1]. | `L90`[cite: 1] |
| **Turn Right** | `R<angle>` | Rotates the turtle clockwise by `<angle>` degrees[cite: 1]. | `R45`[cite: 1] |
| **Set Color** | `C<color_name>` | Changes the pen/brush color[cite: 1]. | `Cred`, `Cblue`, `Cgreen`[cite: 1] |
| **Change Shape** | `Shape <shape_name>` | Changes cursor icon (`turtle`, `classic`, `arrow`, `circle`, `square`, `triangle`)[cite: 1]. | `Shape arrow`[cite: 1] |
| **Toggle Fill** | `Fill <on\|off>` | Starts or ends filling a drawn shape with the current color[cite: 1]. | `Fill on` ... `Fill off`[cite: 1] |
| **Draw Square** | `SQ<side>` | Draws a square where each edge is of length `<side>`[cite: 1]. | `SQ80`[cite: 1] |
| **Draw Polygon** | `POLY<sides>:<length>` | Draws a regular polygon with `<sides>` edges of length `<length>`[cite: 1]. | `POLY6:50` *(Hexagon)*[cite: 1] |
| **Draw Spiral** | `SPIRAL<length>:<depth>` | Recursively draws an inward 90° spiral[cite: 1]. | `SPIRAL100:15`[cite: 1] |
| **Check Status** | `status` or `report` | Displays current color, scale factor, valid, and invalid command counts[cite: 1]. | `status`[cite: 1] |

---

### Step-by-Step Drawing Examples

* **Red Filled Square:** `Cred;Fill on;SQ100;Fill off` (Target: Turtle `1`)[cite: 1]
* **Equilateral Triangle:** `Cblue;POLY3:120` (Target: Turtle `1` or `2`)[cite: 1]
* **Purple Octagon:** `Cpurple;Fill on;POLY8:60;Fill off` (Target: Turtle `1`)[cite: 1]
* **Inward Spiral:** `Cgreen;SPIRAL120:20` (Target: Turtle `1`)[cite: 1]
* **Staircase Step:** `F40;L90;F40;R90;F40;L90;F40;R90;F40` (Target: Turtle `2`)[cite: 1]

---

## Technical Architecture

* **Closure State Encapsulation:** `create_turtle_controller` maintains internal private state (`current_color`, `command_history`, counters, and turtle references) without global variables[cite: 1].
* **Regex Dispatcher:** Tokenizes commands separated by `;` and parses them using pre-compiled regular expressions[cite: 1].
* **Independent Scaling:** Turtle 1 operates at `1.0` scale, while Turtle 2 runs at `0.5` scale, scaling distances dynamically[cite: 1].

---

## Running the Application

### Local Machine (Recommended)
`turtle` relies on Tkinter GUI bindings[cite: 1]. Run the script locally on Windows, macOS, or Linux with an active desktop display:

```bash
python main.py
