---
UID: NS:rilapitypes.RILSETNOTIFICATIONFILTERSTATEPARAMS
title: RILSETNOTIFICATIONFILTERSTATEPARAMS
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilsetnotificationfilterstateparams_2.htm
old-project: netvista
ms.assetid: 87dc2ef3-047c-4255-832c-508b378ca412
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: RILSETNOTIFICATIONFILTERSTATEPARAMS, *LPRILSETNOTIFICATIONFILTERSTATEPARAMS, RILSETNOTIFICATIONFILTERSTATEPARAMS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: rilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILSETNOTIFICATIONFILTERSTATEPARAMS
req.alt-loc: rilapitypes.h
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
req.typenames: *LPRILSETNOTIFICATIONFILTERSTATEPARAMS, RILSETNOTIFICATIONFILTERSTATEPARAMS
req.product: Windows 10 or later.
---

# RILSETNOTIFICATIONFILTERSTATEPARAMS structure



## -description
This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. 



## -syntax

````
typedef struct _RILSETNOTIFICATIONFILTERSTATEPARAMS {
  DWORD  dwFilterMask;
  DWORD  dwFilterState;
} RILSETNOTIFICATIONFILTERSTATEPARAMS, RILSETNOTIFICATIONFILTERSTATEPARAMS;
````


## -struct-fields

### -field dwFilterMask


### -field dwFilterState


## -remarks
