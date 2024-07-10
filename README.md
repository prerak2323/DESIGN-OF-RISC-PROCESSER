# DESIGN-OF-RISC-PROCESSER


# MIPS Assembly Instructions

| Instruction        | Assembly Code            | Operation                      | Comments                                                                                   |
|--------------------|--------------------------|--------------------------------|--------------------------------------------------------------------------------------------|
| Add                | `add $s1, $s2, $s3`      | $s1 = $s2 + $s3                | 2’s complement overflow detected                                                           |
| Subtract           | `sub $s1, $s2, $s3`      | $s1 = $s2 - $s3                | Overflow detected                                                                          |
| Add Immediate      | `addi $s1, $s2, k`       | $s1 = $s2 + k                  | Overflow detected; k is a 16-bit constant, sign-extended and added                          |
| Add Unsigned       | `addu $s1, $s2, $s3`     | $s1 = $s2 + $s3                | Overflow not detected                                                                      |
| Subtract Unsigned  | `subu $s1, $s2, $s3`     | $s1 = $s2 - $s3                | Overflow not detected                                                                      |
| Add Immediate Unsigned | `addiu $s1, $s2, k`  | $s1 = $s2 + k                  | Same as addi except no overflow detected                                                   |
| Move from Co-processor Register | `mfc0 $s1, $epc` | $s1 = EPC                  | epc is exception program counter                                                           |
| Multiply           | `mult $s2, $s3`          | Hi, Lo = $s2 * $s3             | 64-bit signed product in Hi, Lo                                                             |
| Multiply Unsigned  | `multu $s2, $s3`         | Hi, Lo = $s2 * $s3             | 64-bit unsigned product in Hi, Lo                                                          |
| Divide             | `div $s2, $s3`           | Lo = $s2 / $s3, Hi = $s2 % $s3 | Lo quotient, Hi remainder                                                                  |
| Divide Unsigned    | `divu $s2, $s3`          | Lo = $s2 / $s3, Hi = $s2 % $s3 | Unsigned quotient and remainder                                                            |
| Move from Hi       | `mfhi $s1`               | $s1 = Hi                       |                                                                                            |
| Move from Lo       | `mflo $s1`               | $s1 = Lo                       |                                                                                            |

# MIPS Assembly Instructions

| Instruction            | Assembly Code          | Operation              | Comments                                          |
|------------------------|------------------------|------------------------|---------------------------------------------------|
| And                    | `and $s1, $s2, $s3`    | $s1 = $s2 AND $s3      | logical AND                                       |
| Or                     | `or $s1, $s2, $s3`     | $s1 = $s2 OR $s3       | logical OR                                        |
| And Immediate          | `andi $s1, $s2, k`     | $s1 = $s2 AND k        | k is a 16-bit constant; k is zero-extended first  |
| Or Immediate           | `ori $s1, $s2, k`      | $s1 = $s2 OR k         | k is a 16-bit constant; k is zero-extended first  |
| Shift Left Logical     | `sll $s1, $s2, k`      | $s1 = $s2 << k         | Shift left by 5-bit constant k                    |
| Shift Right Logical    | `srl $s1, $s2, k`      | $s1 = $s2 >> k         | Shift right by 5-bit constant k                   |

# MIPS Assembly Instructions

| Instruction          | Assembly Code          | Operation                | Comments                                                                 |
|----------------------|------------------------|--------------------------|--------------------------------------------------------------------------|
| Load Word            | `lw $s1, k($s2)`       | $s1 = Memory[$s2 + k]    | Read 32 bits from memory; memory address is $s2 + k; k is a 16-bit offset|
| Store Word           | `sw $s1, k($s2)`       | Memory[$s2 + k] = $s1    | Write 32 bits to memory; memory address is $s2 + k; k is a 16-bit offset |
| Load Halfword        | `lh $s1, k($s2)`       | $s1 = Memory[$s2 + k]    | Read 16 bits from memory; sign-extend and load into register             |
| Store Halfword       | `sh $s1, k($s2)`       | Memory[$s2 + k] = $s1    | Write 16 bits to memory                                                 |
| Load Byte            | `lb $s1, k($s2)`       | $s1 = Memory[$s2 + k]    | Read byte from memory; sign-extend and load into register                |
| Store Byte           | `sb $s1, k($s2)`       | Memory[$s2 + k] = $s1    | Write byte to memory                                                    |
| Load Byte Unsigned   | `lbu $s1, k($s2)`      | $s1 = Memory[$s2 + k]    | Read byte from memory; byte is zero-extended                             |
| Load Upper Immediate | `lui $s1, k`           | $s1 = k << 16            | Load constant k to upper 16 bits of register                             |


# MIPS Assembly Instructions

| Instruction                   | Assembly Code          | Operation                                   | Comments                                                                                     |
|-------------------------------|------------------------|---------------------------------------------|----------------------------------------------------------------------------------------------|
| Branch on Equal               | `beq $s1, $s2, k`      | If ($s1 == $s2) go to PC + 4 + k * 4        | Branch if registers are equal; PC-relative branch; Target PC = PC + 4 + Offset * 4; k is sign-extended |
| Branch on Not Equal           | `bne $s1, $s2, k`      | If ($s1 != $s2) go to PC + 4 + k * 4        | Branch if registers are not equal; PC-relative branch; Target PC = PC + 4 + Offset * 4; k is sign-extended |
| Set on Less Than              | `slt $s1, $s2, $s3`    | If ($s2 < $s3) $s1 = 1 else $s1 = 0         | Compare and set                                                                            |
| Set on Less Than Immediate    | `slti $s1, $s2, k`     | If ($s2 < k) $s1 = 1 else $s1 = 0           | Compare and set; k is 16-bit constant; sign-extended and compared                           |
| Set on Less Than Unsigned     | `sltu $s1, $s2, $s3`   | If ($s2 < $s3) $s1 = 1 else $s1 = 0         | Compare and set; unsigned                                                                  |
| Set on Less Than Immediate Unsigned | `sltiu $s1, $s2, k` | If ($s2 < k) $s1 = 1 else $s1 = 0           | Compare and set; natural numbers; k, the 16-bit constant, is sign-extended; no overflow     |

# MIPS Assembly Instructions

| Instruction       | Assembly Code    | Operation                             | Comments                                                                                      |
|-------------------|------------------|---------------------------------------|-----------------------------------------------------------------------------------------------|
| Jump              | `j addr`         | Go to addr * 4                        | Target address is addr * 4; addr is 26 bits                                                   |
| Jump Register     | `jr $reg`        | Go to $reg                            | Target address is the content of register $reg                                                |
| Jump and Link     | `jal addr`       | Go to addr * 4; $31 = PC + 4          | For procedure call, target address is addr * 4; return address is saved in the link register $31 |

