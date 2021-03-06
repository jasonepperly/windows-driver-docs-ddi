---
UID: NF:rilapi.RIL_CloseUiccLogicalChannel
title: RIL_CloseUiccLogicalChannel function
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\ril_closeuicclogicalchannel.htm
old-project: netvista
ms.assetid: 4cc0c9b0-8ddc-408e-bc49-81e5a19843d2
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: RIL_CloseUiccLogicalChannel
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: rilapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RIL_CloseUiccLogicalChannel
req.alt-loc: rilapi.h
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
req.typenames: *PRH_QUERY_CONNECTION_PROPERTIES_OUTPUT_BUFFER, RH_QUERY_CONNECTION_PROPERTIES_OUTPUT_BUFFER
req.product: Windows 10 or later.
---

# RIL_CloseUiccLogicalChannel function



## -description
This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. 

            



## -syntax

````
HRESULT  RIL_CloseUiccLogicalChannel(
   HRIL   hRil,
   LPVOID lpContext,
   DWORD  dwSlotIndex,
   DWORD  dwChannelId
);
````


## -parameters

### -param hRil 


### -param lpContext 


### -param dwSlotIndex 


### -param dwChannelId 


## -returns
If this method succeeds, it returns <b xmlns:loc="http://microsoft.com/wdcml/l10n">S_OK</b>. Otherwise, it returns an <b xmlns:loc="http://microsoft.com/wdcml/l10n">HRESULT</b> error code.


## -remarks
