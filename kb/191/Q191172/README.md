---
layout: page
title: "Q191172: FIX: Performance Degradation with Repeated SQL SELECTs"
permalink: /kb/191/Q191172/
---

## Q191172: FIX: Performance Degradation with Repeated SQL SELECTs

{% raw %}

	Article: Q191172
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbDatabase kbSQL kbvfp500 kbvfp500aBUG kbvfp500bug kbvfp600 kbvfp600bug kbVS600sp3fix k
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	There is a slow degradation of Visual FoxPro's performance with repeated
	execution of SQL SELECT statements. The results returned by SYS(1016) and the
	time required to process SQL Select statements gradually increase with repeated
	execution of SQL Select statements.
	
	CAUSE
	=====
	
	This is caused by repeated execution of an SQL SELECT statement containing WHERE
	and OR clauses, as in the following example:
	
	  SELECT * ;
	    FROM <TABLE NAME> ;
	    WHERE .T. ;
	    OR .T. ;
	    INTO CURSOR TEST
	
	RESOLUTION
	==========
	
	Here are three ways to workaround this problem:
	
	- Use the HAVING clause in the SQL Select statement rather than the WHERE
	  clause. For example:
	
	  SELECT DISTINCT * ;
	    FROM <table name> ;
	    HAVING <condition 1> ;
	    OR <condition 2> ;
	    OR <condition 3> ;
	    ORDER BY <order> ;
	    INTO CURSOR <destination>
	
	- Use the INLIST() function in the SQL Select statement, in place of the OR.
	  For example:
	
	  SELECT DISTINCT * ;
	    FROM <table name> ;
	    WHERE INLIST(eExpression,<condition 1>, ;
	    <condition 2>, ;
	    <condition 3>, ;
	    ORDER BY <order> ;
	    INTO CURSOR <destination>;
	
	- Use a UNION for each OR condition. For example:
	
	  SELECT DISTINCT * ;
	    FROM <table name> ;
	    WHERE <condition 1> ;
	    UNION SELECT DISTINCT * ;
	    FROM <table name> ;
	    WHERE <condition 2> ;
	    UNION SELECT DISTINCT * ;
	    FROM <table name> ;
	    WHERE <condition 3> ;
	    INTO CURSOR <destination>
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3.
	
	For more information about Visual Studio service packs, please see the following
	articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	The amount by which the result returned by SYS(1016) increases is dependent on
	the version of Visual FoxPro and the number of ORs contained in the SQL Select
	statement. With Visual FoxPro 5.0, the amount of increase in the result returned
	by SYS(1016) is 16 times the number of ORs contained in the SQL Select
	statement. In Visual FoxPro 6.0, the amount of increase in the result returned
	by SYS(1016) is 24 times the number of ORs contained in the SQL Select
	statement. This behavior does not occur with Visual FoxPro 3.0.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a program named Test.prg using the following code:
	
	  CLOSE ALL
	  CLEAR ALL
	  OPEN DATABASE "c:\program files\devstudio\vfp\samples\data\testdata"
	  startval=VAL(SYS(1016))
	  FOR i=1 TO 10
	    SELECT * FROM customer WHERE .T. OR .T. INTO CURSOR test
	    endval=VAL(SYS(1016))
	    ? ALLTRIM(STR(endval)) +  ;
	      " - " + ALLTRIM(STR(startval)) + ;
	      " = " + ALLTRIM(STR(endval-startval))
	    startval=endval
	  NEXT
	
	2. From the Command prompt, type the following:
	
	  DO TEST
	
	3. Observe that the startval and endval increase and that the difference between
	  endval and startval is 16 in Visual FoxPro 5.0 and 24 in Visual FoxPro 6.0.
	
	(c) Microsoft Corporation 1999, All Rights Reserved.
	Contributions by John Desch, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDatabase kbSQL kbvfp500 kbvfp500aBUG kbvfp500bug kbvfp600 kbvfp600bug kbVS600sp3fix kbGrpDSFox kbSQLProg 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
