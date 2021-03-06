---
layout: page
title: "Q313225: HOWTO: Connect to a SQL Server 2000 Named Instance with JDBC"
permalink: /kb/313/Q313225/
---

## Q313225: HOWTO: Connect to a SQL Server 2000 Named Instance with JDBC

{% raw %}

	Article: Q313225
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 
	Operating System(s): 
	Keyword(s): kbJDBC kbDSupport kbSQLServ2000 kbSQLServSearch kbAudDeveloper kbHOWTOmaster kbSystemDa
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SQL Server 2000 Driver for JDBC 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft SQL Server 2000 supports multiple instances of the SQL Server database
	engine that run concurrently on the same computer. The following are the two
	types of SQL Server database engine instances: default and named. There can only
	be one default instance that runs on any computer, and it is identified by the
	name of the computer on which the default instance runs. The computer name and
	instance name are typically specified in the following format:
	
	computer_name\instance_name
	
	To connect to a named instance through the Microsoft SQL Server 2000 Driver for
	JDBC, you must specify the port number that is associated with the named
	instance, instead of the name of the named instance as shown earlier.
	
	MORE INFORMATION
	================
	
	To find the SQL Server instance port number, follow these steps:
	
	1. On the Microsoft SQL Server 2000 server, start the SQL Server Network
	  Utility.
	
	2. Click the General tab, and then click the instance you want from the
	  Instances drop-down menu.
	
	3. Click TCP/IP, and then click Properties. Note that the port number for this
	  instance appears in the Properties dialog box.
	
	As soon as you have this value, you can use it in your connection URL when you
	connect to SQL Server through JDBC. The following is an example of a typical
	connection URL:
	
	  jdbc:microsoft:sqlserver://<yourServerName>:1433;user=<yourUser>;password=<yourPwd>
	
	In this example, the default port of 1433 is used. Replace this default with the
	port number for your named instance.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbJDBC kbDSupport kbSQLServ2000 kbSQLServSearch kbAudDeveloper kbHOWTOmaster kbSystemData 
	Technology        : kbAudDeveloper kbSQLServ2000Search kbSQLServJDBC
	Version           : :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
