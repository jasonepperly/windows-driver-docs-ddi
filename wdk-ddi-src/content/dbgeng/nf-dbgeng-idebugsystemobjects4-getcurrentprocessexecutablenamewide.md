---
UID: NF:dbgeng.IDebugSystemObjects4.GetCurrentProcessExecutableNameWide
title: IDebugSystemObjects4::GetCurrentProcessExecutableNameWide method
author: windows-driver-content
description: The GetCurrentProcessExecutableNameWide method returns the name of executable file loaded in the current process.
old-location: debugger\getcurrentprocessexecutablenamewide.htm
old-project: debugger
ms.assetid: 4b87adca-e838-471b-a600-1327253ee45d
ms.author: windowsdriverdev
ms.date: 1/10/2018
ms.keywords: IDebugSystemObjects4, IDebugSystemObjects4::GetCurrentProcessExecutableNameWide, GetCurrentProcessExecutableNameWide
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
req.alt-api: IDebugSystemObjects4.GetCurrentProcessExecutableNameWide
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

# IDebugSystemObjects4::GetCurrentProcessExecutableNameWide method



## -description
The <b>GetCurrentProcessExecutableNameWide</b>  method returns the name of executable file loaded in the current process.



## -syntax

````
HRESULT GetCurrentProcessExecutableNameWide(
  [out, optional] PWSTR  Buffer,
  [in]            ULONG  BufferSize,
  [out, optional] PULONG ExeSize
);
````


## -parameters

### -param Buffer [out, optional]

Receives the name of the executable file.  If <i>Buffer</i> is <b>NULL</b>, this information is not returned.


### -param BufferSize [in]

Specifies the size in characters of the buffer <i>Buffer</i>.


### -param ExeSize [out, optional]

Receives the size in characters of the name of the executable file.  If <i>ExeSize</i> is <b>NULL</b>, this information is not returned.


## -returns
This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.
<dl>
<dt><b>S_OK</b></dt>
</dl>The method was successful.
<dl>
<dt><b>S_FALSE</b></dt>
</dl>The method was successful. However, the buffer was not large enough to hold the name of the executable file and it was truncated.

 


## -remarks
These methods are only available in user-mode debugging.

If the engine cannot determine the name of the executable file, it writes the string "?NoImage?" to the buffer.

For more information about processes, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff558896">Threads and Processes</a>.</p>