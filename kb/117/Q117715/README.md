---
layout: page
title: "Q117715: Slow Performance over IBM Software Source Routing Bridge"
permalink: /kb/117/Q117715/
---

## Q117715: Slow Performance over IBM Software Source Routing Bridge

{% raw %}

	Article: Q117715
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): 3.11
	Operating System(s): 
	Keyword(s): kbfile kbgraphxlinkcritical
	Last Modified: 13-JUN-2001
	
	3.11
	
	WINDOWS
	
	kbnetwork kbprb kbfile
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Data transfers across a source routing bridge are very slow or appear to hang.
	
	CAUSE
	=====
	
	Windows for Workgroups (NetBEUI protocol) over a Token Ring Source Routing
	Bridge advertises a Largest Frame (LF) size of 8130 bytes. However, the Maxframe
	size is negotiated at 156 bytes. This causes very slow data transfer.
	
	A network trace illustrates the problem:
	
	  Destination   Source        Summary
	  Server      WFWClient<00>   NETB D=2B S=16 Session initialize
	
	  NETB: ----- NETBIOS Session Initialize -----
	  NETB:
	  NETB: Header length = 14, Data length = 0
	  NETB: Delimiter = EFFF (NETBIOS)
	  NETB: Command = 19
	  NETB: Flags = 89
	  NETB: 1... .... = NO.ACK ability
	
	  NETB: .... 100. = Largest frame value = 4 <<<8130 bytes -IBM Spec
	
	  NETB: .... ...1 = Version 2.0 or higher
	
	  NETB: Max data receive size = 156     <<< Small Frame size negotiated.
	
	  NETB: Transmit correlator = 0000
	  NETB: Response correlator = 0016
	  NETB: Remote session number = 43
	  NETB: Local session number = 22
	
	If the bridge advertises a size OTHER THAN 8130 bytes, this problem does not
	occur.
	
	WORKAROUND
	==========
	
	An updated NETBEUI.386 file is available to correct this problem. Replace your
	existing NETBEUI.386 file with the updated version. For information about how to
	obtain the updated driver, refer to the More Information section below.
	
	The following options allow you to work around this problem:
	
	- Use the real-mode NetBEUI protocol.
	
	  -or-
	
	- Execute "Net start Full" at the command prompt before running Windows for
	  Workgroups.
	
	  -or-
	
	- Configure the bridge by changing a Largest Frame size (smaller or larger).
	
	  In a case where an IBM software bridge is used to connect two 16 MB rings, it
	  is not possible to change the LF size on the bridge software. In this case,
	  you can bring down the network ring to 4 MB, or install a hardware bridge.
	
	NOTE: This problem does not occur on LAN Manager/Windows workstations.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  DownloadDownload Netbeui.exe now
	  (http://download.microsoft.com/download/wfw311/Update/1/WFW/EN-US//Netbeui.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	STATUS
	======
	
	Some of the products discussed here are manufactured by vendors independent of
	Microsoft; we make no warranty, implied or otherwise, regarding these products'
	performance or reliability.
	
	Additional query words: 3.11 TR bridging client hangs freezes locks
	
	======================================================================
	Keywords          : kbfile kbgraphxlinkcritical 
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311
	Version           : :3.11
	
	=============================================================================
	

{% endraw %}
