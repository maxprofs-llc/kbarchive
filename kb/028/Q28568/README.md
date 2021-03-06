---
layout: page
title: "Q28568: Terminate-and-Stay-Resident (TSR) Program Example"
permalink: /kb/028/Q28568/
---

## Q28568: Terminate-and-Stay-Resident (TSR) Program Example

{% raw %}

	Article: Q28568
	Product(s): Microsoft Programming Utilities
	Version(s): 1.0,1.5,5.1,6.0,6.0a,6.0ax; MS-DOS:7.0
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft C for MS-DOS, versions 5.1, 6.0, 6.0a, 6.0ax 
	- Microsoft C/C++ for MS-DOS, version 7.0 
	- Microsoft Visual C++, versions 1.0, 1.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following code example demonstrates using Microsoft C to write a
	terminate-and-stay-resident (TSR) program. The example also demonstrates using
	the following functions in the C run-time library:
	
	     _dos_setvect
	     _dos_getvect
	     _dos_keep
	     _chain_intr
	     spawnXXX
	
	MORE INFORMATION
	================
	
	  DIRZAP.MAK
	  ----------
	
	  DIRZAP.OBJ:     DIRZAP.C
	            CL -AM -c DIRZAP.C
	            LINK DIRZAP.OBJ;
	
	  DIRZAP.H
	  --------
	
	  /********************************************************************/ 
	  /*                                                                  */ 
	  /*                            DirZap.h                              */ 
	  /*                                                                  */ 
	  /*        This header file defines a global variable, macros,       */ 
	  /*        function pointers, and function prototypes needed         */ 
	  /*        in the DirZap.c program.                                  */ 
	  /*                                                                  */ 
	  /*                                                                  */ 
	  /********************************************************************/ 
	
	  /* Global Variable For Macro SHIFTL(x, n) */ 
	  long _ADDRESS;
	
	  /* Macro Definitions */ 
	  #define INT5  0x5
	  #define INT21 0x21
	  #define SHIFTL(x, n) (_ADDRESS = 0L, _ADDRESS = (long)(x), _ADDRESS << (n))
	  #define HIBYTE(x) (((unsigned)(x) >> 8) & 0xff)
	  #define REGPAK unsigned es, unsigned ds, unsigned di, unsigned si,\ 
	                 unsigned bp, unsigned sp, unsigned bx, unsigned dx,\ 
	                 unsigned cx, unsigned ax, unsigned ip, unsigned  cs,\ 
	                 unsigned flags
	
	  /* Function Pointers */ 
	  void (interrupt far *save_dir_adr)();
	  /* Saves address of the original interrupt service routine */ 
	
	  void (interrupt far *set_dir_adr)();
	  /* This function pointer gets set to the address of the new
	     interrupt service routine 'set_dir' */ 
	
	  void (interrupt far *reset_dir_adr)();
	  /* This function pointer gets set to the address of the new
	     interrupt service routine 'reset_dir' */ 
	
	  /* Function Declarations */ 
	  void cdecl interrupt far set_dir(REGPAK);
	  /* This is the new service routine which zaps the directory
	     interrupt routines. */ 
	
	  void interrupt far reset_dir(void);
	  /* This routine toggles between setting and disabling the
	     directory interrupt routines */ 
	
	  unsigned _get_memsize(void);
	  /* This function gets the number of bytes to keep resident */ 
	
	  short _set_shell(void);
	  /* Sets a DOS shell. */ 
	
	  DIRZAP.C
	  --------
	
	  /*******************************************************************/ 
	  /*                                                                 */ 
	  /*                        DirZap.c                                 */ 
	  /*                                                                 */ 
	  /*  This is an illustration of a Terminate-and-Stay-Resident       */ 
	  /*  program. It traps and disables the directory interrupts for    */ 
	  /*  MkDir, RmDir, and ChDir.  When DirZap is in memory you can     */ 
	  /*  toggle it on and off with the PrintScreen key.  When it is     */ 
	  /*  on you will not be able to change directories or make or       */ 
	  /*  remove any directories.                                        */ 
	  /*  The PrintScreen key and directories have nothing to do with    */ 
	  /*  TSR programming.  They were just randomly picked to create     */ 
	  /*  an application.  This program is not intended to be a complete */ 
	  /*  application.  It's intent is to demonstrate how to write a     */ 
	  /*  TSR.  You can take the concept used here and incorporate it    */ 
	  /*  in to your own program.                                        */ 
	  /*  Below is a summary of what this program does :                 */ 
	  /*   - Save the address of INT 21                                  */ 
	  /*   - Revector INT 21 to a routine that disables the directory    */ 
	  /*     operations.                                                 */ 
	  /*   - Revector the PrintScreen interrupt to a routine that will   */ 
	  /*     toggle DirZap on and off.                                   */ 
	  /*   - Execute a _dos_keep to make the program resident            */ 
	  /*                                                                 */ 
	  /*                                                                 */ 
	  /*   Copyright (c) Microsoft Corp 1988. All rights reserved.       */ 
	  /*                                                                 */ 
	  /*  To run:                                                        */ 
	  /*          1) Type DirZap at dos prompt                           */ 
	  /*          2) The PRINT SCREEN key now toggles                    */ 
	  /*             DirZap on and off but no memory                     */ 
	  /*             is freed.                                           */ 
	  /*                                                                 */ 
	  /*******************************************************************/ 
	  /* NOTE:                                                           */ 
	  /*                                                                 */ 
	  /* THIS PROGRAM, ITS USE, OPERATION AND SUPPORT IS PROVIDED "AS IS"*/ 
	  /* WITHOUT WARRANTY OF ANY  KIND, EITHER EXPRESSED OR IMPLIED,     */ 
	  /* INCLUDING, BUT  NOT LIMITED TO, THE IMPLIED WARRANTIES OF        */ 
	  /* MERCHANTABILITY AND FITNESS FOR  A PARTICULAR PURPOSE.          */ 
	  /* THE ENTIRE RISK  AS TO THE QUALITY AND  PERFORMANCE OF THIS     */ 
	  /* PROGRAM IS WITH THE USER. IN NO EVENT SHALL MICROSOFT BE LIABLE */ 
	  /* FOR ANY DAMAGES  INCLUDING, WITHOUT LIMITATION,  ANY LOST       */ 
	  /* PROFITS,  LOST SAVINGS OR OTHER INCIDENTAL OR CONSEQUENTIAL     */ 
	  /* DAMAGES ARISING THE USE OR INABILITY TO USE SUCH PROGRAM, EVEN  */ 
	  /* IF MICROSOFT HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES*/ 
	  /* OR FOR ANY CLAIM BY ANY OTHER PARTY.                            */ 
	  /*******************************************************************/ 
	
	  #include <dos.h>
	  #include <stdio.h>
	  #include <stdlib.h>
	  #include <process.h>
	  #include "dirzap.h"
	
	  extern unsigned _psp;           /* _psp = segment address of PSP   */ 
	  unsigned far    *psp_pointer;   /* To retrieve the memsize to stay */ 
	                                  /* resident                        */ 
	  short           hot_key=1;      /* To toggle dirzap on and off     */ 
	
	  void main(void)
	  {
	
	        /***************************************/ 
	        /*                                     */ 
	        /* Revector the directory interrupts   */ 
	        /*                                     */ 
	        /***************************************/ 
	        save_dir_adr = _dos_getvect(INT21); /* Save original address  */ 
	        set_dir_adr  = set_dir;            /* Get addr of new routine */ 
	
	        /***************************************/ 
	        /*                                     */ 
	        /* Revector the PRINT SCREEN interrupt */ 
	        /*                                     */ 
	        /***************************************/ 
	        reset_dir_adr = reset_dir;          /* Get addr of new routine*/ 
	        _dos_setvect (INT5, reset_dir_adr); /* Revector to new routine*/ 
	
	        /***************************************/ 
	        /*                                     */ 
	        /*      Become memory resident.        */ 
	        /*                                     */ 
	        /***************************************/ 
	        _dos_keep(0, _get_memsize());
	
	        printf ("DirZap is now memory resident");  /* Inform the user */ 
	
	  }
	
	  void cdecl interrupt far set_dir(REGPAK)
	  {
	  /********************************************************************/ 
	  /*                                                                  */ 
	  /*  DS:DX points to the string entered by the user for MkDir, RmDir */ 
	  /*  and ChDir.  This function makes that string null so that        */ 
	  /*  the user will no longer be able to make, remove, or change      */ 
	  /*  directories.                                                    */ 
	  /*  WARNING: When compiled at high warning levels, several warnings */ 
	  /*  are generated. This is because several elements of REGPAK are   */ 
	  /*  not referenced. These warnings should be ignored.               */ 
	  /*                                                                  */ 
	  /********************************************************************/ 
	
	     if (HIBYTE(ax) == 0x39 || HIBYTE(ax) == 0x3A || HIBYTE(ax) == 0x3B)
	        dx=0;
	     _chain_intr(save_dir_adr);
	  }
	
	  void interrupt far reset_dir()
	  {
	     /****************************************************************/ 
	     /*                                                              */ 
	     /*  This function is used to toggle DirZap on and off.          */ 
	     /*                                                              */ 
	     /****************************************************************/ 
	
	     if (hot_key)
	     {
	        hot_key=0;
	        _dos_setvect(INT21, save_dir_adr);  /* Reset initial vector  */ 
	     }
	     else
	     {
	        hot_key=1;
	        _dos_setvect(INT21, set_dir_adr);   /* Install DirZap again  */ 
	        _chain_intr(set_dir_adr);    /* Chain to the Zapper function */ 
	     }
	  }
	
	  unsigned _get_memsize()
	  {
	     psp_pointer = (int far *) SHIFTL(_psp, 16); /* Get segment of the*/ 
	                                                 /* PSP               */ 
	     return(psp_pointer[1] - _psp);            /* Amount of memory to */ 
	                                               /* stay resident       */ 
	  }
	
	Additional query words: kbinf 1.00 1.50 5.10 6.00 6.00a 6.00ax 7.00
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbVCsearch kbAudDeveloper kbPTProdChange kbvc150 kbvc100 kbCCompSearch kbZNotKeyword3 kbCComp510DOS kbCComp600DOS kbCComp600aDOS kbCComp600axDOS kbCVC700DOS
	Version           : :1.0,1.5,5.1,6.0,6.0a,6.0ax; MS-DOS:7.0
	
	=============================================================================
	

{% endraw %}
