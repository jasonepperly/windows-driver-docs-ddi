---
UID: NC:wdfchildlist.EVT_WDF_CHILD_LIST_SCAN_FOR_CHILDREN
title: EVT_WDF_CHILD_LIST_SCAN_FOR_CHILDREN
author: windows-driver-content
description: A driver's EvtChildListScanForChildren event callback function must report all of the child devices that are present.
old-location: wdf\evtchildlistscanforchildren.htm
old-project: wdf
ms.assetid: 57b06ecd-fc8c-4653-bb78-2bc6ecde6d63
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: _WDBGEXTS_THREAD_OS_INFO, *PWDBGEXTS_THREAD_OS_INFO, WDBGEXTS_THREAD_OS_INFO
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: wdfchildlist.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: EvtChildListScanForChildren
req.alt-loc: WdfChildlist.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (see Remarks section)
req.typenames: *PWDBGEXTS_THREAD_OS_INFO, WDBGEXTS_THREAD_OS_INFO
req.product: Windows 10 or later.
---

# EVT_WDF_CHILD_LIST_SCAN_FOR_CHILDREN callback



## -description
<p class="CCE_Message">[Applies to KMDF only]

A driver's <i>EvtChildListScanForChildren</i> event callback function must report all of the child devices that are present. 



## -prototype

````
EVT_WDF_CHILD_LIST_SCAN_FOR_CHILDREN EvtChildListScanForChildren;

VOID EvtChildListScanForChildren(
  _In_ WDFCHILDLIST ChildList
)
{ ... }
````


## -parameters

### -param ChildList [in]

A handle to a framework child list object.


## -returns
None


## -remarks
If a bus driver is using <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/dynamic-enumeration">dynamic enumeration</a>, it can register an <i>EvtChildListScanForChildren</i> callback function by calling <a href="..\wdffdo\nf-wdffdo-wdffdoinitsetdefaultchildlistconfig.md">WdfFdoInitSetDefaultChildListConfig</a> or <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistcreate.md">WdfChildListCreate</a>.

If a driver provides an <i>EvtChildListScanForChildren</i> callback function, the framework calls it each time the parent device enters its working (D0) state. (For more information about when this callback function is called, see <a href="https://msdn.microsoft.com/9175ce95-196d-44bd-b31c-88386fa0d3d3">PnP and Power Management Scenarios</a>.)

The driver must report all of its child devices by doing the following:

Calling <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistbeginscan.md">WdfChildListBeginScan</a>, which marks all previously reported child devices as missing. 

Detecting child devices and calling <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistaddorupdatechilddescriptionaspresent.md">WdfChildListAddOrUpdateChildDescriptionAsPresent</a> for each detected device.

Calling <a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistendscan.md">WdfChildListEndScan</a>, which informs the PnP manager of the reported child devices. 

For more information about dynamic enumeration, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/enumerating-the-devices-on-a-bus">Enumerating the Devices on a Bus</a>.

The <i>EvtChildListScanForChildren</i> callback function is called at IRQL = PASSIVE_LEVEL. You should not make this callback function <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/creating-pageable-code-in-a-kmdf-driver">pageable</a>.

To define an <i>EvtChildListScanForChildren</i> callback function, you must first provide a function declaration that identifies the type of callback function you’re defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="https://msdn.microsoft.com/2F3549EF-B50F-455A-BDC7-1F67782B8DCA">Code Analysis for Drivers</a>, <a href="https://msdn.microsoft.com/74feeb16-387c-4796-987a-aff3fb79b556">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it’s a requirement for writing drivers for the Windows operating system.

For example, to define an <i>EvtChildListScanForChildren</i> callback function that is named <i>MyChildListScanForChildren</i>, use the <b>EVT_WDF_CHILD_LIST_SCAN_FOR_CHILDREN</b> type as shown in this code example:

To define an <i>EvtChildListScanForChildren</i> callback function that is named <b>MyChildListScanForChildren</b>, you must first provide a function declaration that SDV and other verification tools require, as follows:

Then, implement your callback function as follows:

The <b>EVT_WDF_CHILD_LIST_SCAN_FOR_CHILDREN</b> function type is defined in the WdfChildlist.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_WDF_CHILD_LIST_SCAN_FOR_CHILDREN</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="https://msdn.microsoft.com/73a408ba-0219-4fde-8dad-ca330e4e67c3">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For information about _Use_decl_annotations_, see <a href="https://msdn.microsoft.com/en-US/library/c0aa268d-6fa3-4ced-a8c6-f7652b152e61">Annotating Function Behavior</a>.


## -see-also
<dl>
<dt>
<a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistaddorupdatechilddescriptionaspresent.md">WdfChildListAddOrUpdateChildDescriptionAsPresent</a>
</dt>
<dt>
<a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistbeginscan.md">WdfChildListBeginScan</a>
</dt>
<dt>
<a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistcreate.md">WdfChildListCreate</a>
</dt>
<dt>
<a href="..\wdfchildlist\nf-wdfchildlist-wdfchildlistendscan.md">WdfChildListEndScan</a>
</dt>
<dt>
<a href="..\wdffdo\nf-wdffdo-wdffdoinitsetdefaultchildlistconfig.md">WdfFdoInitSetDefaultChildListConfig</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20EVT_WDF_CHILD_LIST_SCAN_FOR_CHILDREN callback function%20 RELEASE:%20(1/11/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

