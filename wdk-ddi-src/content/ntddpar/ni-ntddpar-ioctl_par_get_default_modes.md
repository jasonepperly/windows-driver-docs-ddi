---
UID: NI:ntddpar.IOCTL_PAR_GET_DEFAULT_MODES
title: IOCTL_PAR_GET_DEFAULT_MODES
author: windows-driver-content
description: The IOCTL_PAR_GET_DEFAULT_MODES request returns the default write (forward) and read (reverse) IEEE 1284 protocols that the system-supplied bus driver for parallel ports uses.
old-location: parports\ioctl_par_get_default_modes.htm
old-project: parports
ms.assetid: d2f440b2-1208-4cae-9790-b93f267499b1
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _OFFLOAD_SECURITY_ASSOCIATION, OFFLOAD_SECURITY_ASSOCIATION, *POFFLOAD_SECURITY_ASSOCIATION
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: ntddpar.h
req.include-header: Ntddpar.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_PAR_GET_DEFAULT_MODES
req.alt-loc: ntddpar.h
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
req.typenames: OFFLOAD_SECURITY_ASSOCIATION, *POFFLOAD_SECURITY_ASSOCIATION
---

# IOCTL_PAR_GET_DEFAULT_MODES IOCTL



## -description

The IOCTL_PAR_GET_DEFAULT_MODES request returns the default write (forward) and read (reverse) IEEE 1284 protocols that the system-supplied bus driver for parallel ports uses. The default write protocol is CENTRONICS; the default read protocol is NIBBLE. 

For more information, see <a href="https://msdn.microsoft.com/2ff53ed0-dbb7-4c8f-b6e4-5f7d20124a7c">Setting and Clearing a Communication Mode for a Parallel Device</a>.



The IOCTL_PAR_GET_DEFAULT_MODES request returns the default write (forward) and read (reverse) IEEE 1284 protocols that the system-supplied bus driver for parallel ports uses. The default write protocol is CENTRONICS; the default read protocol is NIBBLE. 

For more information, see <a href="https://msdn.microsoft.com/2ff53ed0-dbb7-4c8f-b6e4-5f7d20124a7c">Setting and Clearing a Communication Mode for a Parallel Device</a>.



## -ioctlparameters

### -input-buffer
None.


### -input-buffer-length
None.


### -output-buffer
The <b>AssociatedIrp.SystemBuffer</b> member points to a PARCLASS_NEGOTIATION_MASK structure that the client allocates to output mode information. The system-supplied bus driver for parallel ports sets the <b>usReadMask</b> member and the <b>usWriteMask</b> member. The default write mode is CENTRONICS; the default read mode is NIBBLE.


### -output-buffer-length
The value of the <b>Parameters.DeviceIoControl.OutputBufferLength</b> member is set to the size, in bytes, of a <a href="..\ntddpar\ns-ntddpar-_parclass_negotiation_mask.md">PARCLASS_NEGOTIATION_MASK</a> structure. 


### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
If the request is successful, the <b>Information</b> member is set to the size, in bytes, of a PARCLASS_NEGOTIATION_MASK structure. Otherwise, <b>Information</b> is set to zero. 

The <b>Status</b> member is set to one of the generic status values returned by device control requests for parallel devices or to the following value:



The value of the <b>Parameters.DeviceIoControl.OutputBufferLength</b> is less than the size, in bytes, of a PARCLASS_NEGOTIATION_MASK structure.


## -remarks


## -see-also
<dl>
<dt>
<a href="..\ntddpar\ni-ntddpar-ioctl_ieee1284_get_mode.md">IOCTL_IEEE1284_GET_MODE</a>
</dt>
<dt>
<a href="..\ntddpar\ni-ntddpar-ioctl_ieee1284_negotiate.md">IOCTL_IEEE1284_NEGOTIATE</a>
</dt>
<dt>
<a href="..\ntddpar\ni-ntddpar-ioctl_par_get_device_caps.md">IOCTL_PAR_GET_DEVICE_CAPS</a>
</dt>
<dt>
<a href="..\ntddpar\ns-ntddpar-_parclass_negotiation_mask.md">PARCLASS_NEGOTIATION_MASK</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [parports\parports]:%20IOCTL_PAR_GET_DEFAULT_MODES control code%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

