---
UID: NF:wdm.RtlCompareUnicodeString
title: RtlCompareUnicodeString function
author: windows-driver-content
description: The RtlCompareUnicodeString routine compares two Unicode strings.
old-location: kernel\rtlcompareunicodestring.htm
old-project: kernel
ms.assetid: 82567434-be54-4436-a26e-9a89a532addf
ms.author: windowsdriverdev
ms.date: 1/4/2018
ms.keywords: RtlCompareUnicodeString
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlCompareUnicodeString
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
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

# RtlCompareUnicodeString function



## -description
The <b>RtlCompareUnicodeString</b> routine compares two Unicode strings.



## -syntax

````
LONG RtlCompareUnicodeString(
  _In_ PCUNICODE_STRING String1,
  _In_ PCUNICODE_STRING String2,
  _In_ BOOLEAN          CaseInSensitive
);
````


## -parameters

### -param String1 [in]

Pointer to the first string.


### -param String2 [in]

Pointer to the second string.


### -param CaseInSensitive [in]

If <b>TRUE</b>, case should be ignored when doing the comparison. 


## -returns
<b>RtlCompareUnicodeString</b> returns a signed value that gives the results of the comparison:
<dl>
<dt><b>Zero</b></dt>
</dl><i>String1</i> equals <i>String2</i>.
<dl>
<dt><b>&lt; Zero</b></dt>
</dl><i>String1</i> is less than <i>String2</i>.
<dl>
<dt><b>&gt; Zero </b></dt>
</dl><i>String1</i> is greater than <i>String2</i>.

 


## -remarks


## -see-also
<dl>
<dt>
<a href="..\ntddk\nf-ntddk-rtlcomparestring.md">RtlCompareString</a>
</dt>
<dt>
<a href="..\ntddk\nf-ntddk-rtlequalstring.md">RtlEqualString</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RtlCompareUnicodeString routine%20 RELEASE:%20(1/4/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

