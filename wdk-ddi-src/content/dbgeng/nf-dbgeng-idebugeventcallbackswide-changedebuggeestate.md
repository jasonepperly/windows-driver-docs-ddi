---
UID: NF:dbgeng.IDebugEventCallbacksWide.ChangeDebuggeeState
title: IDebugEventCallbacksWide::ChangeDebuggeeState method
author: windows-driver-content
description: The ChangeDebuggeeState callback method is called by the engine when it makes or detects changes to the target.
old-location: debugger\idebugeventcallbackswide_changedebuggeestate.htm
old-project: debugger
ms.assetid: ffb5925a-6bbd-41f5-b8b8-e8c7189d57ac
ms.author: windowsdriverdev
ms.date: 1/10/2018
ms.keywords: IDebugEventCallbacksWide, IDebugEventCallbacksWide::ChangeDebuggeeState, ChangeDebuggeeState
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
req.alt-api: IDebugEventCallbacksWide.ChangeDebuggeeState
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

# IDebugEventCallbacksWide::ChangeDebuggeeState method



## -description
The <b>ChangeDebuggeeState</b> callback method is called by the engine when it makes or detects changes to the target.



## -syntax

````
HRESULT ChangeDebuggeeState(
  [in] ULONG   Flags,
  [in] ULONG64 Argument
);
````


## -parameters

### -param Flags [in]

Specifies the type of changes made to the target.  <i>Flags</i> may take one of the following values:

<table>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
<tr>
<td>
DEBUG_CDS_ALL

</td>
<td>
A general change in the target has occurred. For example, the target has been executing, or the engine has just attached to the target.

</td>
</tr>
<tr>
<td>
DEBUG_CDS_REGISTERS

</td>
<td>
The processor's register for the target have changed.

</td>
</tr>
<tr>
<td>
DEBUG_CDS_DATA

</td>
<td>
The target's data space has changed.

</td>
</tr>
</table>
 


### -param Argument [in]

Provides additional information about the change in the target. The interpretation of the value of <i>Argument</i> depends on the value of <i>Flags</i>:


### -param DEBUG_CDS_ALL

The value of <i>Argument</i> is zero.


### -param DEBUG_CDS_REGISTERS

If a single register has changed, the value of <i>Argument</i> is the index of that register.  Otherwise, the value of <i>Argument</i> is DEBUG_ANY_ID.


### -param DEBUG_CDS_DATA

The value of <i>Argument</i> specifies which data space was changed.  The following table contains the possible values of <i>Argument</i>.

<table>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
<tr>
<td>
DEBUG_DATA_SPACE_VIRTUAL

</td>
<td>
The target's virtual memory has changed.

</td>
</tr>
<tr>
<td>
DEBUG_DATA_SPACE_PHYSICAL

</td>
<td>
The target's physical memory has changed.

</td>
</tr>
<tr>
<td>
DEBUG_DATA_SPACE_CONTROL

</td>
<td>
The target's control memory has changed.

</td>
</tr>
<tr>
<td>
DEBUG_DATA_SPACE_IO

</td>
<td>
The target's I/O ports have received input or output.

</td>
</tr>
<tr>
<td>
DEBUG_DATA_SPACE_MSR

</td>
<td>
The target's Model-Specific Registers (MSRs) have changed.

</td>
</tr>
<tr>
<td>
DEBUG_DATA_SPACE_BUS_DATA

</td>
<td>
The target's bus memory has changed.

</td>
</tr>
</table>
 

</dd>
</dl>



## -returns
The return value is ignored by the engine unless it indicates a remote procedure call error; in this case the client, with which this <b>IDebugEventCallbacksWide</b> object is registered, is disabled.


## -remarks
The engine calls <b>ChangeDebuggeeState</b> only if the DEBUG_EVENT_CHANGE_DEBUGGEE_STATE flag is set in the mask returned by <a href="https://msdn.microsoft.com/library/windows/hardware/ff550625">IDebugEventCallbacksWide::GetInterestMask</a>.

For more information about handling events, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552239">Monitoring Events</a>.  For information about managing the target's memory, including registers and data spaces, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552179">Memory Access</a>.  For information about the target's virtual and physical memory, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff561217">Virtual and Physical Memory</a>.  For information about the target's control memory, I/O ports, MSR, and bus memory, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff553172">Other Data Spaces</a>.</p>