---
UID: NS:wdm._REG_SET_VALUE_KEY_INFORMATION
title: _REG_SET_VALUE_KEY_INFORMATION
author: windows-driver-content
description: The REG_SET_VALUE_INFORMATION structure describes a new setting for a registry key's value entry.
old-location: kernel\reg_set_value_key_information.htm
old-project: kernel
ms.assetid: a74d9740-8342-454e-8cbf-cf248e67d857
ms.author: windowsdriverdev
ms.date: 1/4/2018
ms.keywords: _REG_SET_VALUE_KEY_INFORMATION, *PREG_SET_VALUE_KEY_INFORMATION, REG_SET_VALUE_KEY_INFORMATION
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: Available on Microsoft Windows XP and later versions of the Windows operating system.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: REG_SET_VALUE_KEY_INFORMATION
req.alt-loc: wdm.h
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
req.typenames: *PREG_SET_VALUE_KEY_INFORMATION, REG_SET_VALUE_KEY_INFORMATION
req.product: Windows 10 or later.
---

# _REG_SET_VALUE_KEY_INFORMATION structure



## -description
The <b>REG_SET_VALUE_INFORMATION</b> structure describes a new setting for a registry key's value entry.



## -syntax

````
typedef struct _REG_SET_VALUE_KEY_INFORMATION {
  PVOID           Object;
  PUNICODE_STRING ValueName;
  ULONG           TitleIndex;
  ULONG           Type;
  PVOID           Data;
  ULONG           DataSize;
  PVOID           CallContext;
  PVOID           ObjectContext;
  PVOID           Reserved;
} REG_SET_VALUE_KEY_INFORMATION, *PREG_SET_VALUE_KEY_INFORMATION;
````


## -struct-fields

### -field Object

A pointer to the registry key object for the key whose value entry is about to be changed.


### -field ValueName

A pointer to a <a href="..\wudfwdm\ns-wudfwdm-_unicode_string.md">UNICODE_STRING</a> structure that contains the name of the value entry about to be changed. 


### -field TitleIndex

Reserved for system use. Drivers should ignore this member. 


### -field Type

The type of data that is about to be written. For more information about the possible values for this member, see the <i>Type</i> parameter of <a href="..\wdm\nf-wdm-zwsetvaluekey.md">ZwSetValueKey</a>.


### -field Data

A pointer to a buffer that contains the data about to be written. The format of the buffer depends on the value of <b>Type</b>. For more information, see <a href="..\wdm\nf-wdm-zwsetvaluekey.md">ZwSetValueKey</a>.


### -field DataSize

The size, in bytes, of the <b>Data</b> buffer.


### -field CallContext

Optional driver-defined context information that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a> routine can supply. This member is defined for Windows Vista and later versions of the Windows operating system. 


### -field ObjectContext

A pointer to driver-defined context information that the driver has associated with a registry object by calling <a href="..\wdm\nf-wdm-cmsetcallbackobjectcontext.md">CmSetCallbackObjectContext</a>. This member is defined for Windows Vista and later versions of the Windows operating system.


### -field Reserved

This member is reserved for future use. This member is defined for Windows Vista and later versions of the Windows operating system.


## -remarks
The system passes this structure to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a> routine every time a thread attempts to set a value entry for a key—for example, when a user-mode thread calls <b>RegSetValue</b> or <b>RegSetValueEx</b> or when a driver calls <a href="..\wdm\nf-wdm-zwsetvaluekey.md">ZwSetValueKey</a>.

For more information about registry filtering operations, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff545879">Filtering Registry Calls</a>.


## -see-also
<dl>
<dt>
<a href="..\wdm\nf-wdm-cmsetcallbackobjectcontext.md">CmSetCallbackObjectContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a>
</dt>
<dt>
<a href="..\wdm\nf-wdm-zwsetvaluekey.md">ZwSetValueKey</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20REG_SET_VALUE_KEY_INFORMATION structure%20 RELEASE:%20(1/4/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

