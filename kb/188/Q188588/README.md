---
layout: page
title: "Q188588: VB5SP3DS.EXE Contains Visual Basic SP3 Debugging Symbols"
permalink: /kb/188/Q188588/
---

## Q188588: VB5SP3DS.EXE Contains Visual Basic SP3 Debugging Symbols

{% raw %}

	Article: Q188588
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,97sp3
	Operating System(s): 
	Keyword(s): kbfile kbDebug kbVBp kbVBp500 kbVS97sp3 kbGrpDSVB kbDSupport
	Last Modified: 13-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Studio 97sp3 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft has made available to the public debugging symbols to aid in the
	debugging of applications created with Microsoft Visual Basic 5.0 Service Pack
	Three (SP3) components. These symbols allow debugging tools such as Visual C++,
	Dr. Watson, NTSD/CDB, and WinDBG to obtain stack traces describing the functions
	within built components, such as MSVBVM50.DLL, that are being called when a
	crash occurs. These traces would aid developers and Microsoft support engineers
	in diagnosing the problems.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  Vb5sp3ds.exe
	  (http://download.microsoft.com/download/vb50ent/Sample30/1/W9XNT4/EN-US/Vb5sp3ds.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	To install the debugging symbols, first extract them from VB5SP3DS.EXE. When
	VB5SP3DS.EXE is run, it will prompt you for a directory (default: C:\WINNT) in
	which to extract the files. At completion, the following directory tree will be
	created below the directory you have chosen:
	
	\SYMBOLS\dll
	
	07/19/97  04:54p                 1,340 vb5en.dbg
	07/19/97  04:59p               136,616 MSConDes.dbg
	07/19/97  04:59p               583,236 MSRDO20.dbg
	07/19/97  04:54p             2,679,216 MSVBVM50.dbg
	07/19/97  04:45p               168,292 VB5DB.dbg
	07/19/97  04:59p                38,696 MSCDRun.dbg
	07/19/97  04:45p                 1,672 vb5ide.dbg
	10/01/97  11:48a             2,769,076 VBA5.dbg
	
	\SYMBOLS\exe
	
	07/19/97  04:45p             3,453,180 VB5.dbg
	
	\SYMBOLS\ocx
	
	07/19/97  04:59p               224,428 comct232.dbg
	09/17/97  09:07p               298,884 DBList32.dbg
	07/19/97  04:59p               146,792 ComDlg32.dbg
	07/19/97  04:59p               713,896 ComCtl32.dbg
	07/19/97  04:59p               216,072 mci32.dbg
	07/19/97  04:59p               140,332 MSComm32.dbg
	07/19/97  04:59p               281,260 msflxgrd.dbg
	09/11/97  09:24p               161,384 msinet.dbg
	07/19/97  04:59p               176,916 msmapi32.dbg
	07/19/97  04:59p               170,632 MSMask32.dbg
	07/19/97  05:00p               143,064 mswinsck.dbg
	07/19/97  05:00p               129,684 PicClp32.dbg
	07/19/97  05:00p               256,740 RichTx32.dbg
	07/19/97  05:00p                95,932 SysInfo.dbg
	07/19/97  05:00p               298,772 tabctl32.dbg
	07/19/97  04:59p               183,320 MSRDC20.dbg
	
	These .dbg files are for debugging Visual Studio SP3 components on Intel
	platforms only.
	
	Different debugging tools have different methods of locating debugging symbols.
	Usually, you can put a .dbg file in the same directory as the corresponding
	.exe, .dll, or .ocx file. For instance, MSVBVM50.DLL is in C:\Winnt\System32
	directory; you can copy Msvbvm50.dbg to C:\Winnt\System32 and most debuggers
	will find it. Some debuggers are set up by default to find symbols in the
	Symbols directory if it exists below your system root directory (for example
	C:\WINNT\Symbols\). You should consult your debugger documentation for more
	information before installing the symbols.
	
	The .dbg files in VB5SP3DS.EXE contain symbols in the Common Object File Format
	(COFF). To use them with Visual C++ 5.0, you may need to copy SYMCVT.DLL from
	your Visual C++ CD-ROM to your Windows system (system32 for NT) directory.
	DRWTSN32.EXE shipped with NT understands COFF symbols without SYMCVT.DLL.
	
	Additional query words: Vb5sp3ds
	
	======================================================================
	Keywords          : kbfile kbDebug kbVBp kbVBp500 kbVS97sp3 kbGrpDSVB kbDSupport 
	Technology        : kbVSsearch kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB500 kbVS97SP3 kbVS97Search
	Version           : WINDOWS:5.0,97sp3
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
