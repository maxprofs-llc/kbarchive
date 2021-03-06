---
layout: page
title: "Q154632: FIX: Accept Returns FALSE but GetLastError Returns 0"
permalink: /kb/154/Q154632/
---

## Q154632: FIX: Accept Returns FALSE but GetLastError Returns 0

{% raw %}

	Article: Q154632
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.1,4.2
	Operating System(s): 
	Keyword(s): kbMFC kbVC150bug kbVC200bug kbVC400bug kbVC410bug kbVC420fix kbWinsock kbDSupport kbGrp
	Last Modified: 04-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, version 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	A call to CSocket or CAsyncSocket::Accept returns FALSE, but a call to
	GetLastError or WSAGetLastError returns 0. The same code works correctly with
	MFC version 4.0.
	
	CAUSE
	=====
	
	MFC maintains information in Thread Local Storage. In CAsyncSocket::Accept, the
	MFC code makes a call to DetachHandle that indirectly makes a call to
	TlsGetValue. This occurs after a call to the WinSock API function accept(). The
	call to TlsGetValue resets the thread's error code to zero and the error
	returned from the accept() call is lost.
	
	RESOLUTION
	==========
	
	If your class is derived directly from CAsyncSocket, then replace the Accept
	function and modify it so that the error code is not lost.
	
	This can be done by first borrowing the function from the CAsyncSocket::Accept
	function found in the MFC source code in the file SOCKCORE.CPP. Change the
	function to be implemented as follows:
	
	     #if _MFC_VER >= 0x0410 && _MFC_VER <= 0x0420
	
	     BOOL CMySocket::Accept(CAsyncSocket& rConnectedSocket,
	                            SOCKADDR* lpSockAddr, int* lpSockAddrLen)
	     {
	       ASSERT(rConnectedSocket.m_hSocket == INVALID_SOCKET);
	       ASSERT(CAsyncSocket::FromHandle(INVALID_SOCKET) == NULL);
	
	       CAsyncSocket::AttachHandle(INVALID_SOCKET, &rConnectedSocket);
	
	       SOCKET hTemp = accept(m_hSocket, lpSockAddr, lpSockAddrLen);
	
	       if (hTemp == INVALID_SOCKET)
	       {
	     // <===== STORE THE ERROR CODE RECEIVED FROM THE accept CALL
	         int nError = WSAGetLastError();
	
	         CAsyncSocket::DetachHandle(rConnectedSocket.m_hSocket, FALSE);
	
	     // <===== RE-SET THE ERROR CODE THAT WAS SET IN THE accept CALL
	         WSASetLastError(nError);
	
	         rConnectedSocket.m_hSocket = INVALID_SOCKET;
	       }
	       else if (CAsyncSocket::FromHandle(INVALID_SOCKET) != NULL)
	       {
	         rConnectedSocket.m_hSocket = hTemp;
	         CAsyncSocket::DetachHandle(INVALID_SOCKET, FALSE);
	         CAsyncSocket::AttachHandle(hTemp, &rConnectedSocket);
	       }
	
	       return (hTemp != INVALID_SOCKET);
	     }
	
	     #endif  // _MFC_VER
	
	If your class is derived from CSocket, then you will have to replace
	CAsyncSocket::Accept as well as CSocket::Accept. This is necessary because
	CSocket::Accept directly calls CAsyncSocket::Accept. This can be accomplished by
	providing your own Accept function, called AcceptFix. It would be implemented
	just as the Accept function shown above. For example:
	
	     #if _MFC_VER >= 0x0410 && _MFC_VER <= 0x0420
	
	     BOOL CMySocket::AcceptFix(CAsyncSocket& rConnectedSocket,
	                               SOCKADDR* lpSockAddr, int* lpSockAddrLen)
	     {
	        ...
	        // IMPLEMENTATION IS THE SAME AS THE ONE SHOWN ABOVE
	        ...
	        return (hTemp != INVALID_SOCKET);
	     }
	
	     #endif // _MFC_VER
	
	Then provide a replacement for CSocket::Accept and modify it to call AcceptFix
	instead of CAsyncSocket::Accept. You can borrow the CSocket::Accept function
	from SOCKCORE.CPP and modify it as follows:
	
	     #if _MFC_VER >= 0x0410 && _MFC_VER <= 0x0420
	
	     BOOL CMySocket::Accept(CAsyncSocket& rConnectedSocket,
	                            SOCKADDR* lpSockAddr, int* lpSockAddrLen)
	     {
	       if (m_pbBlocking != NULL)
	       {
	         WSASetLastError(WSAEINPROGRESS);
	         return FALSE;
	       }
	
	       // <===============  REPLACE THE FOLLOWING LINE
	       // while (!CAsyncSocket::Accept(rConnectedSocket, lpSockAddr,...
	       // <===============  WITH THIS:
	
	       while (!AcceptFix(rConnectedSocket, lpSockAddr, lpSockAddrLen))
	       {
	         if (GetLastError() == WSAEWOULDBLOCK)
	         {
	           if (!PumpMessages(FD_ACCEPT))
	             return FALSE;
	         }
	         else
	           return FALSE;
	       }
	       return TRUE;
	     }
	
	     #endif // _MFC_VER
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been corrected in the Visual C++ 4.2b
	technology update.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbMFC kbVC150bug kbVC200bug kbVC400bug kbVC410bug kbVC420fix kbWinsock kbDSupport kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:4.1,4.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
