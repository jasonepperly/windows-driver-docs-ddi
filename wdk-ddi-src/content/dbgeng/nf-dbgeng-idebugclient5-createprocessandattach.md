---
UID: NF:dbgeng.IDebugClient5.CreateProcessAndAttach
title: IDebugClient5::CreateProcessAndAttach method
author: windows-driver-content
description: The CreateProcessAndAttach method creates a process from a specified command line, then attach to another user-mode process.
old-location: debugger\createprocessandattach.htm
old-project: debugger
ms.assetid: 1a92a823-ec50-406f-942c-c64fc820f9af
ms.author: windowsdriverdev
ms.date: 1/10/2018
ms.keywords: IDebugClient5, IDebugClient5::CreateProcessAndAttach, CreateProcessAndAttach
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugClient.CreateProcessAndAttach,IDebugClient2.CreateProcessAndAttach,IDebugClient3.CreateProcessAndAttach,IDebugClient4.CreateProcessAndAttach,IDebugClient5.CreateProcessAndAttach
req.alt-loc: dbgeng.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
req.typenames: *PDOT4_ACTIVITY, DOT4_ACTIVITY
---

# IDebugClient5::CreateProcessAndAttach method



## -description
The <b>CreateProcessAndAttach</b>  method creates a process from a specified command line, then attach to another user-mode process.  The created process is suspended and only allowed to execute when the attach has completed.  This allows rough synchronization when debugging both,  client and server processes.



## -syntax

````
HRESULT CreateProcessAndAttach(
  [in]           ULONG64 Server,
  [in, optional] PSTR    CommandLine,
  [in]           ULONG   CreateFlags,
  [in]           ULONG   ProcessId,
  [in]           ULONG   AttachFlags
);
````


## -parameters

### -param Server [in]

Specifies the process server to use to attach to the process.  If <i>Server</i> is zero, the engine will connect to the local process without using a process server.


### -param CommandLine [in, optional]

Specifies the command line to execute to create the new process.  If <i>CommandLine</i> is <b>NULL</b>, then no process is created and these methods attach to an existing process, as <a href="https://msdn.microsoft.com/library/windows/hardware/ff538150">AttachProcess</a> does.


### -param CreateFlags [in]

Specifies the flags to use when creating the process.  For details on these flags, see <a href="..\dbgeng\ns-dbgeng-_debug_create_process_options.md">DEBUG_CREATE_PROCESS_OPTIONS</a>.<b>CreateFlags</b>.


### -param ProcessId [in]

Specifies the process ID of the target process the debugger will attach to.  If <i>ProcessId</i> is zero, the debugger will attach to the process it created from <i>CommandLine</i>.


### -param AttachFlags [in]

Specifies the flags that control how the debugger attaches to the target process.  For details on these flags, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff541454">DEBUG_ATTACH_XXX</a>.


## -returns
This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.
<dl>
<dt><b>S_OK</b></dt>
</dl>The method was successful.

 


## -remarks
This method is available only for live user-mode debugging.

If <i>CommandLine</i> is not <b>NULL</b> and <i>ProcessId</i> is not zero, then the engine will create the process in a suspended state.  The engine will resume this newly created process after it successfully connects to the process specified in <i>ProcessId</i>.

For more information about creating and attaching to live user-mode targets, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552020">Live User-Mode Targets</a>.


## -see-also
<dl>
<dt>
<a href="..\dbgeng\nn-dbgeng-idebugclient.md">IDebugClient</a>
</dt>
<dt>
<a href="..\dbgeng\nn-dbgeng-idebugclient2.md">IDebugClient2</a>
</dt>
<dt>
<a href="..\dbgeng\nn-dbgeng-idebugclient3.md">IDebugClient3</a>
</dt>
<dt>
<a href="..\dbgeng\nn-dbgeng-idebugclient4.md">IDebugClient4</a>
</dt>
<dt>
<a href="..\dbgeng\nn-dbgeng-idebugclient5.md">IDebugClient5</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540055">CreateProcessAndAttach2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538150">AttachProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562135">.attach (Attach to Process)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562280">.create (Create Process)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539237">ConnectProcessServer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539323">CreateProcess2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548265">GetRunningProcessSystemIds</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548243">GetRunningProcessDescription</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541846">DetachCurrentProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558866">TerminateCurrentProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537786">AbandonCurrentProcess</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugClient::CreateProcessAndAttach method%20 RELEASE:%20(1/10/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

