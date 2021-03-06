---
layout: page
title: "Q192983: XCON: Content Conversion Errors on OLE Embedded Objects"
permalink: /kb/192/Q192983/
---

## Q192983: XCON: Content Conversion Errors on OLE Embedded Objects

{% raw %}

	Article: Q192983
	Product(s): Microsoft Exchange
	Version(s): WinNT:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you send a message containing an embedded object, for example, a bitmap
	image, you may receive the following non-delivery report (NDR):
	
	  Your message did not reach some or all of the intended recipients.
	
	     Subject: embedded object 2
	     Sent: 04/02/98 13:07
	
	  The following recipient(s) could not be reached:
	
	     <recipient name> (X400) on 04/02/98 13:06
	        The message contains a content type that is not supported
	        MSEXCH:MSExchangeMTA:SITEA:EXCHSRV
	
	Additionally, a content conversion error (Event ID 210) is logged on the
	destination server.
	
	This issue only occurs in the following circumstances:
	
	- You are sending from an Exchange Server 5.5 server to an Exchange Server 4.0
	  server.
	
	- The two servers are connected via an X.400 Connector.
	
	- The sites do not have directory replication configured between them.
	
	- The embedded object has been placed in the message by clicking the Insert
	  menu and clicking Object in the Outlook or Exchange client.
	
	CAUSE
	=====
	
	The Exchange 4.0 message transfer agent (MTA) was not handling OLE objects
	correctly and therefore could not convert this message.
	
	
	RESOLUTION
	==========
	
	Exchange Server 4.0
	-------------------
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression-tested and should be applied only to systems
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: MTA
	
	  File Name      Version
	  ------------------------
	  Address.dll    4.0.997.0
	  Dbserver.sch   4.0.997.0
	  Dcprods.cat    4.0.997.0
	  Ems_rid.dll    4.0.997.0
	  Emsmta.exe     4.0.997.0
	  Infodlog.cfg   4.0.997.0
	  Infotlog.cfg   4.0.997.0
	  Mmiext.dll     4.0.997.0
	  Mtacheck.exe   4.0.997.0
	  Mtalog.dll     4.0.997.0
	  P2.xv2         4.0.997.0
	  P3.tpl         4.0.997.0
	  Saalog.dll     4.0.997.0
	  X400omv1.dll   4.0.997.0
	
	
	Exchange Server 5.0
	-------------------
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression-tested and should be applied only to systems
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next Microsoft
	Exchange Server version 5.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: MTA
	
	  File Name      Version
	  --------------------------
	  Address.dll    5.0.1461.45
	  Dbserver.sch   5.0.1461.45
	  Dcprods.cat    5.0.1461.45
	  Ems_rid.dll    5.0.1461.45
	  Emsmta.exe     5.0.1461.45
	  Infotlog.cfg   5.0.1461.45
	  Infoxlog.cfg   5.0.1461.45
	  Mmiext.dll     5.0.1461.45
	  Mtacheck.exe   5.0.1461.45
	  Mtamsg.dll     5.0.1461.45
	  P2.xv2         5.0.1461.45
	  P3.tpl         5.0.1461.45
	  P772.tpl       5.0.1461.45
	  X400om.dll     5.0.1461.45
	  X400omv1.dll   5.0.1461.45
	
	
	Exchange Server 5.5
	-------------------
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: MTA
	
	  File Name      Version
	  -------------------------
	  Dbserver.sch   5.5.2329.0
	  Dcprods.cat    5.5.2329.0
	  Ems_rid.dll    5.5.2329.0
	  Emsmta.exe     5.5.2329.0
	  Info4log.cfg   5.5.2329.0
	  Infodlog.cfg   5.5.2329.0
	  Infollog.cfg   5.5.2329.0
	  Infotlog.cfg   5.5.2329.0
	  Mtacheck.exe   5.5.2329.0
	  Mtamsg.dll     5.5.2329.0
	  P2.xv2         5.5.2329.0
	  X400om.dll     5.5.2329.0
	  X400omv1.dll   5.5.2329.0
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	versions 4.0, 5.0, and 5.5. This problem was first corrected in Exchange Server
	5.5 Service Pack 2.
	
	
	======================================================================
	Keywords          : exc55sp2fix 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : WinNT:4.0,5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
