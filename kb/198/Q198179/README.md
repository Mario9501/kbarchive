---
layout: page
title: "Q198179: Enabling an APPC/CPIC Program to Use Persistent Verification"
permalink: /kb/198/Q198179/
---

## Q198179: Enabling an APPC/CPIC Program to Use Persistent Verification

{% raw %}

	Article: Q198179
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0 SP3,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0 SP3, 4.0, 4.0 SP1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft SNA Server 3.0 Service Pack 3 and later versions include support for
	LU6.2 "persistent verification" as described in the following Knowledge Base
	article:
	
	  Q180866 Persistent Verification Support for APPC Sessions
	
	In order for an application to make use of SNA Server persistent verification
	support, the application must do the following:
	
	- An APPC application must set security = AP_SAME, and set the user_id and pwd
	  fields on every call to the [MC_]ALLOCATE verb.
	
	- A CPIC application must set conversation_security_type = XC_SECURITY_SAME,
	  and set security_user_id and security_password fields prior to every call to
	  the CMALLC (Allocate) function.
	
	MORE INFORMATION
	================
	
	Persistent verification (PV) eliminates the need to provide a user ID and
	password on each Attach during multiple conversations between a user and its
	partner at a remote LU. The user is verified once during a sign-on process
	during its initial conversation over an LU6.2 session between an LU/LU pair, and
	remains verified until the user is signed off by the remote LU, or if all
	sessions between the LUs are ended.
	
	In order for persistent verification to be used, the host system must indicate
	support within its BIND command or response, by setting the following option:
	
	  Byte 23, Bit 7 persistent verification capability must be set to 1 (ON):
	  (Persistent Verification indicator is supported on incoming FMH-5s)
	
	Note that SNA Server does not set this bit, because SNA Server only supports the
	sending of FMH-5 Attach requests with persistent verification. SNA Server does
	not support incoming FMH-5 Attaches which have persistent verification set.
	
	If SNA Server detects that the remote system supports persistent verification (as
	indicated in the host BIND message), then the APPC or CPIC application can take
	advantage of persistent verification by setting security = SAME, and by
	providing a user ID AND password on every allocate request. SNA Server then
	implements PV by maintaining a PV sign-on user list associated with each Remote
	APPC LU as follows:
	
	- If a client allocate request is received and the user is not in the PV user
	  sign-on list, SNA Server adds the user to its sign-on user list, sets Byte 4
	  Bit 1-2 (persistent verification indicator) to "01", indicating "sign-on
	  requested", and includes the user ID and password security vectors in the
	  FMH-5 Attach.
	
	- If a client allocate request is received and the user is found in the sign-on
	  list, SNA Server sets Byte 4 Bit 1-2 (persistent verification indicator) to
	  "10" indicating "already signed on", and includes the user ID only in the
	  FMH-5 Attach, but does not include the password vector.
	
	As mentioned above, SNA Server removes a user from its PV sign-on list when one
	of the following conditions occurs:
	
	- If the remote system sends a PV Sign-Off request to SNA Server and indicates
	  the user. The remote system initiates an LU6.2 conversation to the SNA Server
	  Sign-Off TP (TP name = X'06F3F0F0'), and indicating the user name in the
	  Sign-Off GDS X'1220' message.
	
	- If all sessions end between the SNA Server LU and remote LU. This can occur
	  if the connection fails or if all sessions are unbound.
	
	There is no way to view the SNA Server PV sign-on list, although this is under
	consideration for a future release of SNA Server.
	
	
	REFERENCES
	==========
	
	IBM documents the format of the SNA BIND command and FMH-5 Attach requests in
	the following IBM reference:
	
	  Title: Systems Network Architecture Formats
	  IBM Document Number GA27-3136-14
	
	For more information about persistent verification, please see the following IBM
	reference:
	
	  Title: SNA LU 6.2 Peer Protocols
	  IBM Document Number: SC31-6808-02
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400 kbSNAServ300SP3 kbSNAServ400SP1
	Version           : WINDOWS:3.0 SP3,4.0,4.0 SP1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
