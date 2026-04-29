# DigClock — 8086 Assembly Digital Clock

A retro digital clock written in **8086 Assembly** for **emu8086**.  
Displays the current system **minutes and seconds** as large ASCII art digits.

## Features

- Reads real system time via DOS interrupt INT 21h
- Displays MM:SS format in large ASCII art (0–9)
- Refreshes only when time changes (no flicker)
- Auto-clears screen on each update
- Pure 8086 assembly — no libraries

## Requirements

- [emu8086](https://www.emu8086.com/) — 8086 emulator and assembler

## How to Run

1. Open `src/digclock.asm` in **emu8086**
2. Click **Emulate** and open it
3. Watch the live clock display

## Program Flow
```
start → set_digit_pointer
  ↓
main_loop → load_time
  ↓
Time changed?
  ├─ No  → main_loop
  └─ Yes → clear_screen → print → main_loop
```

## Subroutines

| Subroutine | Description |
|---|---|
| `load_time` | Gets system time via INT 21h (2Ch) |
| `parse_time` | Splits value into tens and units digits |
| `set_digit` | Looks up ASCII art pointer for a digit |
| `print_digit` | Prints ASCII art to screen at current column |
| `set_cursor` | Positions cursor using INT 10h |
| `clear_screen` | Resets video mode to clear screen |

## Display Layout
```
Col 0     Col 20    Col 40    Col 60
[Min Ten] [Min Unit] [Sec Ten] [Sec Unit]
```

## Interrupts Used

| Interrupt | Function | Purpose |
|---|---|---|
| INT 21h | 2Ch | Get system time |
| INT 21h | 02h | Print character |
| INT 10h | 0Fh | Get video mode |
| INT 10h | 00h | Set video mode |
| INT 10h | 02h | Set cursor position |

## Author

**Hazam Liaqat** 
<br>


## License

MIT License
```



## File 3: `.gitignore`
```
# Compiled output
*.exe
*.obj
*.bin
*.com
*.hex
*.o

# emu8086 temp files
*.~

# OS files
.DS_Store
Thumbs.db

# Editor files
*.swp
*~
.vscode/
.idea/
