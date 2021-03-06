---
layout: page
title: "Q123688: Turning a 16-bit Protected Segment into a 32-bit Segment"
permalink: /kb/123/Q123688/
---

## Q123688: Turning a 16-bit Protected Segment into a 32-bit Segment

{% raw %}

	Article: Q123688
	Product(s): Microsoft Macro Assembler
	Version(s): 6.0,6.1,6.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 6.0, 6.1, 6.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	By default, 32-bit code created in MASM exists in 16-bit segments. This article
	shows by example how to use DPMI calls to change a 16-bit segment into a 32-bit
	segment.
	
	NOTE: On a 386, almost no improvement in performance results from using 32-bit
	code in a 32-bit segment over using 32-bit code in a 16-bit segment. There may
	be slight performance improvement on a 486 due to the effects of the 66h prefix
	byte on instruction pipelining.
	
	MORE INFORMATION
	================
	
	The following code fragment uses DPMI calls to turn a 16-bit protected mode
	segment into a 32-bit protected mode segment. A number of the instructions are
	encoded using the DB directive because you need to generate USE16 instructions
	inside of a USE32 segment. The sample includes an interface function so that you
	can call the 32-bit segment from a 16-bit C, C++, or FORTRAN module.
	
	NOTE: Your debugger may still report these segments to be 16-bit segments. It all
	depends on what the debugger expects.
	
	Sample Code
	-----------
	
	     .MODEL large
	     .386
	
	     .CODE
	     SwitchInterface PROC FAR16
	        call FAR32 PTR Switch16bitTo32bit
	        ret
	     SwitchInterface ENDP
	
	     CODE32 SEGMENT PARA PUBLIC USE32 'CODE'
	     Switch16bitTo32bit PROC FAR32
	        xor eax, eax                       ;zero set
	        xor eax, DWORD PTR 0C08B0000h      ;zero clear for 32-bit
	        jz Still16bit                      ;zero set for 16-bit
	        ret
	
	     Still16bit:
	        DB 083h, 0ECh, 008h        ;sub sp, 8
	        DB 08Ch, 0D0h              ;mov ax, ss
	        DB 08Eh, 0C0h              ;mov es, ax
	        DB 08Bh, 0FCh              ;mov di, sp
	
	        DB 08Ch, 0CBh              ;mov bx, cs
	        DB 0B8h, 00Bh, 0000h       ;mov ax, 000Bh
	        int 31h
	
	        DB 026h, 080h, 04Dh, 006h, 040h    ;or BYTE PTR es:[di+6], 40h
	        DB 0B8h, 00Ch, 0000h       ;mov ax, 000Ch
	        int 31h
	
	     Now32bit:
	        add sp, 8
	        ret
	     Switch16bitTo32bit ENDP
	     CODE32 ENDS
	
	     END
	
	Additional query words: kbinf 6.00 6.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM600 kbMASM610 kbMASM611
	Version           : :6.0,6.1,6.11
	
	=============================================================================
	

{% endraw %}
