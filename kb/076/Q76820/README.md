---
layout: page
title: "Q76820: Programs Don't Load into Upper Memory Area"
permalink: /kb/076/Q76820/
---

## Q76820: Programs Don't Load into Upper Memory Area

{% raw %}

	Article: Q76820
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.0
	Operating System(s): 
	Keyword(s): msdos
	Last Modified: 19-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You set up your system to run device drivers and programs in the upper memory
	area, but when you use the MEM /C command, nothing appears in the Upper Memory
	Area section of the MEM command output.
	
	CAUSE
	=====
	
	There are several things that can cause these symptoms:
	
	- You are running Windows version 3.0 in 386 enhanced mode and issued the MEM
	  /C command from the MS-DOS command prompt while Windows was running. The MEM
	  command does not report the contents of the upper memory area when Windows is
	  running in 386 enhanced mode.
	
	- Your system might not be set up properly to run programs in the upper memory
	  area. To make sure your system is set up properly, see "Making Sure Your
	  System Is Set Up to Run Programs in the UMA" in this document.
	
	- You are starting EMM386 with the RAM switch, which allows you to use expanded
	  memory. The RAM switch sets aside 64K of the upper memory area for use as an
	  expanded-memory page frame. This might not leave enough space in the upper
	  memory area to load any programs or device drivers. To solve this problem,
	  see "Adjusting EMM386 to Provide More Upper Memory Blocks" later in this
	  document.
	
	MAKING SURE YOUR SYSTEM IS SET UP TO RUN PROGRAMS IN THE UMA
	------------------------------------------------------------
	
	You should be able to run programs in the upper memory area (UMA) if all the
	following conditions are met:
	
	- Your computer must have an 80386 or higher processor.
	
	- Your computer must have at least 350K of extended memory available.
	
	- Your CONFIG.SYS file must contain a DEVICE command for HIMEM.SYS. This
	  command must appear before any other DEVICE commands or DEVICEHIGH commands.
	
	- Your CONFIG.SYS file must contain either a DOS=UMB or DOS=HIGH, UMB command.
	
	- Your CONFIG.SYS file must contain a DEVICE command for EMM386.EXE, which must
	  include either the NOEMS switch or the RAM switch. This command must appear
	  after the DEVICE command for HIMEM.SYS, but before any DEVICEHIGH commands.
	
	- Your CONFIG.SYS file must contain a DEVICEHIGH command for each device driver
	  you want to load into the upper memory area.
	
	- Your AUTOEXEC.BAT file should contain a LOADHIGH command for each
	  memory-resident program you want to run in the upper memory area.
	
	The following sample CONFIG.SYS file contains examples of the commands you need
	to run programs in the upper memory area:
	
	  device=c:\dos\himem.sys
	  dos=high,umb
	  device=c:\dos\emm386.exe ram
	  devicehigh=c:\util\mydriver.sys
	
	For instructions on setting up your system to run programs in the upper memory
	area, see page 317 of the "User's Guide and Reference."
	
	ADJUSTING EMM386 TO PROVIDE MORE UPPER MEMORY BLOCKS
	----------------------------------------------------
	
	You can adjust EMM386 so that it provides additional space in the upper memory
	area for use as upper memory blocks (UMBs). (This is particularly useful if you
	are starting EMM386 with the RAM switch.) First, complete the steps in Procedure
	1. If you still cannot load programs and device drivers into UMBs, complete the
	steps in Procedure 2.
	
	Procedure 1: Including Specific Portions of the Upper Memory Area
	-----------------------------------------------------------------
	
	Certain addresses in the upper memory area are normally reserved for use by
	hardware and video drivers; EMM386 does not usually make these areas available
	as UMBs. However, on many systems, the hardware and video drivers do not use all
	the reserved memory addresses. The remaining addresses can be included by EMM386
	for use as UMBs. To instruct EMM386 to include these unused areas, you use the I
	switch after the DEVICE command that starts EMM386.
	
	To allocate additional space in the upper memory area for use as UMBs, follow
	these steps:
	
	1. Create an MS-DOS version 5.0 startup disk. To do so, insert a formatted
	  floppy disk in drive A and type the following:
	
	  " sys c: a: " (without the quotation marks)
	
	2. Copy your CONFIG.SYS file to the startup disk by typing the following:
	
	  " copy c:\config.sys a:\ " (without the quotation marks)
	
	3. Edit your original CONFIG.SYS file. To edit the file using MS-DOS Editor,
	  type the following at the command prompt:
	
	  " edit c:\config.sys " (without the quotation marks)
	
	4. Locate the DEVICE command for EMM386.EXE, and insert the I switch in front of
	  the RAM or the NOEMS switch. The I switch specifies a range of addresses in
	  the upper memory area, and tells EMM386 to allocate that memory for use as
	  UMBs. The value you specify for the I switch will depend on your computer and
	  monitor type.
	
	   - If your computer is not an IBM PS/2 and does not have a monochrome
	     monitor, add the i=E000-EFFF and the i=B000-B7FF switches before the RAM
	     or NOEMS switch, as follows:
	
	       device=c:\dos\emm386.exe i=E000-EFFF i=B000-B7FF ram
	
	   - If your computer is not a PS/2 and has a monochrome monitor, add the
	     i=E000-EFFF switch before the RAM or NOEMS switch, as follows:
	
	       device=c:\dos\emm386.exe i=E000-EFFF ram
	
	   - If your computer is an IBM PS/2 and does not have a monochrome monitor,
	     add the i=B000-B7FF switch before the RAM or NOEMS switch, as follows:
	
	       device=c:\dos\emm386.exe i=B000-B7FF ram
	
	   - If your computer is an IBM PS/2 with a monochrome monitor, see Procedure
	     2.
	
	5. If you're using MS-DOS Editor, choose Exit from the File menu. When MS-DOS
	  Editor displays a dialog box prompting you to save your file, choose Yes, or
	  press ENTER.
	
	6. Restart your computer by pressing CTRL+ALT+DEL.
	
	  If your computer fails when you start it, the memory range you specified for
	  EMM386 is probably being used by hardware or video display drivers. In that
	  case, insert your startup disk in drive A and restart your computer. Then,
	  edit your CONFIG.SYS file and remove the I switch(es) you added to the DEVICE
	  command for EMM386.
	
	  If you are starting EMM386 with the RAM switch, follow Procedure 2. Otherwise,
	  contact Microsoft Support Services for further assistance.
	
	7. After your computer starts, check whether your programs were loaded into UMBs
	  successfully. To do so, type the following at the command prompt:
	
	  " mem /c |more " (without the quotation marks)
	
	  This command displays the contents of your computer's conventional and upper
	  memory, and shows where in memory each program is running. (For more
	  information about the MEM command and UMBs, see page 320 of the "User's Guide
	  and Reference.")
	
	You have solved the problem if your programs and device drivers are running in
	UMBs.
	
	If you still cannot load your programs into UMBs, your system might be using much
	of the upper memory area for hardware code. Some computers use the upper memory
	area for ROM shadowing, which can improve your computer's speed. (In ROM
	shadowing, the computer copies hardware code from the slower read-only memory
	(ROM) into the faster RAM.) To find out more about how your computer uses the
	upper memory area, see the documentation that came with it.
	
	If you cannot load programs into UMBs and you are starting EMM386 with the RAM
	switch, follow the steps in Procedure 2.
	
	Procedure 2: Reducing the Space Set Aside for Use with Expanded Memory
	----------------------------------------------------------------------
	
	If you start EMM386 with the RAM switch and programs or device drivers do not
	load into UMBs when your computer starts, there might not be enough UMBs to run
	those programs. This is because using the RAM switch sets aside 64K of the upper
	memory area as a page frame for use with expanded memory. The remaining UMBs
	might not be large enough to run your programs, even if you were able to include
	additional addresses by following Procedure 1.
	
	You can instruct EMM386 to set aside 16K of the upper memory area, rather than
	64K, as an expanded-memory page frame. This makes more UMBs available.
	
	NOTE: Use this procedure only if your applications use expanded memory according
	to the Lotus-Intel-Microsoft Expanded Memory Specification (LIM EMS) version
	4.0. Applications that follow the LIM EMS version 3.2 need the full 64K page
	frame, and will not be able to use expanded memory if you follow this
	procedure.
	
	To reduce the number of UMBs set aside for use with expanded memory, follow these
	steps:
	
	1. Type the following at the MS-DOS command prompt:
	
	  " emm386 " (without the quotation marks)
	
	  EMM386 displays information about its current memory-management activities.
	  Locate the line that reads "Page frame segment" and write down the
	  hexadecimal address that appears on that line. In the following example, the
	  page frame segment address is E000.
	
	     Page frame segment . . . . . . . . . E000  F
	
	2. Edit your original CONFIG.SYS file. To edit the file using MS-DOS Editor,
	  type the following at the MS-DOS command prompt:
	
	  " edit c:\config.sys " (without the quotation marks)
	
	3. Locate the DEVICE command for EMM386.EXE, and insert the P0 switch before the
	  RAM switch. The P0 switch should specify the address you obtained from EMM386
	  in Step 1. For example, if the page frame segment was E000, the DEVICE
	  command would appear as follows:
	
	     device=c:\dos\emm386.exe p0=E000 ram
	
	4. If you're using MS-DOS Editor, choose Exit from the File menu. When MS-DOS
	  Editor displays a dialog box prompting you to save your file, choose Yes or
	  press ENTER.
	
	5. Restart your computer by pressing CTRL+ALT+DEL.
	
	  If your computer fails when you start it, insert your startup disk in drive A
	  and restart your computer. Then, edit your CONFIG.SYS file and remove the P0
	  switch you added to the DEVICE command for Procedure 2; be sure to check the
	  page frame segment address carefully.
	
	6. After your computer starts, check whether your programs were loaded into UMBs
	  successfully. To do so, type the following at the MS-DOS command prompt:
	
	  " mem /c |more " (without the quotation marks)
	
	  This command displays the contents of your computer's conventional and upper
	  memory, and shows where in memory each program is running. (For more
	  information about the MEM /C command and UMBs, see page 320 of the "User's
	  Guide and Reference.")
	
	You have solved the problem if your programs and device drivers are running in
	UMBs.
	
	If your programs are still not running in UMBs, contact Microsoft Support
	Services for further assistance.
	
	REFERENCES
	==========
	
	See the following for additional information:
	
	"User's Guide and Reference," pages 313-326, explains how to set up your computer
	to run programs in the upper memory area.
	
	"User's Guide and Reference," page 327, explains how to troubleshoot the process
	of running programs in the upper memory area.
	
	"User's Guide and Reference," page 435, provides information about the DEVICEHIGH
	command.
	
	"User's Guide and Reference," page 518, provides information about the LOADHIGH
	command.
	
	"User's Guide and Reference," page 519, provides information about the MEM
	command.
	
	"User's Guide and Reference," page 605, provides information about EMM386.EXE
	startup parameters.
	
	"User's Guide and Reference," page 610, provides information about HIMEM.SYS
	startup parameters.
	
	Additional query words: appnote 5.00
	
	======================================================================
	Keywords          : msdos 
	Technology        : kbMSDOSSearch kbMSDOS500
	Version           : MS-DOS:5.0
	
	=============================================================================
	

{% endraw %}
