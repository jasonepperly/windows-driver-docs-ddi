---
UID: NF:fltkernel.FltGetVolumeFromFileObject
title: FltGetVolumeFromFileObject function
author: windows-driver-content
description: The FltGetVolumeFromFileObject routine returns an opaque pointer for the volume that a given file stream resides on.
old-location: ifsk\fltgetvolumefromfileobject.htm
old-project: ifsk
ms.assetid: 3b13c4a2-b2b5-4b59-881c-01ee430ac720
ms.author: windowsdriverdev
ms.date: 1/9/2018
ms.keywords: FltGetVolumeFromFileObject
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltGetVolumeFromFileObject
req.alt-loc: fltmgr.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: Fltmgr.sys
req.irql: <= APC_LEVEL
req.typenames: EXpsFontRestriction
---

# FltGetVolumeFromFileObject function



## -description
The <b>FltGetVolumeFromFileObject</b> routine returns an opaque pointer for the volume that a given file stream resides on. 



## -syntax

````
NTSTATUS FltGetVolumeFromFileObject(
  _In_  PFLT_FILTER  Filter,
  _In_  PFILE_OBJECT FileObject,
  _Out_ PFLT_VOLUME  *RetVolume
);
````


## -parameters

### -param Filter [in]

Opaque filter pointer for the caller. This parameter is required and cannot be <b>NULL</b>. 


### -param FileObject [in]

File object pointer for a file stream that resides on the volume. 


### -param RetVolume [out]

Pointer to a caller-allocated variable that receives an opaque pointer for the volume. This parameter is required and cannot be <b>NULL</b>. 


## -returns
<b>FltGetVolumeFromFileObject</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value, such as one of the following: 
<dl>
<dt><b>STATUS_FLT_DELETING_OBJECT</b></dt>
</dl>The volume is being torn down. This is an error code. 
<dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl>No matching volume was found. This is an error code. 

 


## -remarks
<b>FltGetVolumeFromFileObject</b> adds a rundown reference to the opaque volume pointer returned in the <i>RetVolume</i> parameter. When this pointer is no longer needed, the caller must release it by calling <a href="..\fltkernel\nf-fltkernel-fltobjectdereference.md">FltObjectDereference</a>. Thus every successful call to <b>FltGetVolumeFromFileObject</b> must be matched by a subsequent call to <b>FltObjectDereference</b>. 

To get a pointer to the device object for a given volume, call <a href="..\fltkernel\nf-fltkernel-fltgetdeviceobject.md">FltGetDeviceObject</a>. 


## -see-also
<dl>
<dt>
<a href="..\fltkernel\nf-fltkernel-fltgetdeviceobject.md">FltGetDeviceObject</a>
</dt>
<dt>
<a href="..\fltkernel\nf-fltkernel-fltgetdiskdeviceobject.md">FltGetDiskDeviceObject</a>
</dt>
<dt>
<a href="..\fltkernel\nf-fltkernel-fltgetvolumefromdeviceobject.md">FltGetVolumeFromDeviceObject</a>
</dt>
<dt>
<a href="..\fltkernel\nf-fltkernel-fltobjectdereference.md">FltObjectDereference</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltGetVolumeFromFileObject routine%20 RELEASE:%20(1/9/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

