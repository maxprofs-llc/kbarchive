---
layout: page
title: "Q110478: Auto-Start .AVI on Viewer Start Up"
permalink: /kb/110/Q110478/
---

## Q110478: Auto-Start .AVI on Viewer Start Up

{% raw %}

	Article: Q110478
	Product(s): Miscellaneous Software Development Kits
	Version(s): 2.0,2.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Multimedia Viewer Publishing Toolkit, versions 2.0, 2.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains information on how to make Viewer play an .AVI file when
	your user first starts up your Viewer title. The step-by-step instructions in
	Method 1 will help you put an auto-starting video into your title using the
	Multimedia ewX command. The instructions in Method 2 will give you more control
	over the video by using mciSendString() commands. Method 2 also tells you how to
	execute a command, such as JumpID(), immediately after the .AVI file finishes
	playing.
	
	MORE INFORMATION
	================
	
	First, decide how you want your startup screen to look. Do you want the Viewer
	window to be a certain size and position on your users screen (see Optional
	Window Design later in this article)? Do you want just an .AVI file or do you
	want text and bitmaps too?
	
	If you want your user to have control of pausing, playing, or stopping the .AVI
	file choose Method 1. If you want your user to have less control over when the
	.AVI starts or stops choose Method 2.
	
	Decide how you want your user to get out of the startup screen and on to other
	topics in your title. Method 2 explains the following:
	
	- How to enable the user to use the Search, Index, and Contents buttons from
	  the startup screen.
	
	- How to remove all of the default buttons (temporarily) and make your own
	  button(s).
	
	- How to use a text or bitmap hotspot on the screen to jump to another topic
	  when the user clicks it.
	
	- How to make Viewer automatically jump to a specific topic as soon as the .AVI
	  file finishes playing.
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q110384 Direct Control of .AVI Files From Viewer
	
	Method 1
	--------
	
	How to Play an Auto-start .AVI file on Viewer Startup
	
	1. In your .RTF file, create your startup screen topic. Add your context string
	  footnote and any topic entry commands that you want from the "Optional Window
	  Design" section of this article. Insert a Multimedia ewX command where you
	  want your .AVI file to appear. See page 10-9 of the Authoring Guide for
	  step-by-step instructions on inserting an embedded MCI sequence into a topic.
	
	2. On page 10-9 of the Authoring Guide, step 6 says to "Type the properties you
	  want for the multimedia controller." You should select Auto-Start.
	
	3. In Project Editor, select [OPTIONS] from the Section menu. In the Contents
	  Topic field, type in the context string of your .AVI topic. The first topic
	  you see when you start Viewer is the topic specified in the Contents Topic in
	  the [OPTIONS] Title Options section of the Project File. If no topic is
	  specified in the Contents Topic field, then the default action of Viewer is
	  to display the first page of the first .RTF file listed in the Project File.
	
	4. You should have already decided how you want your user to get from the .AVI
	  topic to the table of contents. If you want to manipulate the buttons or
	  menus, see pages 5-16 to 5-18 of the Viewer Technical Reference. If you want
	  to use the Contents button, see step 5 in these instructions. If you want to
	  make a bitmap hotspot that runs JumpID(), see pages 9-8 to 9-16 of the Viewer
	  Authoring Guide. For other ideas on how to get from the startup screen to
	  other topics in the title, see chapter 6, Linking Topics, in the Viewer
	  Authoring Guide.
	
	5. The default Contents button will jump to the topic specified in the [OPTIONS]
	  section. To change the Contents button so that it jumps to your "real" table
	  of contents, use the ChangeButtonBinding() function. Place the
	  ChangeButtonBinding() function in the [CONFIG] section of your Project file.
	  The ChangeButtonBinding() function needs to be after the Std20Buttons()
	  function in the [CONFIG] section. Here is an example of a
	  ChangeButtonBinding() function:
	
	     ChangeButtonBinding(`btn_contents', `JumpID(`autoavi.mvb',
	     `table_of_contents')')
	
	  NOTE: The Contents() command will jump to the topic specified in the CONTENTS
	  option in the [OPTIONS] section or it will jump to the default contents
	  topic. In this case, the Contents() command will jump to the .AVI topic.
	
	Method 2
	--------
	
	How to Automatically Execute JumpID When the .AVI File Finishes Playing
	
	In this method, you will NOT use a Multimedia ewX command. Instead, you will
	manually insert three commands to open, play, and close your .AVI file. You can
	then insert commands that will execute only after your .AVI file is closed. In
	this example, a JumpID() is executed to jump to the table of contents. For this
	example, all of these commands are placed in a topic entry command.
	
	NOTE: Page 5-1 of the Authoring Guide states that "In a Viewer title, commands
	can be run at any of the following times:
	
	  When Viewer first loads a title
	  When a topic group is entered or exited
	  When a topic is displayed
	  When a hot spot is selected"
	
	1. In your .RTF file, create your startup screen topic. Add your context string
	  footnote and any topic entry commands that you want from the "Optional Window
	  Design" section of this article. Next, insert a topic entry command at the
	  beginning of the topic. The order of the footnotes does not matter; the topic
	  entry command can be before or after any of the other footnotes. Type the
	  following four commands in the "Topic Entry commands: (one per line)" section
	  of the Topic Editor dialog box:
	
	     mciSendString("open coyote.avi",0,0,0)
	     mciSendString("play coyote.avi wait",0,0,0)
	     mciSendString("close coyote.avi",0,0,0)
	     JumpID(`title.mvb>main', `table_of_contents')
	
	  Where table_of_contents is the context string for the true contents topic,
	  title.mvb is the title of your project, and replace coyote.avi with the name
	  of the .AVI file you want to play. Whatever .AVI file you use, the .AVI file
	  will need to be either in the same directory as the .MVP file, or in a
	  directory specified by the ROOT option (see page 2-10 of the Viewer Authoring
	  Guide).
	
	  NOTE: You can also enter this topic entry command without using the Topic
	  Editor. Choose Footnote from the Insert menu of Microsoft Word for Windows.
	  In the View Footnotes window, the footnote text should look as follows:
	
	        ! mciSendString("open coyote.avi",0,0,0); mciSendString("play
	        coyote.avi wait",0,0,0); mciSendString("close coyote.avi",0,0,0);
	        JumpID(`title.mvb>main', `table_of_contents')
	
	2. Add the following line to your [CONFIG] section so that Viewer knows where to
	  find the mciSendString procedure:
	
	  RegisterRoutine("mmsystem","mciSendString","SUuu")
	
	  MMSYSTEM.DLL will need to be on any machine that your title will play on. The
	  file MMSYSTEM.DLL comes with Windows 3.1, and can be found in the
	  \WINDOWS\SYSTEM directory. You do not need to ship this DLL with your
	  product.
	
	3. In Project Editor, select [OPTIONS] from the Section menu. In the Contents
	  Topic field, type in the context string of your .AVI topic. The first topic
	  you see when you start Viewer is the topic specified in the Contents Topic in
	  the [OPTIONS] Title Options section of the Project File. If no topic is
	  specified in the Contents Topic field, then the default action of Viewer is
	  to display the first page of the first .RTF file listed in the Project File.
	
	4. The default Contents button will jump to the topic specified in the [OPTIONS]
	  section. To change the Contents button so that it jumps to your "real" table
	  of contents, use the ChangeButtonBinding() function. Place the
	  ChangeButtonBinding() function in the [CONFIG] section of your Project file.
	  The ChangeButtonBinding() function needs to be after the Std20Buttons()
	  function in the [CONFIG] section. The following is an example of a
	  ChangeButtonBinding() function:
	
	     ChangeButtonBinding(`btn_contents', `JumpID(`autoavi.mvb',
	     `table_of_contents')').
	
	  NOTE: The Contents() command will jump to the topic specified in the CONTENTS
	  option in the [OPTIONS] section or it will jump to the default contents
	  topic. In this case, the Contents() command will jump to the .AVI topic.
	
	Optional Window Design
	----------------------
	
	To temporarily change the look of your Viewer title, execute some of the
	following commands as topic entry commands:
	
	- Use PositionWindow() to set the size and position of a window.
	
	- Use PositionMaster() to set the size and position of the master pane.
	
	- Use HideMenuBar() and ShowMenuBar().
	
	- Use HideButtonBar() and ShowButtonBar().
	
	- Use CreateButton() and DestroyButton().
	
	For more information on hiding the caption bar, hiding maximize button, hiding
	the minimize button, and/or hiding the system menu button, please see the
	following article(s) in the Microsoft Knowledge Base:
	
	  Q111011 Changing the Style of the Main Window
	
	Additional query words: 2.00 2.00a
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch kbHomeMMsearch kbMMViewer200 kbMMViewer200a
	Version           : :2.0,2.0a
	
	=============================================================================
	

{% endraw %}
