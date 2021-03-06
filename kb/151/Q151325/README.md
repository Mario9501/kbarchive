---
layout: page
title: "Q151325: Bookshelf '96-'97: Manual Installation On Windows 3.1"
permalink: /kb/151/Q151325/
---

## Q151325: Bookshelf '96-'97: Manual Installation On Windows 3.1

{% raw %}

	Article: Q151325
	Product(s): Microsoft Home Multimedia Titles
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Bookshelf 1996-97 for Windows 
	- the operating system: Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides instructions to manually install Bookshelf '96-'97 on a
	computer system running Microsoft Windows 3.x.
	
	MORE INFORMATION
	================
	
	These instructions assume:
	
	- Your hard drive is drive C:
	
	- Your Windows folder is C:\Windows
	
	- Your CD-ROM drive is drive D
	
	- Your Destination folder is C:\Books96
	
	If your hard disk drive, destination folder (directory), Windows folder, or
	CD-ROM drive letters are different, replace the drive letters and folder names
	throughout this article with the drive letters and folder names on your
	computer.
	
	NOTE: The following instructions discuss copying, editing, and modifying folders
	and files. For more information about how to accomplish these tasks in Windows,
	see your Windows printed documentation or online Help.
	
	When copying files, exit Windows and copy from the MS-DOS command prompt. Allow
	MS-DOS to overwrite any files it finds already on your hard drive.
	
	1. Create a folder named C:\Books96 on your hard drive.
	
	  For example, type the following at the MS-DOS command prompt and press the
	  ENTER key at the end of the line:
	
	  "md c:\books96" (without the quotation marks)
	
	2. Copy all the files from the D:\Aamsstp\App16 to C:\Books96. The files are:
	
	  Bs9616.exe
	  Bs9616s.exe
	  Bs96ctw.exe
	  Bs96spl.dll
	  Deco.dll
	  Mssp2_En.lex
	  Qkeyslib.dll
	  Qs9616.exe
	  Qs9616.hlp
	  Tv16dcmp.dll
	
	  For example, to copy Deco.dll, type the following at the MS-DOS command prompt
	  and press ENTER at the end of the line:
	
	  "copy d:\aamsstp\app16\deco.dll c:\books96" (without the quotation marks)
	
	3. Copy the following files from D:\Aamsstp\App to C:\Books96:
	
	  Mmb.dll
	  Bs96ingn.lst
	  Bsmmplyr.exe
	
	4. Copy the following file from D:\ to C:\Books96:
	
	  Readme.txt
	
	5. Copy the following files from D:\Aamsstp\System16 to C:\Windows\System:
	
	  Acmcmprs.dll
	  Avicap.dll
	  Avifile.dll
	  Bshelf93.exe
	  Cleanup.reg
	  Compobj.dll
	  Ctl3dv2.dll
	  Dispdib.dll
	  Dva.386
	  Iccvid.drv
	  Imaadpcm.acm
	  Iniupd.dll
	  Ir21_r.dll
	  Ir32.dll
	  Map_win.hlp
	  Mciavi.drv
	  Mcimmp.drv
	  Mciole.dll
	  Mfcans32.dll
	  Mfcuia32.dll
	  Mplayer.reg
	  Msacm.dll
	  Msacm.drv
	  Msadpcm.acm
	  Msgsm610.acm
	  Msrle.drv
	  Msvidc.drv
	  Msvideo.dll
	  Ole2.dll
	  Ole2.reg
	  Ole2conv.dll
	  Ole2disp.dll
	  Ole2nls.dll
	  Ole2prox.dll
	  Stdole.tlb
	  Storage.dll
	  Typelib.dll
	  Ver.dll
	  Vshare.386
	
	6. Copy the following files from D:\Aamsstp\System16 to C:\Windows:
	
	  Mplayer.exe
	  Mplayer.hlp
	
	7. Copy the following file from D:\Aamsstp\System16 to C:\Windows:
	
	  Msinfo.exe
	
	8. Use a text editor, such as Microsoft Notepad, to make the following changes
	  to the Bshelf96.ini file, which is located in the Windows folder.
	
	  NOTE: If the Bshelf96.ini file does not already exist, create one in the
	  Windows folder with the following entries:
	
	        [Options]
	        drive=D:\ 
	        Sounds=1
	        Tooltips=1
	
	        [Find]
	        Near=8
	
	        [Colors]
	        JumpColor=0 0 128
	        PopUpColor=128 0 128
	
	        [GrabText]
	        winfile=0
	
	        [Program]
	        App=C:\BOOKS96\bs9616.exe
	
	9. Use a text editor to make the following changes to the Windows initialization
	  files, which are located in the Windows folder:
	
	  Win.ini File Changes
	  --------------------
	
	        [MCI Extentions]
	        avi=AVIVideo
	
	        [Bookshelf]
	        App=C:\Books96\bs9616s.exe
	
	        [Microsoft System Info]
	        Msinfo=C:\Windows\Msapps\Msinfo\Msinfo.exe
	
	  Changes to the System.ini File
	  ------------------------------
	
	        [mci]
	        AVIVideo=mciavi.drv
	        MMMovie=mcimmp.drv
	
	        [drivers]
	        MSACM.msgsm610=msgsm610.acm
	        MSACM.msadpcm=msadpcm.acm
	        MSACM.imaadpcm=imaadpcm.acm
	        VIDC.MSVC=msvidc.drv
	        VIDC.RT21=ir21_r.dll
	        VIDC.CVID=iccvid.drv
	        VIDC.IV31=ir32.dll
	        VIDC.MRLE=msrle.drv
	        VIDC.YVU9=ir21_r.dl
	        VIDC.IV32=ir32.dll
	        WaveMapper=msacm.drv
	
	        [msacm.msgsm610]
	         MaxRTDecodeSamplesPerSec=22050
	
	        [386enh]
	        device=dva.386
	        device=vshare.386
	
	  Control.ini File Changes
	  ------------------------
	
	        [drivers.desc]
	        msacm.drv=Microsoft Sound Mapper V2.00
	        msadpcm.acm=Microsoft ADPCM Codec V2.00
	        imaadpcm.acm=Microsoft IMA ADPCM Codec V2.00
	
	10. Start Windows.
	
	11. Install the fonts included on the compact disc using the following steps:
	  a. Open the Windows Control Panel, usually located in the Main program group
	     of Program Manager.
	
	  b. On Settings menu, click Fonts.
	
	  c. Click Add.
	
	  d. Change the drive letter to match the letter of your CD-ROM drive.
	
	  e. In the Directories area, double-click the Aamsstp folder, then
	     double-click the Fonts16 folder.
	
	  f. After the fonts appear in the List of Fonts:, click Select All, and then
	     click OK.
	
	  g. If messages about the fonts already being installed appear, click OK.
	
	  h. Click Close.
	
	  i. Close the Control Panel.
	
	12. Open file manager and double-click the following files:
	
	  C:\Windows\System\Ole2.reg
	  C:\Windows\System\Cleanup.reg
	  C:\Windows\System\Mplayer.reg
	
	  After you click each one, you should get a "successfully registered" message.
	  Click OK.
	
	13. Register the Bookshelf Update file type by following these steps:
	  a. In Program Manager, on the File menu, click Run.
	
	  b. Type the following, and then press ENTER:
	
	  "regedit" (without the quotation marks)
	
	  c. When Registration Info Editor appears, on the Edit menu, click Add File
	     Type.
	
	  d. Type the following data into the corresponding fields:
	
	         Field           Data
	         -----           ----
	         Identifier      lstfile
	         File Type       lstfile
	         Command         c:\books96\bs9616s.exe %1
	
	  e. Click Uses DDE to clear the checkbox.
	
	  f. Click OK and exit the Editor.
	
	14. Add the Program icons. As a guide, use the "Creating Program Manager Icons"
	  section.
	
	15. Restart Windows. Installation is now complete.
	
	Creating Program Manager Icons
	------------------------------
	
	1. Open the Microsoft Reference group. If this group does not already exist,
	  create it as follows:
	  a. On the File menu, click New.
	
	  b. Click Program Group, and then click OK.
	
	  c. In the Description box, type the following, and then click OK:
	
	  "Microsoft Reference" (without the quotation marks)
	
	2. On the File menu, click New.
	
	3. Click Program Item, and then click OK.
	
	4. Type the following Description and Command Line information, and then click
	  OK:
	
	     Description:       Bookshelf 1996-97
	     Command Line:      c:\books96\bs9616.exe
	
	5. Repeat steps 2-4 for each of the following items:
	
	  Item 2
	  ------
	
	     Description:       QuickShelf 1996-97
	     Command Line:      c:\books96\qs9616.exe
	
	  Item 3
	  ------
	
	     Description:       Bookshelf 1996-97 ReadMe
	     Command Line:      c:\books96\readme.txt
	
	  Item 4
	  ------
	
	     Description:       Microsoft Multimedia Catalog
	     Command Line:      d:\mmcat\mmcat.exe
	
	6. Open the Startup group.
	
	7. On the File menu, click New.
	
	8. Click Program Item, and then click OK.
	
	9. Type the following Description and Command Line information, and then click
	  OK:
	
	     Description:       QuickShelf 1996-97
	     Command Line:      c:\books96\qs9616.exe
	
	Setup is complete.
	
	Additional query words: '96-'97 mmtitles kbmm 96 1996 97 1997 96-97 multi media multimedia multi-media install setup set up installation
	
	======================================================================
	Keywords          :  
	Technology        : kbOSWinSearch kbHomeMMsearch kbZNotKeyword6 kbBookshelfSearch kbBookShelf1996 kbBookShelf1997 kbOSWin310 kbOSWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
