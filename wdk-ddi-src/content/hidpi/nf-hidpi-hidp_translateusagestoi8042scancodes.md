---
UID: NF:hidpi.HidP_TranslateUsagesToI8042ScanCodes
title: HidP_TranslateUsagesToI8042ScanCodes function
author: windows-driver-content
description: The HidP_TranslateUsagesToI8042ScanCodes routine maps a list of HID usages on the HID_USAGE_PAGE_KEYBOARD usage page to their respective PS/2 scan codes (Scan Code Set 1).
old-location: hid\hidp_translateusagestoi8042scancodes.htm
old-project: hid
ms.assetid: d3ad851d-ba09-4052-a2d0-d6cb8315e04f
ms.author: windowsdriverdev
ms.date: 12/21/2017
ms.keywords: HidP_TranslateUsagesToI8042ScanCodes
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: hidpi.h
req.include-header: Hidpi.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 2000 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HidP_TranslateUsagesToI8042ScanCodes
req.alt-loc: Hidparse.lib,Hidparse.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Hidparse.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
req.typenames: HIDP_REPORT_TYPE
---

# HidP_TranslateUsagesToI8042ScanCodes function



## -description
The <b>HidP_TranslateUsagesToI8042ScanCodes</b> routine maps a list of <a href="https://msdn.microsoft.com/84fed314-3554-4291-b51c-734d874a4bab">HID usages</a> on the HID_USAGE_PAGE_KEYBOARD usage page to their respective PS/2 scan codes (Scan Code Set 1).



## -syntax

````
NTSTATUS __stdcall HidP_TranslateUsagesToI8042ScanCodes(
  _In_     PUSAGE                        ChangedUsageList,
  _In_     ULONG                         UsageListLength,
  _In_     HIDP_KEYBOARD_DIRECTION       KeyAction,
  _Inout_  PHIDP_KEYBOARD_MODIFIER_STATE ModifierState,
  _In_     PHIDP_INSERT_SCANCODES        InsertCodesProcedure,
  _In_opt_ PVOID                         InsertCodesContext
);
````


## -parameters

### -param ChangedUsageList [in]

Pointer to a list of keyboard (button) usages. The translate usages routine interprets a zero as a delimiter that ends the usage list. 


### -param UsageListLength [in]

Specifies the maximum possible number of usages in the changed usage list. 


### -param KeyAction [in]

Identifies the key direction for the specified change usage list. 

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef enum _HIDP_KEYBOARD_DIRECTION {
    HidP_Keyboard_Break,
    HidP_Keyboard_Make
} HIDP_KEYBOARD_DIRECTION;</pre>
</td>
</tr>
</table></span></div>



### -param HidP_Keyboard_Break

Specifies a <i>break</i> direction (key up). The changed usage list contains the usages set to OFF that were previously set to ON (which corresponds to the keys that were previously down, but are now up).


### -param HidPKeyboard_Make

Specifies a <i>make</i> direction (key down). The changed usage list contains the usages set to ON that were previously set to OFF (which corresponds to the keys that were previously up, but now are down).

</dd>
</dl>

### -param ModifierState [in, out]

Pointer to a _HIDP_KEYBOARD_MODIFIER_STATE structure that the caller maintains for use by the translate usages routine. The modifier state structure identifies the state of the keyboard modifier keys. 

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _HIDP_KEYBOARD_MODIFIER_STATE {
    union {
      struct {
        ULONG LeftControl: 1;
        ULONG LeftShift: 1;
        ULONG LeftAlt: 1;
        ULONG LeftGUI: 1;
        ULONG RightControl: 1;
        ULONG RightShift: 1;
        ULONG RightAlt: 1;
        ULONG RigthGUI: 1;
        ULONG CapsLock: 1;
        ULONG ScollLock: 1;
        ULONG NumLock: 1;
        ULONG Reserved: 21;
      };
      ULONG ul;
};</pre>
</td>
</tr>
</table></span></div>
Each member of the modifier state structure identifies whether the corresponding usage is set to ON (1) or OFF (zero).

See the Remarks section for more information about how a modifier state structure is used with the translate usage routine.


### -param InsertCodesProcedure [in]

Pointer to a caller-supplied PHIDP_INSERT_SCANCODES-typed callback routine that the translate usage routine uses to return the mapped scan codes to the caller of the translate usage routine.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef BOOLEAN (*PHIDP_INSERT_SCANCODES)(
    IN PVOID  Context,
    IN PCHAR  NewScanCodes,
    IN ULONG  Length
    );</pre>
</td>
</tr>
</table></span></div>



### -param Context

Pointer to the context of the caller of the translate usage routine. The translate usage routine passes the <i>InsertCodesContext</i> pointer to the <i>InsertCodesProcedure</i> routine.


### -param NewScanCodes

Pointer to the first byte of a scan code that the translate usage routine returns to the caller of the translate usage routine.


### -param Length

Specifies the length, in bytes, of the scan code. A scan code cannot exceed four bytes.

</dd>
</dl>

### -param InsertCodesContext [in, optional]

Pointer to a caller-defined context that the translate usage routine passes to the <i>InsertCodesProcedure</i> routine.


## -returns
<b>HidP_TranslateUsagesToI8042ScanCodes</b> returns one of the following status values:
<dl>
<dt><b>HIDP_STATUS_SUCCESS</b></dt>
</dl>The translate usage routine successfully mapped all the valid usages in the changed usage list.
<dl>
<dt><b>HIDP_STATUS_I8042_TRANS_UNKNOWN</b></dt>
</dl>A usage in the changed usage list mapped to an invalid keyboard scan code.

 


## -remarks
<b>HidP_TranslateUsagesToI8042ScanCodes</b> sequentially maps the keyboard button usages in the changed usage list in the order in which they occur in the list, beginning with the value at <i>ChangedUsageList.</i> After the translate usage routine successfully maps a usage, it uses the caller's <i>InsertCodesProcedure</i> routine to return the corresponding scan code to the caller. The translate usage routine continues to map the usages in the list until one of the following occurs: a usage value in the list is zero; it maps the number of usages that is specified by <i>UsageListLength</i>; a usage maps to an invalid keyboard scan code.

<b>HidP_TranslateUsagesToI8042ScanCodes</b> is designed primarily to be used in a processing loop that repeatedly determines the current usage list (usages that are currently set to ON), compares them with a previous usage list (usages that were previously set to ON), and maps the difference between the current and previous usage lists to make scan codes and break scan codes. The following operations illustrate how to use the translate usages routine.

Prior to beginning a processing loop, the processing code typically allocates and initializes the following data:

A previous usage list, current usage list, break usage list, and a make usage list.

Each list is a zero-initialized array of usages. To ensure that the processing code maps all the usages that can change between consecutive HID input reports, the processing code must set the number of elements in each list to the maximum number of usages that <a href="..\hidpi\nf-hidpi-hidp_getusages.md">HidP_GetUsages</a> can return for the HID_USAGE_PAGE_KEYBOARD usage page. This number is obtained using <a href="..\hidpi\nf-hidpi-hidp_maxusagelistlength.md">HidP_MaxUsageListLength</a>.

A zero-initialized _HIDP_KEYBOARD_MODIFIER_STATE structure for use by the translate usages routine.

In the processing loop, the code must maintain this structure for use by the translate usages routine. The processing code can read the state of the modifier keys, but the code must not modify the structure. The translate usage routine uses this structure to maintain internal information about the state of the modifier keys. 

After initializing the required structures, each iteration of the processing loop typically includes the following sequence of operations:

Call <b>HidP_GetUsages</b> to obtain the current usage list of usages that are set to ON. Set the <i>UsagePage</i> input parameter of the get usages routine to HID_USAGE_PAGE_KEYBOARD. 

Call <b>HidP_UsageListDifference</b> to compare the current usage list of usages to a previous usage list. The usage list difference routine returns a break usage list and a make usage list.

Call the translate usage routine, setting <i>ChangedUsageList</i> to the break usage list, <i>KeyAction</i> to HidP_KeyboardBreak, and <i>ModifierState</i> to the structure that the processing code maintains for the translate usages routine. The translate usages routine uses the <i>InsertCodesProcedure</i>s callback routine to return the break scan codes to the processing loop.

Call the translate usage routine, setting <i>ChangedUsageList</i> to the make usage list, <i>KeyAction</i> to HidP_KeyboardMake, and <i>ModifierState</i> to the structure that the processing code maintains for the translate usages routine. The translate usages routine uses the <i>InsertCodesProcedure</i>s callback routine to return the make scan codes to the processing loop.

Update the previous usage list to the current usage list.

For information about the mapping between HID usages and PS/2 keyboard scan codes, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=242210">key support and scan codes</a> website.


## -see-also
<dl>
<dt>
<a href="..\hidpi\nf-hidpi-hidp_getusages.md">HidP_GetUsages</a>
</dt>
<dt>
<a href="..\hidpi\nf-hidpi-hidp_maxusagelistlength.md">HidP_MaxUsageListLength</a>
</dt>
<dt>
<a href="..\hidpi\nf-hidpi-hidp_usagelistdifference.md">HidP_UsageListDifference</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20HidP_TranslateUsagesToI8042ScanCodes routine%20 RELEASE:%20(12/21/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

