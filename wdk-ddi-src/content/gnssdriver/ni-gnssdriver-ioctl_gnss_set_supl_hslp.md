---
UID: NI:gnssdriver.IOCTL_GNSS_SET_SUPL_HSLP
title: IOCTL_GNSS_SET_SUPL_HSLP
author: windows-driver-content
description: The IOCTL_GNSS_SET_SUPL_HSLP control code is used by the GNSS adapter to set the SUPL H-SLP address.
old-location: sensors\ioctl_gnss_set_supl_hslp.htm
old-project: sensors
ms.assetid: A6056EB4-4CEA-4C80-A3CA-1B6B81F47889
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: GNSS_SUPL_CERT_ACTION, GNSS_SUPL_CERT_ACTION
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: gnssdriver.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_GNSS_SET_SUPL_HSLP
req.alt-loc: gnssdriver.h
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
req.typenames: GNSS_SUPL_CERT_ACTION
---

# IOCTL_GNSS_SET_SUPL_HSLP IOCTL



## -description
The <b>IOCTL_GNSS_SET_SUPL_HSLP</b> control code is used by the GNSS adapter to set the SUPL H-SLP address.



## -ioctlparameters

### -input-buffer
A pointer to a <a href="..\gnssdriver\ns-gnssdriver-gnss_supl_hslp_config.md">GNSS_SUPL_HSLP_CONFIG</a> structure.


### -input-buffer-length
Set to sizeof(GNSS_SUPL_HSLP_CONFIG).


### -output-buffer
Set to NULL.


### -output-buffer-length
Set to 0.


### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. 


## -remarks
The driver sets one of the following NTSTATUS values to indicate result.

<b>STATUS_SUCCESS</b>, when the driver processes the SUPL H-SLP information successfully.

<b>Failed</b>, when the driver does not process the SUPL H-SLP information successfully.

<b>Ignored</b>, when the driver ignores the SUPL H-SLP information.

The GNSS driver must pass the H-SLP information, contained in the input structure, to the SUPL component which should connect to the server address specified by the H-SLP.

If the certificate with the same name is injected again, the GNSS driver should overwrite the previous certificate with the same name.

The H-SLP address is always in the form of a FQDN.


## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542894">Creating IOCTL Requests in Drivers</a>
</dt>
<dt>
<a href="..\wdfiotarget\nf-wdfiotarget-wdfiotargetsendinternalioctlotherssynchronously.md">WdfIoTargetSendInternalIoctlOthersSynchronously</a>
</dt>
<dt>
<a href="..\wdfiotarget\nf-wdfiotarget-wdfiotargetsendinternalioctlsynchronously.md">WdfIoTargetSendInternalIoctlSynchronously</a>
</dt>
<dt>
<a href="..\wdfiotarget\nf-wdfiotarget-wdfiotargetsendioctlsynchronously.md">WdfIoTargetSendIoctlSynchronously</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [sensors\sensors]:%20IOCTL_GNSS_SET_SUPL_HSLP control code%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

