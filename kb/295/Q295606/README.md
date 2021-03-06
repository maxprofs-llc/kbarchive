---
layout: page
title: "Q295606: FP: How to Insert Script Code in a Shared Border of a Web"
permalink: /kb/295/Q295606/
---

## Q295606: FP: How to Insert Script Code in a Shared Border of a Web

{% raw %}

	Article: Q295606
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 2002 
	- Microsoft FrontPage 2000 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to insert script code into a shared border of a Web.
	
	MORE INFORMATION
	================
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: You may receive an error message if you copy and paste the examples
	directly from this article to FrontPage. The angle brackets ("<" and ">")
	may appear as escaped HTML code ("&lt;" and "&gt;"). To work around this
	behavior, paste the script in a blank Notepad document, and then copy it from
	Notepad before you paste it into FrontPage.
	
	To add script code to a shared border, follow these steps:
	
	1. Start FrontPage and open the Web site. To do this, click Open Web on the File
	  menu, select the Web you want to open, and click Open.
	
	2. On the Tools menu, click Web Settings.
	
	3. Click the Advanced Settings tab. Click to select the "Show hidden files and
	  folders" check box and click Apply.
	
	  NOTE: Shared borders are kept in a hidden folder named _borders.
	
	4. If you receive the following message
	
	  The changes you made in the Advanced Settings tab will take effect after the
	  Web is refreshed from the server.
	
	  Do you want to refresh the Web now?
	
	  click Yes.
	
	5. Click OK to close the Web Settings dialog box.
	
	6. Double-click the _borders folder.
	
	  NOTE: You should see one or more of the following shared border pages:
	
	   - Top.htm (Top Shared Border)
	   - Left.htm (Left Shared Border)
	   - Right.htm (Right Shared Border)
	   - Bottom.htm (Bottom Shared Border)
	
	  When you edit these files the information that appears in the borders is
	  updated.
	
	7. Right-click the file you want to modify and click Open on the menu that
	  appears. For example, open the Top.htm page.
	
	8. When the page opens in FrontPage, switch to HTML view.
	
	9. Locate the opening <BODY> tag in the HTML code and click just after the
	  tag. Press ENTER twice to create new lines.
	
	  WARNING: Information you type between the <BODY> and </BODY> tags
	  in a shared border file appears in the border. Any code that you type in the
	  <HEAD></HEAD> section is ignored. Therefore, to have the script
	  be processed, place it in the document body section.
	
	10. On the new line, type the script code you want. For example, type the
	  following script code:
	
	  <script language="JavaScript">
	  <!--
	      alert('This is in the TOP border.');
	  -->
	  </script>
	
	11. On the File menu, click Save to save the changes you made to the page.
	
	12. On the File menu, click Close.
	
	When you view your Web site in a Web browser, a message box similar to the
	following appears for each page that has the shared border:
	
	  This is in the TOP border.
	
	REFERENCES
	==========
	
	For additional information about using FrontPage and shared borders, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q290767 FP2000: How to View Shared Borders Pages in a FrontPage Web
	
	Additional query words: front page
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch kbFrontPage2002 kbFrontPage2000Search kbFrontPage2002Search kbZNotKeyword5
	Version           : :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
