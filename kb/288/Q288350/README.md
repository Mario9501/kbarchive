---
layout: page
title: "Q288350: FTP Failed Login and Bye Command Cause Dr. Watson in Inetinfo"
permalink: /kb/288/Q288350/
---

## Q288350: FTP Failed Login and Bye Command Cause Dr. Watson in Inetinfo

{% raw %}

	Article: Q288350
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbiis500prod2web kbProd2Web
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to log on to the Internet Information Server (IIS) FTP Service
	by using the DOS FTP client, the system returns a "Home Directory inaccessible"
	message. When you return to the FTP prompt, and use the Bye command to exit the
	FTP client, a Dr. Watson occurs in the Inetinfo.exe service.
	
	NOTE: The credentials that are passed work correctly when you attempt to log on
	to other resources, such as domain logins or network shares.
	
	CAUSE
	=====
	
	For the IIS Services (WWW, FTP, NNTP, and SMTP) to function properly, it is
	imperative that the corresponding DLL files for the service are the same
	version. For example, if a computer is running Windows NT Server with Service
	Pack 5 (SP5), then the version for W3svc.dll, Infocomm.dll, Ftpsvc2.dll must all
	have the same modified dates. If they do not have the same modified dates, the
	out of date DLLs in Inetinfo.exe will cause an Access Violation to occur. If the
	service that you are attempting to use is not running the proper version, the
	Inetinfo service will return a Dr. Watson (C0000005) error.
	
	RESOLUTION
	==========
	
	To resolve this problem, apply the latest service pack to the server (currently
	SP6a).
	
	NOTE: IIS 4.0, which is included in the Windows NT Option Pack (NTOP), was
	released before SP4. To successfully update problems in products that were
	included in the NTOP, Microsoft has bundled all fixes in subsequent service
	packs. Therefore, to ensure that all services are running the latest version,
	you must run the latest Windows NT service pack.
	
	Additional query words: IIS 5
	
	======================================================================
	Keywords          : kbiis500prod2web kbProd2Web 
	Technology        : kbiisSearch kbiis400
	Version           : :4.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
