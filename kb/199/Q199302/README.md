---
layout: page
title: "Q199302: XFOR: Understanding F/B Flow Between GroupWise &amp; Exchange Server"
permalink: /kb/199/Q199302/
---

## Q199302: XFOR: Understanding F/B Flow Between GroupWise &amp; Exchange Server

{% raw %}

	Article: Q199302
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	The Calendar Connector (Calcon) supports the exchange of Free/Busy (F/B)
	information between Exchange Server and Novell GroupWise. This article describes
	the underlying mechanism between both systems.
	
	Exchange Server to GroupWise
	----------------------------
	
	1. The Calcon server continually monitors all F/B requests using an internal
	  store-based mechanism. The Calcon server is also responsible for sending and
	  receiving F/B information based on which mail system the F/B query originated
	  at.
	
	2. The GroupWise provider writes a MSG-Type=SEARCH type API file in the Togwise
	  directory. The following is an example of the API file:
	
	  WPC-API= 1.2;
	  MSG-TYPE= Search;
	  Msg-ID= AFJDHGOI:1998.11.26.1.5:1999.1.25.1.5:1998.11.26.1.5.54;
	  From=
	   WPD= Exchange;
	   WPPO= WasteLand;
	   WPU= BEDLAM-SA;
	   CDBA= Exchange.WasteLand.BEDLAM-SA; ;
	  To=
	   WPD= BETA 5;
	   WPPO= Petaling Jaya;
	   WPU= efong;
	   CDBA= BETA 5.Petaling Jaya.efong; ;
	  Begin-Time= 26/11/1998 1:5 +0;
	  End-Time= 25/1/1999 1:5 +0;
	
	3. The Microsoft Exchange Router for Novell GroupWise moves this API file from
	  the Togwise directory to the Api_in directory on the NetWare server.
	
	4. The API gateway then picks up the F/B query, sees that it is a SEARCH type
	  message, and delivers the message to its internal GroupWise mail system for
	  further processing.
	
	GroupWise to Exchange Server (F/B Responses and Queries)
	--------------------------------------------------------
	
	1. The F/B response or query is dropped into the API gateway's Api_out
	  directory.
	
	2. The GroupWise router picks up the message and moves it to the Freebusy
	  directory on the Exchange Server computer. The GroupWise provider then picks
	  this message up.
	
	3. The GroupWise provider translates the F/B message into an Exchange Server
	  format, and hands it off to the Calcon server.
	
	  If this is an F/B response from the GroupWise system, the new information is
	  updated in the F/B public folder. If the F/B response has timed out, the new
	  data will be automatically written to the folder, refreshing the old data
	  accordingly. This way, the next user that queries for this same GroupWise
	  user will have the new F/B information without going through another complete
	  F/B transaction.
	
	  If this is an F/B query, then the Calcon server sends a request to the MAPI
	  provider for the appropriate F/B information for the target recipients.
	
	MORE INFORMATION
	================
	
	For further information on the installation and configuration of the GroupWise
	API gateway, please refer to the Novell Web site at:
	
	  http://www.novell.com (http://www.novell.com)
	
	Note that both the Togwise and Freebusy directories exist under the
	Exchsrvr\Connect\Exchconn\Gwrouter directory.
	
	
	Additional query words: calcon, GroupWise provider
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
