---
layout: page
title: "Q74605: Advanced WDEB386 Features and Tips"
permalink: /kb/074/Q74605/
---

## Q74605: Advanced WDEB386 Features and Tips

{% raw %}

	Article: Q74605
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 06-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains some of the more advanced WDEB386 commands and features,
	including:
	
	- Breakpoint commands (BP/BR)
	
	- Conditional execution command (J)
	
	- Default command (Z)
	
	MORE INFORMATION
	================
	
	Breakpoint Commands
	-------------------
	
	Syntax:
	
	  BP[n] <address> [<passcount>] ["<breakpoint cmds>"]
	  BR[n] E|W|R|1|2|4 <address> [<passcount>] ["<breakpoint cmds>"]
	
	A breakpoint command is a string of debugger commands that are executed when a
	breakpoint is hit. Semicolons (;) separate commands from one another. All text
	is converted to uppercase except for text surrounded by single quotation marks
	('). Two single quotation marks ('') or two double quotation marks ("") in a row
	act as an escape character and add one single quotation mark or one double
	quotation mark to the string. The maximum length of a breakpoint command is 80
	characters. Both normal (set with BP) and 386 debug register (set with BR)
	breakpoints can have breakpoint commands.
	
	The commands BP[n] "<breakpoint command>" or BR[n] "<breakpoint
	command>", where n is the breakpoint number, can be used to add or to change
	commands corresponding to existing breakpoints. Other breakpoints or the last
	breakpoint encountered can be set, cleared, disabled, or enabled.
	
	If the breakpoint has no breakpoint command string, WDEB386 executes the default
	(ZD) command. (See below for information about the default command.) The
	conditional execution command (J) is very useful in breakpoint commands (see
	below).
	
	Conditional Execution Command
	-----------------------------
	
	Syntax:
	
	  J <expr> ["<command list>"]
	
	This command executes the command list if the expression evaluates to TRUE
	(nonzero); otherwise, it continues to the next command in the command line (not
	including the ones in the command list parameter). If the command list contains
	more than one command, it must be enclosed in single or double quotation marks.
	Use a semicolon (;) to separate commands. No quotation marks are required if the
	command list contains zero or one command. The conditional execution command can
	be used in breakpoint commands to halt execution when an expression becomes true
	or in the default command (see below).
	
	Any operator, number, or symbol value can be used in the conditional expression.
	The following are the most common relational operators used with this command:
	
	  >    Greater than
	  <    Less than
	  >=   Greater than or equal to
	  <=   Less than or equal to
	  ==   Equal to
	  !=   Not equal
	  &&   Logical AND
	  ||   Logical OR
	
	The BY, WO, DW, and POI operators are very useful with the J command because they
	allow access to bytes, words, or dwords of memory in conditional expressions, as
	follows:
	
	  BY   1-byte value from the address
	  WO   2-byte value from the address
	  DW   4-byte value from the address
	  POI  4-byte 16:16 address from the address
	
	DW can be used to get a 32-bit flat address in an expression--for example %(DW
	ESI).
	
	Always put a zero in front of a hexadecimal number that begins with a nonnumeric
	character. Doing so will prevent the debugger from treating the number as a
	symbol and searching all the loaded symbol files. For example, using 0f000 is
	faster than f000.
	
	In Windows version 3.0, the backslash (\) prefix in front of registers skips the
	symbol lookup and speeds up the expression evaluation; that is, \DS:\SI is
	faster than DS:SI if many symbols have been defined. In Windows version 3.1,
	even though the \ prefix is allowed, the \ is not required to speed up register
	evaluation because registers are evaluated first.
	
	Default Command (Z)
	-------------------
	
	Syntax:
	
	  ZD                  Run the default command
	  ZL                  List the default command
	  ZS "<command list>" Set the default command
	
	The debugger's initial default command string is R (display registers).
	
	The debugger runs the default command string when:
	
	- It reaches a G (go) breakpoint
	
	- It reaches a software breakpoint set by BP (set breakpoint) or by BR (set
	  debug register breakpoint), and the breakpoint does not have a corresponding
	  breakpoint command string
	
	- It runs a P (program trace) or a T (trace) command
	
	- The user enters ZD at the debugger prompt
	
	The ZS command changes the default command. If any errors occur (for example, if
	the command line is too long), the default command returns to the R command. The
	default command can be any sequence of debugger commands each separated by a
	semicolon (;). In the default command, J commands can be useful.
	
	Examples
	--------
	
	- Display 8 bytes pointed to by DS:SI, display the registers, and stop when
	  DoSomething is executed:
	
	  bp DoSomething "db ds:si l8;r"
	
	- Display 16 bytes pointed to by DS:ESI (the default segment register is DS)
	  and continue execution every time DoSomething is executed:
	
	  bp DoSomething "db esi l10;g"
	
	- Display the window handle, message type, word parameter, and long parameter
	  of a Windows message procedure. Specifying sp+4 skips the far return
	  address:
	
	  bp MyWinProc "dw ss:sp+4 l6;g"
	
	- Display all the messages going to MyWndProc except for WM_TIMER messages:
	
	  bp MyWinProc "j wo(ss:sp+6) == 113 'g';dw ss:sp+4 l6;g"
	
	- Display and stop each time MyWinProc receives a WM_PAINT message:
	
	  bp MyWinProc "j wo(ss:sp+6) == 0f 'dw ss:sp+4 l6';g"
	
	- Break when the AX register equals zero:
	
	  bp 167:1454 "j ax == 0;g"
	
	- If the byte pointed to by DS:SI+3 equals 40h when this breakpoint is hit,
	  display the register and continue; otherwise, print the descriptor table
	  entry in DS:
	
	  bp 167:1452 "j by (ds:si+3) == 40 'r;g';dg ds"
	
	- Break when the BP address is reached in real mode:
	
	  bp 156:1455 "j (msw and 1) == 1 'g'"
	
	- Because WDEB386 uses C language conventions for Boolean expressions, a
	  shortcut that achieves the same result as above is:
	
	  bp 156:1455 "j (msw and 1) 'g'"
	
	- Default command needed to continue execution each time the application or
	  test program encounters an Interrupt 3:
	
	  zs "j (by cs:ip) == 0cc 'g'"
	
	- Trace until the word at 40:1234h is equal to 0EEDh (a primitive watchpoint).
	  This operation must be started with a T, a P, or a ZD command so that the
	  default command can be executed. If this operation is started by the G
	  command, the default command will not execute unless execution is stopped on
	  a go breakpoint or on a sticky breakpoint with no breakpoint command.
	
	  zs "j (wo 40:1234) == 0eed 'r';t"
	  zd
	
	- Perform a trace that displays each instruction until control is returned to
	  code segment or selector 2CFh. Notice that PN displays only the disassembly
	  line and not the register set, saving line space on the debugger's terminal
	  screen.
	
	  zs "u cs:ip l1; j cs == 2cf 'r';pn"
	  zd
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
