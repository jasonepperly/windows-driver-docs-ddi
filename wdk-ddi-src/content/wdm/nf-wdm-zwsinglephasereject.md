---
UID: NF:wdm.ZwSinglePhaseReject
title: ZwSinglePhaseReject function
author: windows-driver-content
description: The ZwSinglePhaseReject routine informs KTM that the calling resource manager will not support single-phase commit operations for a specified enlistment.
old-location: kernel\zwsinglephasereject.htm
old-project: kernel
ms.assetid: a653a980-8ad6-46e7-ad9d-f060ab333731
ms.author: windowsdriverdev
ms.date: 1/4/2018
ms.keywords: ZwSinglePhaseReject
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Vista and later operating system versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ZwSinglePhaseReject,NtSinglePhaseReject
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
req.typenames: WORK_QUEUE_TYPE
req.product: Windows 10 or later.
---

# ZwSinglePhaseReject function



## -description
The <b>ZwSinglePhaseReject</b> routine informs KTM that the calling resource manager will not support <a href="https://msdn.microsoft.com/4885476e-ce68-4674-b8a5-8a317f33cd5b">single-phase commit operations</a> for a specified enlistment.



## -syntax

````
NTSTATUS ZwSinglePhaseReject(
  _In_     HANDLE         EnlistmentHandle,
  _In_opt_ PLARGE_INTEGER TmVirtualClock
);
````


## -parameters

### -param EnlistmentHandle [in]

A handle to an <a href="https://msdn.microsoft.com/80e61475-4bb7-4eaa-b9f1-ff95eac9bc77">enlistment object</a> that was obtained by a previous call to <a href="..\wdm\nf-wdm-zwcreateenlistment.md">ZwCreateEnlistment</a> or <a href="..\wdm\nf-wdm-zwopenenlistment.md">ZwOpenEnlistment</a>. The handle must have ENLISTMENT_SUBORDINATE_RIGHTS access to the object.


### -param TmVirtualClock [in, optional]

A pointer to a <a href="https://msdn.microsoft.com/de01b0f1-86b1-4e7d-af22-84dbbe3a3f83">virtual clock value</a>. This parameter is optional and can be <b>NULL</b>.


## -returns
<b>ZwSinglePhaseReject</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, this routine might return one of the following values: 
<dl>
<dt><b>STATUS_OBJECT_TYPE_MISMATCH</b></dt>
</dl>The specified handle is not a handle to an enlistment object.
<dl>
<dt><b>STATUS_INVALID_HANDLE</b></dt>
</dl>The object handle is invalid.
<dl>
<dt><b>STATUS_TRANSACTION_NOT_REQUESTED</b></dt>
</dl>The transaction or its enlistment is not in the correct state.
<dl>
<dt><b>STATUS_ACCESS_DENIED</b></dt>
</dl>The caller does not have appropriate access to the enlistment object.

 

The routine might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.


## -remarks
A resource manager can call <b>ZwSinglePhaseReject</b> when it receives a TRANSACTION_NOTIFY_SINGLE_PHASE_COMMIT <a href="https://msdn.microsoft.com/62169b56-e70f-4d32-a051-a7fd947dbc64">notification</a>. 

For more information about <b>ZwSinglePhaseReject</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff546783">Handling Commit Operations</a>.

<b>NtSinglePhaseReject</b> and <b>ZwSinglePhaseReject</b> are two versions of the same Windows Native System Services routine. The <b>NtSinglePhaseReject</b> routine in the Windows kernel is not directly accessible to kernel-mode drivers. However, kernel-mode drivers can access this routine indirectly by calling the <b>ZwSinglePhaseReject</b> routine.

For calls from kernel-mode drivers, the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a Windows Native System Services routine can behave differently in the way that they handle and interpret input parameters. For more information about the relationship between the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>.


## -see-also
<dl>
<dt>
<a href="..\wdm\nf-wdm-tmsinglephasereject.md">TmSinglePhaseReject</a>
</dt>
<dt>
<a href="..\wdm\nf-wdm-zwcreateenlistment.md">ZwCreateEnlistment</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>
</dt>
<dt>
<a href="..\wdm\nf-wdm-zwopenenlistment.md">ZwOpenEnlistment</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ZwSinglePhaseReject routine%20 RELEASE:%20(1/4/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

