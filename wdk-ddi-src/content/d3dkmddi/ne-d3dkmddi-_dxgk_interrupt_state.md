---
UID: NE:d3dkmddi._DXGK_INTERRUPT_STATE
title: _DXGK_INTERRUPT_STATE
author: windows-driver-content
description: .
old-location: display\dxgk_interrupt_state.htm
old-project: display
ms.assetid: C72DF96B-5D12-4AC0-8FBB-904E087807DB
ms.author: windowsdriverdev
ms.date: 12/29/2017
ms.keywords: _DXGK_INTERRUPT_STATE, DXGK_INTERRUPT_STATE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: enum
req.header: d3dkmddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 10.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_INTERRUPT_STATE
req.alt-loc: d3dkmddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
req.typenames: DXGK_INTERRUPT_STATE
---

# _DXGK_INTERRUPT_STATE enumeration



## -description
Provides additional information for <a href="..\d3dkmddi\nc-d3dkmddi-dxgkddi_controlinterrupt2.md">DxgkDdi_ControlInterrupt2 </a>when VSYNC is not being utilized.



## -syntax

````
typedef enum _DXGK_INTERRUPT_STATE { 
  DXGK_INTERRUPT_ENABLE      = 0,
  DXGK_INTERRUPT_DISABLE     = 1
} DXGK_INTERRUPT_STATE;
````


## -enum-fields

### -field DXGK_INTERRUPT_ENABLE    

Indicates that the interrupt is enabled.


### -field DXGK_INTERRUPT_DISABLE   

Indicates that the interrupt is disabled.


## -remarks
