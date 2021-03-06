---
UID: NS:d3d10umddi.D3D11_1DDI_VIDEO_COLOR
title: D3D11_1DDI_VIDEO_COLOR
author: windows-driver-content
description: Defines a color value for Microsoft Direct3D 11 video.
old-location: display\d3d11_1ddi_video_color.htm
old-project: display
ms.assetid: 200ca1d5-cbfd-4ad8-aa41-8238ea7ea5cf
ms.author: windowsdriverdev
ms.date: 12/29/2017
ms.keywords: D3D11_1DDI_VIDEO_COLOR, D3D11_1DDI_VIDEO_COLOR
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D11_1DDI_VIDEO_COLOR
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
req.typenames: D3D11_1DDI_VIDEO_COLOR
---

# D3D11_1DDI_VIDEO_COLOR structure



## -description
Defines a color value for Microsoft Direct3D 11 video.



## -syntax

````
typedef struct D3D11_1DDI_VIDEO_COLOR {
  union {
    D3D11_1DDI_VIDEO_COLOR_YCbCrA YCbCr;
    D3D11_1DDI_VIDEO_COLOR_RGBA   RGBA;
  };
} D3D11_1DDI_VIDEO_COLOR;
````


## -struct-fields

### -field YCbCr

A <a href="..\d3d10umddi\ns-d3d10umddi-d3d11_1ddi_video_color_ycbcra.md">D3D11_1DDI_VIDEO_COLOR_YCbCrA</a> structure that contains a YCbCr color value.


### -field RGBA

A <a href="..\d3d10umddi\ns-d3d10umddi-d3d11_1ddi_video_color_rgba.md">D3D11_1DDI_VIDEO_COLOR_RGBA</a> structure that contains an RGB color value.


## -remarks
The anonymous union can represent both RGB and YCbCr colors. The interpretation of the union depends on the context.


## -see-also
<dl>
<dt>
<a href="..\d3d10umddi\ns-d3d10umddi-d3d11_1ddi_video_color_rgba.md">D3D11_1DDI_VIDEO_COLOR_RGBA</a>
</dt>
<dt>
<a href="..\d3d10umddi\ns-d3d10umddi-d3d11_1ddi_video_color_ycbcra.md">D3D11_1DDI_VIDEO_COLOR_YCbCrA</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3D11_1DDI_VIDEO_COLOR structure%20 RELEASE:%20(12/29/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

