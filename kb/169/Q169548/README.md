---
layout: page
title: "Q169548: Using Proxy Server with Routing and Remote Access"
permalink: /kb/169/Q169548/
---

## Q169548: Using Proxy Server with Routing and Remote Access

{% raw %}

	Article: Q169548
	Product(s): Microsoft Windows NT
	Version(s): 2.0,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Proxy Server version 2.0 
	- Microsoft Routing and Remote Access Service Update for Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Proxy Server is a network application that does not require routing.
	Operationally, this means that every packet that is transmitted to or from the
	proxy server is either sourced or destined with the proxy server's IP address.
	
	For security reasons, the Proxy Server printed documentation recommends turning
	off IP forwarding on the computer on which Proxy Server is installed. However,
	when you install the Routing and Remote Access Update on a server running
	Microsoft Proxy Server, you now have IP forwarding turned on. With IP forwarding
	on, a computer running Windows NT Server is able to forward packets correctly
	from the Internet connection to the internal network. If IP forwarding is
	enabled on a proxy server, all security can be bypassed unless local host
	filters are configured.
	
	MORE INFORMATION
	================
	
	For Microsoft Proxy Server, or any other application service, to work securely
	with Routing and Remote Access Services you must configure input and output
	filters for local host traffic. These filters are configured using the Routing
	and Remote Access Administrator tool.
	
	Before any filters you set up will work, you must enable packet filtering on a
	global level.
	
	To globally enable packet filtering:
	
	1. In the IP Routing folder, right-click Summary, and then click Configure IP
	  parameters.
	
	2. On the General tab, select the Enable packet-filtering check box.
	
	Adding Local Host Filters
	-------------------------
	
	A local host filter enables your computer to receive only traffic destined for
	the computer. A local host filter works by enabling users to access your
	computer, but not to route through your computer. After this filter is set, only
	traffic destined for this host will be allowed in the interface.
	
	In this example, your Proxy server is configured with an Internet IP address of
	192.168.1.1, with a subnet mask of 255.255.255.0. To add local host filters:
	
	1. In the IP Routing folder, click Summary.
	
	2. Right-click the interface over which you want to set the filter, and click
	  Configure Interface. This should be the external (Internet-connected)
	  interface.
	
	3. In the IP Configuration dialog box, click Input Filters.
	
	4. In the "IP Packet Filters Configuration" dialog box, click Add. To allow
	  packets with a destination address of your Proxy server, add a filter with
	  the Destination IP address of 192.168.1.1 and the Destination subnet mask of
	  255.255.255.255. Then select Any as the type of protocol. Click OK, then
	  select the "Drop All Except Listed Below" option under Filter Action, and
	  then click OK.
	
	5. In the IP Configuration dialog box, click Output Filters.
	
	6. In the "IP Packet Filters Configuration" dialog box, click Add. To allow
	  packets leaving directly from your Proxy server, add a filter with the Source
	  IP address of 192.168.1.1 and the Source subnet mask of 255.255.255.255. Then
	  select Any as the type of protocol. Click OK, then select the "Drop All
	  Except Listed Below'" option under Filter Action, and click OK.
	
	You now have configured RRAS to only allow packets leaving directly from your
	Proxy server or packets coming directly to your Proxy server. This will keep
	someone on the Internet from getting into your internal network, and it will
	keep someone on your internal network from going to the Internet without using
	the Proxy Server.
	
	Configuring your Proxy Server/RRAS like this will also allow your server to now
	act as a PPTP server so that PPTP clients on the Internet can access your
	internal LAN.
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q161410 How to Set Up a Private Network Over the Internet Using PPTP
	
	Adding Advanced Filters
	-----------------------
	
	If you would like to make your Proxy Server's Internet connection more secure
	than this, you can remove the Input filter that allows any packets address
	directly to your Proxy server and add individual input filters for each type of
	packet you would like to allow.
	
	For example, you may want your Proxy server to only service WWW requests from
	Proxy clients on the LAN. To do this, you would remove the Input filter you
	added earlier with the Destination IP address of 192.168.1.1. Then you would add
	an Input filter allowing packets with the Destination IP address of 192.168.1.1,
	Protocol TCP, Source port 80, and Destination port 0. You would also have to add
	a second Input filter allowing packets with the Destination IP address of
	192.168.1.1, Protocol UDP, Source port 53, and Destination port 0. This will
	allow the Proxy Server to resolve Internet names using DNS.
	
	If you want Proxy clients to be able to use additional Proxy services, you would
	have to add Input filters allowing the correct protocol and port number that
	each service uses. If you want PPTP clients to be able to connect to your
	internal LAN, then you would need to add PPTP filters.
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q169890 Enable PPTP Filtering Option No Longer Works
	
	Additional query words: rras
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbAudDeveloper kbProxyServSearch kbProxyServ200 kbRRASNTSearch kbRRASNT400
	Version           : :2.0,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
