# DigClock — 8086 Assembly Digital Clock

A retro digital clock written in **8086 Assembly** for **emu8086**.  
Displays the current system **minutes and seconds** as large ASCII art digits.

## Preview
 data segment
    zero    db "     000000000     ", 10          
            db "   00:::::::::00   ", 10
            db " 00:::::::::::::00 ", 10
            db "0:::::::000:::::::0", 10
            db "0::::::0   0::::::0", 10
            db "0:::::0     0:::::0", 10
            db "0:::::0     0:::::0", 10
            db "0:::::0 000 0:::::0", 10
            db "0:::::0 000 0:::::0", 10
            db "0:::::0     0:::::0", 10
            db "0:::::0     0:::::0", 10
            db "0::::::0   0::::::0", 10
            db "0:::::::000:::::::0", 10
            db " 00:::::::::::::00 ", 10
            db "   00:::::::::00   ", 10
            db "     000000000     ", 10, "$"

    one     db "  1111111   ", 10
            db " 1::::::1   ", 10
            db "1:::::::1   ", 10
            db "111:::::1   ", 10
            db "   1::::1   ", 10
            db "   1::::1   ", 10
            db "   1::::1   ", 10
            db "   1::::l   ", 10
            db "   1::::l   ", 10
            db "   1::::l   ", 10
            db "   1::::l   ", 10
            db "   1::::l   ", 10
            db "111::::::111", 10
            db "1::::::::::1", 10
            db "1::::::::::1", 10
            db "111111111111", 10, "$"

    two     db " 222222222222222    ", 10
            db "2:::::::::::::::22  ", 10
            db "2::::::222222:::::2 ", 10
            db "2222222     2:::::2 ", 10
            db "            2:::::2 ", 10
            db "            2:::::2 ", 10
            db "         2222::::2  ", 10
            db "    22222::::::22   ", 10
            db "  22::::::::222     ", 10
            db " 2:::::22222        ", 10
            db "2:::::2             ", 10
            db "2:::::2             ", 10
            db "2:::::2       222222", 10
            db "2::::::2222222:::::2", 10
            db "2::::::::::::::::::2", 10
            db "22222222222222222222", 10, "$"

    three   db " 333333333333333   ", 10
            db "3:::::::::::::::33 ", 10
            db "3::::::33333::::::3", 10
            db "3333333     3:::::3", 10
            db "            3:::::3", 10
            db "            3:::::3", 10
            db "    33333333:::::3 ", 10
            db "    3:::::::::::3  ", 10
            db "    33333333:::::3 ", 10
            db "            3:::::3", 10
            db "            3:::::3", 10
            db "            3:::::3", 10
            db "3333333     3:::::3", 10
            db "3::::::33333::::::3", 10
            db "3:::::::::::::::33 ", 10
            db " 333333333333333   ", 10, "$"

    four    db "       444444444  ", 10
            db "      4::::::::4  ", 10
            db "     4:::::::::4  ", 10
            db "    4::::44::::4  ", 10
            db "   4::::4 4::::4  ", 10
            db "  4::::4  4::::4  ", 10
            db " 4::::4   4::::4  ", 10
            db "4::::444444::::444", 10
            db "4::::::::::::::::4", 10
            db "4444444444:::::444", 10
            db "          4::::4  ", 10
            db "          4::::4  ", 10
            db "          4::::4  ", 10
            db "        44::::::44", 10
            db "        4::::::::4", 10
            db "        4444444444", 10, "$"

    five    db "555555555555555555 ", 10
            db "5::::::::::::::::5 ", 10
            db "5::::::::::::::::5 ", 10
            db "5:::::555555555555 ", 10
            db "5:::::5            ", 10
            db "5:::::5            ", 10
            db "5:::::5555555555   ", 10
            db "5:::::::::::::::5  ", 10
            db "555555555555:::::5 ", 10
            db "            5:::::5", 10
            db "            5:::::5", 10
            db "5555555     5:::::5", 10
            db "5::::::55555::::::5", 10
            db " 55:::::::::::::55 ", 10
            db "   55:::::::::55   ", 10
            db "     555555555     ", 10, "$"

    six     db "        66666666   ", 10
            db "       6::::::6    ", 10
            db "      6::::::6     ", 10
            db "     6::::::6      ", 10
            db "    6::::::6       ", 10
            db "   6::::::6        ", 10
            db "  6::::::6         ", 10
            db " 6::::::::66666    ", 10
            db "6::::::::::::::66  ", 10
            db "6::::::66666:::::6 ", 10
            db "6:::::6     6:::::6", 10
            db "6:::::6     6:::::6", 10
            db "6::::::66666::::::6", 10
            db " 66:::::::::::::66 ", 10
            db "   66:::::::::66   ", 10
            db "     666666666     ", 10, "$"

    seven   db "77777777777777777777", 10
            db "7::::::::::::::::::7", 10
            db "7::::::::::::::::::7", 10
            db "777777777777:::::::7", 10
            db "           7::::::7 ", 10
            db "          7::::::7  ", 10
            db "         7::::::7   ", 10
            db "        7::::::7    ", 10
            db "       7::::::7     ", 10
            db "      7::::::7      ", 10
            db "     7::::::7       ", 10
            db "    7::::::7        ", 10
            db "   7::::::7         ", 10
            db "  7::::::7          ", 10
            db " 7::::::7           ", 10
            db "77777777            ", 10, "$"

    eight   db "     888888888     ", 10
            db "   88:::::::::88   ", 10
            db " 88:::::::::::::88 ", 10
            db "8::::::88888::::::8", 10
            db "8:::::8     8:::::8", 10
            db "8:::::8     8:::::8", 10
            db " 8:::::88888:::::8 ", 10
            db "  8:::::::::::::8  ", 10
            db " 8:::::88888:::::8 ", 10
            db "8:::::8     8:::::8", 10
            db "8:::::8     8:::::8", 10
            db "8:::::8     8:::::8", 10
            db "8::::::88888::::::8", 10
            db " 88:::::::::::::88 ", 10
            db "   88:::::::::88   ", 10
            db "     888888888     ", 10, "$"

    nine    db "     999999999     ", 10
            db "   99:::::::::99   ", 10
            db " 99:::::::::::::99 ", 10
            db "9::::::99999::::::9", 10
            db "9:::::9     9:::::9", 10
            db "9:::::9     9:::::9", 10
            db " 9:::::99999::::::9", 10
            db "  99::::::::::::::9", 10
            db "    99999::::::::9 ", 10
            db "         9::::::9  ", 10
            db "        9::::::9   ", 10
            db "       9::::::9    ", 10
            db "      9::::::9     ", 10
            db "     9::::::9      ", 10
            db "    9::::::9       ", 10
            db "   99999999        ", 10, "$"

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
2. Click **Emulate**
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
BSCS-F23-M01

## License

MIT License
```

---

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
