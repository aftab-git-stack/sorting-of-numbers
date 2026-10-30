# sorting-of-numbers

## Aim
To write and execute an Assembly Language Program for sorting data in Ascending and Descending order using 8051 microcontroller on Keil software.

---

## Apparatus Required
- Personal Computer
- Keil µVision software

---

## Algorithm (ASCENDING ORDER)
1. Initialize the register **R7** with count (number of passes).
2. Get the first two elements into two registers.
3. Compare the two elements:
   - If the first element is greater than the second, exchange their data.
   - Otherwise, continue to the next pair.
4. Increment the pointer and decrement register **R6**.
5. Repeat the comparison until all adjacent elements are checked.
6. Decrement **R7** and repeat the process until all passes are completed.
7. Stop the program.

---

## Program (Ascending order)

```asm
ORG 0000H

    MOV 30H, #45H
    MOV 31H, #12H
    MOV 32H, #78H
    MOV 33H, #23H
    MOV 34H, #56H

    MOV R7, #04H

PASS:
    MOV R0, #30H
    MOV R6, #04H

LOOP:
    MOV A, @R0
    INC R0
    MOV R5, @R0

    CJNE A, 05H, COMPARE
    SJMP NEXT

COMPARE:
    JC NEXT

    MOV @R0, A
    DEC R0
    MOV @R0, R5
    INC R0

NEXT:
    DJNZ R6, LOOP
    DJNZ R7, PASS

HERE:
    SJMP HERE

END
```

## OUTPUT (Ascending order)

**Initial Data:**

| Memory Location | Data |
|---|---|
| 30H | 45H |
| 31H | 12H |
| 32H | 78H |
| 33H | 23H |
| 34H | 56H |

**Sorted Data (Ascending Order):**

| Memory Location | Data |
|---|---|
| 30H | 12H |
| 31H | 23H |
| 32H | 45H |
| 33H | 56H |
| 34H | 78H |

---

## Algorithm (Descending order)
1. Initialize the register **R7** with count.
2. Get the first two elements into two registers.
3. Compare the two elements:
   - If the first element is smaller than the second, exchange their data.
   - Otherwise, continue to the next pair.
4. Increment the pointer and decrement register **R6**.
5. Repeat the comparison until all adjacent elements are checked.
6. Decrement **R7** and repeat the process until all passes are completed.
7. Stop the program.

---

## Program (Descending order)

```asm
ORG 0000H

    MOV 30H, #45H
    MOV 31H, #12H
    MOV 32H, #78H
    MOV 33H, #23H
    MOV 34H, #56H

    MOV R7, #04H

PASS:
    MOV R0, #30H
    MOV R6, #04H

LOOP:
    MOV A, @R0
    INC R0
    MOV R5, @R0

    CJNE A, 05H, COMPARE
    SJMP NEXT

COMPARE:
    JNC NEXT

    MOV @R0, A
    DEC R0
    MOV @R0, R5
    INC R0

NEXT:
    DJNZ R6, LOOP
    DJNZ R7, PASS

HERE:
    SJMP HERE

END
```

## OUTPUT (Descending order)

**Initial Data:**

| Memory Location | Data |
|---|---|
| 30H | 45H |
| 31H | 12H |
| 32H | 78H |
| 33H | 23H |
| 34H | 56H |

**Sorted Data (Descending Order):**

| Memory Location | Data |
|---|---|
| 30H | 78H |
| 31H | 56H |
| 32H | 45H |
| 33H | 23H |
| 34H | 12H |

---

## RESULT:
Thus the sorting of given data was done using 8051 Keil software.
