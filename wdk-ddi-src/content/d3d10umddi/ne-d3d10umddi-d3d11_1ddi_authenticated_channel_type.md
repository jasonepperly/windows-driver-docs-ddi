---
UID: NE:d3d10umddi.D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE
title: D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE
author: windows-driver-content
description: Specifies the type of Microsoft Direct3D authenticated channel.
old-location: display\d3d11_1ddi_authenticated_channel_type.htm
old-project: display
ms.assetid: da04ef5d-c3e4-4321-8cc8-e20763c5a7db
ms.author: windowsdriverdev
ms.date: 12/29/2017
ms.keywords: D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE, D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: enum
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE
req.alt-loc: D3d10umddi.h
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
req.typenames: D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE
---

# D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE enumeration



## -description
Specifies the type of Microsoft Direct3D authenticated channel.



## -syntax

````
typedef enum D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE { 
  D3D11_1DDI_AUTHENTICATED_CHANNEL_DRIVER_SOFTWARE  = 2,
  D3D11_1DDI_AUTHENTICATED_CHANNEL_DRIVER_HARDWARE  = 3
} D3D11_1DDI_AUTHENTICATED_CHANNEL_TYPE;
````


## -enum-fields

### -field D3D11_1DDI_AUTHENTICATED_CHANNEL_DRIVER_SOFTWARE

Software driver channel. This channel provides communication with a driver that implements content protection mechanisms in software.


### -field D3D11_1DDI_AUTHENTICATED_CHANNEL_DRIVER_HARDWARE

Hardware driver channel. This channel provides communication with a driver that implements content protection mechanisms in the GPU hardware.


## -remarks
