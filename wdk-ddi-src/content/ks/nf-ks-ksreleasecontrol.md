---
UID: NF:ks.KsReleaseControl
title: KsReleaseControl function
author: windows-driver-content
description: The KsReleaseControl function releases the control mutex for Object.
old-location: stream\ksreleasecontrol.htm
old-project: stream
ms.assetid: f585f1ad-7ed0-49b1-ab35-a6b879118b38
ms.author: windowsdriverdev
ms.date: 1/9/2018
ms.keywords: KsReleaseControl
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsReleaseControl
req.alt-loc: Ks.lib,Ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: PASSIVE_LEVEL
req.typenames: 
---

# KsReleaseControl function



## -description
The<b> KsReleaseControl </b>function releases the control mutex for <i>Object</i>.



## -syntax

````
void KsReleaseControl(
  _In_ PVOID Object
);
````


## -parameters

### -param Object [in]

The object for which to release the control mutex.


## -returns
None


## -remarks
<i>Object</i> should be either a filter or a pin cast to PVOID.

Minidrivers typically do not call <b>KsReleaseControl</b> directly, but instead call <a href="..\ks\nf-ks-ksfilterreleasecontrol.md">KsFilterReleaseControl</a> or <a href="..\ks\nf-ks-kspinreleasecontrol.md">KsPinReleaseControl</a>. These versions automatically provide the necessary typecasting to PVOID.

For more information, see <a href="https://msdn.microsoft.com/011edaaa-7449-41c3-8cfb-0d319901af8b">Mutexes in AVStream</a>. 


## -see-also
<dl>
<dt>
<a href="..\ks\nf-ks-ksacquirecontrol.md">KsAcquireControl</a>
</dt>
<dt>
<a href="..\ks\nf-ks-ksfilteracquirecontrol.md">KsFilterAcquireControl</a>
</dt>
<dt>
<a href="..\ks\nf-ks-kspinacquirecontrol.md">KsPinAcquireControl</a>
</dt>
<dt>
<a href="..\ks\nf-ks-ksfilterreleasecontrol.md">KsFilterReleaseControl</a>
</dt>
<dt>
<a href="..\ks\nf-ks-kspinreleasecontrol.md">KsPinReleaseControl</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsReleaseControl function%20 RELEASE:%20(1/9/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

