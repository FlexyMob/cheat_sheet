# GDB / PWNGDB Cheat Sheet

DOWNLOAD <pwndgb>PWNGDB</pwndgb> => [HEREEEEE](https://github.com/pwndbg/pwndbg)

Writted by Moi and helped by [https://cheatography.com/cactuarnation/](https://cheatography.com/cactuarnation/cheat-sheets/gdb-and-pwndbg/)

`
If you see any mistakes (command, syntaxes, language), let me know!
`

<hr/>

## <b>Disassamble, examine code section</b>

| <y>command</y> | <y>description</y> |
| ----------- | ----------- |
| <r>list</r> (gcc -g must be enable) | diplay original code |
| <r>disassemble</r> <v>\<function name\></v> | disassemble a function |
| <r>disassemble</r> <v>\<address\></v> | disassemble at address |

## <b>Running</b>
| <y>command</y> | <y>description</y> |
| ----------- | ----------- |
| <r>list</r> (gcc -g must be enable) | diplay original code |
| <r>run</r> | run the program until termination or breakpoint |
| <r>start</r> | start the program and pause at main() |

> TIPS: execute shell command in GDB :
-   run < <(echo "hello!")
-   run \`echo "hello!"\`
-   r < somefile
-   r arg1 arg2

> TIPS:
-   command can be reduce. Exemple : run to "r", step to "s" etc..

## <b>Breaking</b>

| <y>command</y> | <y>description</y> |
| ----------- | ----------- |
| <r>break</r> <v>\<function name\></v> | add breakpoint at the start of a function |
| <r>break</r> <v>\<address\></v> | add breakpoint at a specific address |
| <r>break</r> <v>\<function name\>+\<offset\></v> |  add breakpoint at the start of a function + offset (disass the function to see it!) |
| <r>bl</r> | list all breakpoints |
| <r>d</r> br| delete all breakpoint |
| <r>db</r> <v>\<breakpoint\></v> | delete specific breakpoint |
| <r>db</r> <v>\<breakpoint\></v> | disable specific breakpoint |
| <r>be</r> <v>\<breakpoint\></v> | enable specific breakpoint |

[or with clear command (click me!)](https://ftp.gnu.org/old-gnu/Manuals/gdb/html_node/gdb_31.html)

## <b>Stepping</b>
| <y>command</y> | <y>description</y> |
| ----------- | ----------- |
| <r>nexti</r> | execute next instruction |
| <r>continue</r> | continue execution until termination or to the next breakpoint |
| <r>step</r> | Execute instru­ction and step into a function |

## x/whatwhatwhat?? (displaying format)
-   x/x => display value in hexadecimal
-   x/d => display value in decimal
-   x/u => display value in decimal unsigned
-   x/s => display value and try to convert it in string

## x/whatwhatwhat?? ("data slicing")
-   x/xb => display bytes by bytes 0x00 0x01 0x02
-   x/xw => display words by words (4bytes) 0x03020100 (little endian) (DEFAULT)
-   x/xdw => display word*double
-   x/xqw => display word*quadruple

## x/whatwhatwhat?? ("values displayed")
-   x/4xb => display 4 bytes in hex
-   x/8xw => display 8 words in hex
-   x/16xdw => display 16 words in hex

## <b>Examining data</b>
| <y>command</y> | <y>description</y> |
| ----------- | ----------- |
| <r>x/10i</r> <v>$(r)(e)ip</v> | see 10 next instructions from (r)(e)ip register |
| <r>x/10xw</r> <v>$(r)(e)sp</v> | see (in hex) 10 words (8 bytes in x64) of (r)(e)sp |
| <r>x/10xw</r> <v>*\<function\>+offset</v> | see 10 next instructions a *function+offset |
| <r>print</r> <v>\<variable\></v>  | print address of variable |
| <r>print</r> <v>&\<variable\></v>  | print value of variable |
| <r>p/d</r> <v>\<variable\></v>  | print address of variable in decimal |
| -------------------------------------- |
| <r>bt [full] | examine stack (full is optionnal) |

> TIPS:
-   when "print" is called, gdb save the value in variable "$x" (x start at 1)

## <b>Modifying data</b>
| <y>command</y> | <y>description</y> |
| ----------- | ----------- |
| <r>set</r> <v>$(r)(e)ax=4</v> | set (r)(e)ax to 4|
| <r>set</r> <v>*0xffffff=8</v> | set address to 8 |
| <r>set</r> <v>($(r)(e)ax - 8) = 16</v> | Set the value pointed to by (r)(e)ax-8 to 16 |

## <b>other PWNGDB (Important!!)</b>
| <y>command</y> | <y>description</y> |
| ----------- | ----------- |
| <r>context</r> | display context with great layout :O |
| <r>stack</r> <v>[row]</v> | view the stack (row number is optionnal) |
| <r>search</r> <v>"hello"</v> | Search in memory "Hello" |
| <r>p/d</r> <v>0x7fff­fff­fe278 - 0x7fff­fff­fe220</v>| Get distance between addresses |
| <r>distance</r> <v>0x7fff­fff­fe220 0x7fff­fff­fe278</v> | Get distance between addresses |
| <r>checksec</r> | Check enabled securities |
| <r>hexdump</r> <v>$register</v> | H3xDUMP 1T!! |
| <r>vmmap</r> | print virtual memory mapping |


