32-Bit Instruction Patterns for RISC-V

This document provides the 32-bit patterns for 15 unique RISC-V instructions, broken down into their respective fields.

 Instruction Breakdown Format
Each instruction is represented in hexadecimal, binary, and its field breakdown:

- Immediate: Immediate value or split fields (specific to instruction type)
- RS1: Source register 1
- RS2: Source register 2 (if applicable)
- Funct3: Function 3 bits
- Opcode: Operation code



 1. `beqz a5, 1017c`
- Hex: `0x02078863`
- Binary: `0000 0010 0000 0111 1000 1000 0110 0011`
- Fields:
  - Immediate: `0000 0010 000` (B-type)
  - RS1: `00111` (`a5`)
  - RS2: `00000`
  - Funct3: `000`
  - Opcode: `1100011`

2. `addi sp, sp, -16`
- Hex: `0xff010113`
- Binary: `1111 1111 0000 0001 0000 0001 0001 0011`
- Fields:
  - Immediate: `1111 1111 0000` (-16)
  - RS1: `00010` (`sp`)
  - RD: `00010` (`sp`)
  - Funct3: `000`
  - Opcode: `0010011`

3. `jal ra, 10408`
- Hex: `0x3400406f`
- Binary: `0011 0100 0000 0000 0100 0000 0110 1111`
- Fields:
  - Immediate: `0011 0100 0000 0000 0` (J-type)
  - RD: `00001` (`ra`)
  - Opcode: `1101111`

 4. `lui a0, 0x21`
- Hex: `0x00201537`
- Binary: `0000 0010 0000 0001 0101 0011 0111`
- Fields:
  - Immediate: `0000 0010 0000` (upper 20 bits)
  - RD: `01010` (`a0`)
  - Opcode: `0110111`

 5. `auipc gp, 0x13`
- Hex: `0x00013197`
- Binary: `0000 0000 0000 0001 0011 0001 1001 0111`
- Fields:
  - Immediate: `0000 0000 0001 0011` (upper 20 bits)
  - RD: `00110` (`gp`)
  - Opcode: `0010111`

6. `sw a0, 0(sp)`
- Hex: `0x00002223`
- Binary: `0000 0000 0000 0000 0010 0010 0010 0011`
- Fields:
  - Immediate: `0000 0000 0000` (S-type)
  - RS1: `00010` (`sp`)
  - RS2: `01010` (`a0`)
  - Funct3: `010`
  - Opcode: `0100011`

7. `lw a0, 0(sp)`
- Hex: `0x00002283`
- Binary: `0000 0000 0000 0000 0010 0010 1000 0011`
- Fields:
  - Immediate: `0000 0000 0000` (I-type)
  - RS1: `00010` (`sp`)
  - RD: `01010` (`a0`)
  - Funct3: `010`
  - Opcode: `0000011`

8. `mul a0, a1, a2`
- Hex: `0x02b50533`
- Binary: `0000 0010 1011 0101 0000 0101 0011 0011`
- Fields:
  - RS1: `01001` (`a1`)
  - RS2: `01010` (`a2`)
  - RD: `01010` (`a0`)
  - Funct7: `0000001`
  - Funct3: `000`
  - Opcode: `0110011`

 9. `jalr zero, 0(ra)`
- Hex: `0x00008067`
- Binary: `0000 0000 0000 0000 1000 0000 0110 0111`
- Fields:
  - Immediate: `0000 0000 0000` (I-type)
  - RS1: `00001` (`ra`)
  - RD: `00000` (`zero`)
  - Funct3: `000`
  - Opcode: `1100111`

 10. `sub a0, a1, a2`
- Hex: `0x40b50533`
- Binary: `0100 0000 1011 0101 0000 0101 0011 0011`
- Fields:
  - RS1: `01001` (`a1`)
  - RS2: `01010` (`a2`)
  - RD: `01010` (`a0`)
  - Funct7: `0100000`
  - Funct3: `000`
  - Opcode: `0110011`

 11. `xor a0, a1, a2`
- Hex: `0x00b50533`
- Binary: `0000 0000 1011 0101 0000 0101 0011 0011`
- Fields:
  - RS1: `01001` (`a1`)
  - RS2: `01010` (`a2`)
  - RD: `01010` (`a0`)
  - Funct7: `0000000`
  - Funct3: `100`
  - Opcode: `0110011`

12 `or a0, a1, a2`
- Hex: `0x02b51533`
- Binary: `0000 0010 1011 0101 0001 0101 0011 0011`
- Fields:
  - RS1: `01001` (`a1`)
  - RS2: `01010` (`a2`)
  - RD: `01010` (`a0`)
  - Funct7: `0000000`
  - Funct3: `110`
  - Opcode: `0110011`

 13. `and a0, a1, a2`
- Hex: `0x02b52533`
- Binary: `0000 0010 1011 0101 0010 0101 0011 0011`
- Fields:
  - RS1: `01001` (`a1`)
  - RS2: `01010` (`a2`)
  - RD: `01010` (`a0`)
  - Funct7: `0000000`
  - Funct3: `111`
  - Opcode: `0110011`

14. `slli a0, a1, 2`
- Hex: `0x00251513`
- Binary: `0000 0000 0010 0101 0001 0101 0001 0011`
- Fields:
  - Immediate: `00000 00010` (I-type, shift amount)
  - RS1: `01001` (`a1`)
  - RD: `01010` (`a0`)
  - Funct3: `001`
  - Opcode: `0010011`

 15. `srli a0, a1, 2`
- Hex: `0x00255513`
- Binary: `0000 0000 0010 0101 0101 0101 0001 0011`
- Fields:  
  - Immediate: `00000 00010` (I-type, shift amount)  
  - RS1: `01001` (`a1`)  
  - RD: `01010` (`a0`)  
  - Funct3: `101`  
  - Opcode: `0010011`  

