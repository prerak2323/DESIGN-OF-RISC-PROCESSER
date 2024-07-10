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
