---
layout: page
title: "Q185295: INFO: Results of Function Timing from Microsoft Source Profiler"
permalink: /kb/185/Q185295/
---

## Q185295: INFO: Results of Function Timing from Microsoft Source Profiler

{% raw %}

	Article: Q185295
	Product(s): Microsoft Programming Utilities
	Version(s): winnt:2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC420 kbVC500 kbVC600
	Last Modified: 29-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Source Profiler, included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 2.2, 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the output generated from the Microsoft Source Profiler
	and specifically focuses on the use of function timing. The sample output comes
	from a default MFC AppWizard-based application called ProfTest. Although it is
	not a complete listing of the output from this profile, it is sufficient to
	demonstrate the output results. A description of each entry presented in the
	"Sample Output" section follows in the "Output Description" section of this
	article.
	
	MORE INFORMATION
	================
	
	Sample Output
	-------------
	
	  Profile: Function timing, sorted by time
	  Date:    Wed Nov 05 23:37:00 1997
	
	Program Statistics
	------------------
	
	     Command line at 1997 Nov 05 23:35: "C:\code\ProfTest\Debug\ProfTest"
	     Total time: 88816.409 millisecond
	     Time outside of functions: 86.090 millisecond
	     Call depth: 21
	     Total functions: 317
	     Total hits: 23933
	     Function coverage: 58.0%
	     Overhead calculated 8
	     Overhead average 8
	
	Module Statistics for proftest.exe
	----------------------------------
	
	     Time in module: 88730.319 millisecond
	     Percent of time in module: 100.0%
	     Functions in module: 317
	     Hits in module: 23933
	     Module function coverage: 58.0%
	
	     Func             Func+Child      Hit
	     Time       %     Time       %    Count  Function
	     ---------------------------------------------------------
	
	     86571.608  97.6  87316.863  98.4   70   CWinThread::PumpMessage(void)
	                                             (mfc42d.dll)
	       246.177   0.3    367.692   0.4  184   CMDIFrameWnd::DefWindowProcA
	                                             (unsigned int,unsigned
	                                             int,long) (mfc42d.dll)
	       188.947   0.2    188.947   0.2  751   CView::AssertValid(void)
	                                             (mfc42d.dll)
	       171.866   0.2    172.011   0.2    1   CToolBar::Create(class CWnd
	                                             *,unsigned long,unsigned int)
	                                             (mfc42d.dll)
	       144.324   0.2    940.322   1.1  517   CWnd::OnWndMsg(unsigned
	                                             int,unsigned int,long,long *)
	                                             (mfc42d.dll)
	        94.550   0.1    314.706   0.4   69   CWinThread::
	                                             PreTranslateMessage(struct
	                                             tagMSG *) (mfc42d.dll)
	        50.008   0.1  88727.904 100.0    1   AfxWinMain(struct HINSTANCE__
	                                             *,struct HINSTANCE__ *,char
	                                             *,int) (mfc42d.dll)
	
	Output Description
	------------------
	
	Program Statistics:
	
	Command line -
	
	  Time and date the application ran, and the complete command line issued by
	  the profiler.
	
	Total time -
	
	  Total application execution time. The time listed in milliseconds might not
	  be completely accurate. Use the times as a relative measure.
	
	Time outside of functions -
	
	  Time spent outside of any profiled functions. If a top level profiled
	  function is called, no time is added to this value until that function
	  returns.
	
	Call depth -
	
	  The deepest level of functions called. For example, if function A calls
	  function B which calls function C, the call depth is 3.
	
	Total functions -
	
	  The number of functions listed in the output.
	
	Total hits -
	
	  How many times the functions listed were executed.
	
	Function coverage -
	
	  The percentage of time spent in the listed functions.
	
	Overhead calculated -
	
	  A relative value that represents profiler overhead. This is not a measure of
	  time, but a larger value indicates more time spent in overhead.
	
	Overhead average -
	
	  The average overhead required for all profiles. This should be the same as
	  the overhead calculated, unless you are merging multiple profiles.
	
	Module Statistics:
	
	These statistics are similar to the Program Statistics. They are useful when
	profiling multiple modules, such as an executable and dynamic link library.
	
	Function Time:
	
	In the Function Timing section of the Visual C++ online documentation, there is
	one error. The function time is in milliseconds, not seconds as it is stated in
	the documentation. The following excerpt is reprinted from the documentation
	with the correct measure for function time (milliseconds):
	
	  The Func Time column reports how much time it took for the function to run in
	  milliseconds. The next column shows what percent of the total profile time is
	  represented by the function time. Func+Child Time refers to the total time
	  profiled for the function as well as any functions called by that function.
	  The next column shows what percent of the total profile time is represented
	  by the Func+Child time. The Hit Count column reports the number of times that
	  the function was called. The Function column displays the decorated name of
	  the function.
	
	If a called function contains profiler information, then the Func+Child Time is
	greater than the Func Time.
	
	REFERENCES
	==========
	
	Visual C++ online documentation: search on "Function Timing"
	
	Additional query words: Prep Profile Plist Ftime
	
	======================================================================
	Keywords          : kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC420 kbVC500 kbVC600 
	Technology        : kbVCsearch kbAudDeveloper kbSProfilerSearch kbVC32bitSearch kbSProfiler100
	Version           : winnt:2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
