---
UID: NF:wdfpdo.WdfPdoInitAllocate
title: WdfPdoInitAllocate function
author: windows-driver-content
description: The WdfPdoInitAllocate method allocates a WDFDEVICE_INIT structure for a framework-based bus driver, which the bus driver uses when reporting a new device.
old-location: wdf\wdfpdoinitallocate.htm
old-project: wdf
ms.assetid: 86e48354-d4cd-4ad0-a6bd-e8ba662075d8
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: WdfPdoInitAllocate
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfpdo.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfPdoInitAllocate
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: AddPdoToStaticChildList, DriverCreate, KmdfIrql, KmdfIrql2, PdoDeviceInitAPI, PdoInitFreeDeviceCallback, PdoInitFreeDeviceCreate, PdoInitFreeDeviceCreateType2, PdoInitFreeDeviceCreateType4
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: PASSIVE_LEVEL
req.typenames: WDF_OBJECT_CONTEXT_TYPE_INFO, *PWDF_OBJECT_CONTEXT_TYPE_INFO
req.product: Windows 10 or later.
---

# WdfPdoInitAllocate function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WdfPdoInitAllocate</b> method allocates a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a> structure for a framework-based bus driver, which the bus driver uses when reporting a new device.



## -syntax

````
PWDFDEVICE_INIT WdfPdoInitAllocate(
  _In_ WDFDEVICE ParentDevice
);
````


## -parameters

### -param ParentDevice [in]

A handle to a framework device object that represents the parent device of the new device. The framework device object must represent a functional device object (FDO).


## -returns
If the operation succeeds, the method returns a pointer to a framework-allocated <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a> structure. Otherwise, the method returns <b>NULL</b>.


## -remarks
If a bus driver uses static enumeration, it reports a new device by:

Calling <b>WdfPdoInitAllocate</b> to allocate a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a> structure.

Calling <a href="wdf_device_object_reference.htm#device_init_methods">framework device object initialization methods</a> and <a href="wdf_device_object_reference.htm#pdo_init_methods">framework PDO initialization methods</a>, as needed, to initialize the WDFDEVICE_INIT structure. If a call to one of these methods fails, the driver must call <a href="..\wdfdevice\nf-wdfdevice-wdfdeviceinitfree.md">WdfDeviceInitFree</a>. 

Calling <a href="..\wdfdevice\nf-wdfdevice-wdfdevicecreate.md">WdfDeviceCreate</a> to create a framework device object, supplying the initialized WDFDEVICE_INIT structure as input.

For more information about static enumeration, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/enumerating-the-devices-on-a-bus">Enumerating the Devices on a Bus</a>.

For a code example that uses <b>WdfPdoInitAllocate</b>, see <a href="..\wdffdo\nf-wdffdo-wdffdoaddstaticchild.md">WdfFdoAddStaticChild</a>.


## -see-also
<dl>
<dt>
<a href="..\wdfcontrol\nf-wdfcontrol-wdfcontroldeviceinitallocate.md">WdfControlDeviceInitAllocate</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfPdoInitAllocate method%20 RELEASE:%20(1/11/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

