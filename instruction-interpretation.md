### Reference
All the instruction links and one of the footnotes come from this [ARM Cortex-M0 User Guide](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0497a/BABIHJGA.html).

### Interpretation assignment
| Label | Instruction | Intepretation |
| --- | --- | --- |
| negate: | | _Label (corresponds to the address of the first following instruction)_ |
| | [sub](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #8` | Subtact 8 from the stack pointer (and store into the stack pointer) |
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r0, [sp, #4]`<sup>[1](#footnotes)</sup> | Write (the contents of) r0 to the memory with address sp + 4 |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Load r3 from the address sp + 4 |
| | [rsbs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)    `r3, r3, #0`  | Subtract r3 from zero, and updates the N, Z, C and V flags |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` | Write/Copy value of r3 to r0, also updates the N and Z flags |
| | [add](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #8` |  Add 8 to stack pointer, and places/stores the result in stack pointer|
| | [bx](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)      `lr` | Return link register -- from function call |
| | | |
| main: | | _Label (corresponds to the address of the first following instruction)_ |
| | [push](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIAJHJ.html)    `{lr}` | Push/store link register onto the stack |
| | [sub](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #12` | Subtract 12 from the stack pointer, and store into the stack pointer |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, #6` |  Write/Copy 6 into r3, also updates the N and Z flags |
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Write (the contents of) r3 to the memory with address sp + 4 |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Load r3 from the address sp + 4 |
| | [cmp](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIHIEI.html)     `r3, #0` | Compare contents of r3 with 0 (updates the N, Z, C and V flags according to the result) |
| | [ble](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)<sup>[2](#footnotes)</sup>     `.L4` | Branch to .L4 if r3 is greater than zero |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Load r3 from the address sp + 4 |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` | Write/Copy value of r3 to r0, also updates the N and Z flags |
| | [bl](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)      `negate` | |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, r0` | Write/Copy value of r0 to r3, also updates the N and Z flags |
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Write (the contents of) r3 to the memory with address sp + 4 |
| | | |
| .L4: | | _Label (corresponds to the address of the first following instruction)_ |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, #0` | Write/Copy value of 0 into r3, also updates the N and Z flags |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` | Write/Copy value of r3 into r0, also updates the N and Z flags |
| | [add](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #12` | Add 12 to stack pointer, and places/stores the result in stack pointer |
| | [pop](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIAJHJ.html)     `{pc}` | Pop PC from stack, and then branch to the new PC |

### Footnotes

**1** _[Addressing modes](http://www.davespace.co.uk/arm/introduction-to-arm/addressing.html)_ 

**2** _[Conditional execution](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0497a/BABEHFEF.html)_ 
