---
layout: page
title: "Q278498: HOWTO: Configure NNTP Service to Use Secure Sockets Layer"
permalink: /kb/278/Q278498/
---

## Q278498: HOWTO: Configure NNTP Service to Use Secure Sockets Layer

{% raw %}

	Article: Q278498
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbDSupport kbiis400
	Last Modified: 23-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to configure the Microsoft Windows NT Option
	Pack-based Network News Transport Protocol (NNTP) service to use Secure Sockets
	Layer (SSL) with the help of a Server Certificate.
	
	MORE INFORMATION
	================
	
	How to Configure NNTP Service to Use SSL
	----------------------------------------
	
	Steps to Install a Certificate for the NNTP Service:
	
	To use SSL with NNTP, you must first install a certificate for the NNTP service
	on the Internet Information Server (IIS) server. To do this, follow these
	steps:
	
	1. Generate a Key Request file that contains the Private and Public key
	  information that is necessary to encrypt the data. To do this, follow these
	  steps:
	
	  a. Open Key Manager either from Internet Service Manager or at the command
	     prompt (%Windir%\System32\Inetsrv\Keyring.exe).
	
	  b. In the list of protocols under Local Computer, click NNTP.
	
	  c. Right-click NNTP, and then click Create New Key.
	
	  d. In the Create New Key Wizard, if you have your own Certification Authority
	     (CA), click "Automatically send the request directly to an online
	     authority". You can also generate the request and store the request in a
	     text file before you send it to a Certification Authority.
	
	  e. On the next page of the wizard, name the key with a name that you can
	     remember why it was generated. Type a password that links the public and
	     private keys of your certificate. Remember this password. Select the bit
	     length (1024 = 128 bit, 768 = 56 bit, and 512 = 40 bit) to specify how
	     strong you want the key to be.
	
	  f. On the next page, type the organizational details. Make sure that you do
	     not use any commas, apostrophes and other similar characters. In the
	     Common Name box, use the Fully Qualified Domain Name (FQDN) of the site
	     for which this certificate is being generated.
	
	  g. On the next page, type the Country, State and City information, following
	     the instructions, and type the contact information.
	
	  h. Click Finish to complete the steps in the wizard. Notice that a key
	     appears under the NNTP protocol with a red slash across it. The request is
	     saved in a text file at the location that you specified in the first step
	     of the wizard (which is C:\NewKeyRq.txt by default).
	
	2. Use the request file that is generated to obtain a signed certificate from a
	  Certification Authority. The certificate is in a .cer file.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q171084 How to Install a Certificate
	
	3. Install the signed certificate as follows:
	
	  a. Right-click the key that you created in the Key Manager, and then click
	     Install Key Certificate.
	
	  b. When you are prompted to open a file, click the .cer file that you
	     obtained from the Certification Authority.
	
	  c. When you are prompted for a password, type the password that you typed
	     when you generated the request file.
	
	  d. In the Server Bindings dialog box, click Add. Under IP Address and Port
	     Number, click Any Unassigned, and then click OK.
	
	  e. Close the Key Manager to commit all changes.
	
	The certificate is now bound to the NNTP service.
	
	Steps to Configure the NNTP Service to Use SSL:
	
	1. Open the Internet Service Manager (MMC).
	
	2. Right-click the NNTP site, and then click Properties.
	
	3. On the Home Directory tab, under Secure Communications, click Edit.
	
	4. Select the "Require Secure Channel" check box.
	
	5. Click OK twice to apply the change.
	
	6. At a command prompt, type the following command to stop the IISADMIN service:
	
	  "net stop IISADMIN" (without the quotation marks)
	
	7. Start the NNTP Service and any other services that IISADMIN stopped in the
	  previous step (such as W3SVC, MSFTPSVC, or SMTPSVC).
	
	The NNTP server is now configured to accept SSL connections.
	
	Set Up Outlook Express 5.x to Connect to an SSL-Enabled NNTP Server
	-------------------------------------------------------------------
	
	The following steps are based on Microsoft Outlook Express 5.x. Although other
	NNTP clients can be configured to access NNTP over SSL, the steps may vary.
	
	1. Open Microsoft Outlook Express.
	
	2. On the Tools menu, click Accounts.
	
	3. Click Add, and then click Select News.
	
	4. Under Display Name, type a name for the NNTP server, and then click Next.
	
	5. Type your e-mail address, and then click Next.
	
	6. Type the IP Address or Fully Qualified Domain Name of the NNTP server. If you
	  are on a local area network (LAN), you can use the NetBIOS name of the NNTP
	  server. Click Next.
	
	7. If the server allows anonymous access, do not select the "The server requires
	  me to logon" check box.
	
	8. Click Finish. You see that an account is created for that NNTP server.
	
	9. Click the News account that you created in the previous step, and then click
	  Properties.
	
	10. On the Advanced tab, select the "This server requires a Secure Connection
	  (SSL)" check box.
	
	11. Click Apply, and then click Close.
	
	12. When you are given the option to download the available newsgroups from that
	  NNTP server, click OK, and you can select the newsgroups to which you want
	  to subscribe.
	
	REFERENCES
	----------
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q218445 How to Configure Certificate Server for Use with SSL on IIS
	
	Additional query words: iis 4 secure internet news
	
	======================================================================
	Keywords          : kbDSupport kbiis400 
	Technology        : kbiisSearch kbiis400
	Version           : :4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
