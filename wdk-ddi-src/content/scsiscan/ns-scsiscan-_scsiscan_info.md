---
UID: NS:scsiscan._SCSISCAN_INFO
title: _SCSISCAN_INFO
author: windows-driver-content
description: The SCSISCAN_INFO structure is used as a parameter to DeviceIoControl (described in the Microsoft Windows SDK documentation), when the specified I/O control code is IOCTL_SCSISCAN_GET_INFO.
old-location: image\scsiscan_info.htm
old-project: image
ms.assetid: 5fd9b381-c0e3-45bf-9061-da816da5e29f
ms.author: windowsdriverdev
ms.date: 1/17/2018
ms.keywords: _SCSISCAN_INFO, *PSCSISCAN_INFO, SCSISCAN_INFO
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: scsiscan.h
req.include-header: Scsiscan.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SCSISCAN_INFO
req.alt-loc: scsiscan.h
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
req.typenames: *PSCSISCAN_INFO, SCSISCAN_INFO
req.product: Windows 10 or later.
---

# _SCSISCAN_INFO structure



## -description
The SCSISCAN_INFO structure is used as a parameter to <a href="https://msdn.microsoft.com/1d35c087-6672-4fc6-baa1-a886dd9d3878">DeviceIoControl</a> (described in the Microsoft Windows SDK documentation), when the specified I/O control code is <a href="..\scsiscan\ni-scsiscan-ioctl_scsiscan_get_info.md">IOCTL_SCSISCAN_GET_INFO</a>.



## -syntax

````
typedef struct _SCSISCAN_INFO {
  ULONG Size;
  ULONG Flags;
  UCHAR PortNumber;
  UCHAR PathId;
  UCHAR TargetId;
  UCHAR Lun;
  UCHAR AdapterName[MAX_STRING];
  ULONG Reserved;
} SCSISCAN_INFO, *PSCSISCAN_INFO;
````


## -struct-fields

### -field Size

Size, in bytes, of the SCSISCAN_INFO structure.


### -field Flags

Not used, must be zero.


### -field PortNumber

SCSI adapter number.


### -field PathId

Host SCSI ID.


### -field TargetId

Target SCSI ID.


### -field Lun

Target logical unit number (LUN).


### -field AdapterName

<i>For internal use only.</i>


### -field Reserved

<i>For internal use only.</i>


## -remarks
