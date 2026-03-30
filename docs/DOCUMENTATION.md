# DigClock — Technical Documentation

## Architecture

DigClock uses a **polling loop** architecture:

1. Read system time continuously
2. Compare with last displayed time
3. If changed → clear screen and redraw
4. Repeat forever

This prevents flickering by only updating when necessary.

## Memory Segments

| Segment | Contents | Size (approx.) |
|---|---|---|
| Data | ASCII digit patterns + variables | ~2.6 KB |
| Stack | Return addresses | 256 bytes |
| Code | Instructions | ~1.5 KB |
| Extra | Reserved | — |

## Data Layout
```
digit_pointer[0]  → offset of "zero" pattern
digit_pointer[2]  → offset of "one" pattern
...
digit_pointer[18] → offset of "nine" pattern
```

Each ASCII pattern is 16 lines, terminated by `"$"`.

## Key Algorithms

### Time Parsing
```
Input : AL = time value (0–59)
        AH = 0
        BL = 10
Process: DIV BL
Output : AL = tens digit
         AH = units digit
```

### Digit Lookup
```
Input : AL = digit (0–9)
Process: AL × 2 → SI (word-sized index)
         SI = digit_pointer[SI]
Output : SI = pointer to ASCII pattern
```

## Register Usage

| Register | Role |
|---|---|
| AL / AH | Time values, digit parsing |
| BH | Video page number |
| BL | Multiplier / divisor |
| DH | Row (cursor position) |
| DL | Column (cursor position) |
| SI | ASCII art string pointer |
| DS | Data segment base |

## INT 21h Reference
```
AH = 2Ch — Get System Time
  OUT: CH = hours (0–23)
       CL = minutes (0–59)
       DH = seconds (0–59)
       DL = centiseconds (0–99)

AH = 02h — Output Character
  IN:  DL = character to print
```

## INT 10h Reference
```
AH = 0Fh — Get Current Video Mode
AH = 00h — Set Video Mode  (AL = mode)
AH = 02h — Set Cursor Position
  IN:  BH = page number
       DH = row
       DL = column
```

## Known Limitations

- Displays MM:SS only (no hours)
- Designed for 80×25 text mode
- Requires emu8086 or real DOS environment

## Possible Enhancements

- Add HH:MM:SS by using CH (hours) from INT 21h
- Use color via direct video memory writes
- Add alarm or countdown timer mode
- Blink separator colon between digits
