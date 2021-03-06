---
UID: NE:dxva._DXVA_DestinationFlags
title: _DXVA_DestinationFlags
author: windows-driver-content
description: The DXVA_DestinationFlags enumeration type contains a collection of flags that identify changes in the current destination surface from the previous destination surface.
old-location: display\dxva_destinationflags.htm
old-project: display
ms.assetid: 842c6ece-5304-428c-afbe-2990d239f38a
ms.author: windowsdriverdev
ms.date: 12/29/2017
ms.keywords: _DXVA_DestinationFlags, DXVA_DestinationFlags
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: enum
req.header: dxva.h
req.include-header: Dxva.h
req.target-type: Windows
req.target-min-winverclnt: This enumeration type applies only to Windows Server 2003 with SP1 and later, and Windows XP with SP2 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXVA_DestinationFlags
req.alt-loc: dxva.h
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
req.typenames: DXVA_DestinationFlags
---

# _DXVA_DestinationFlags enumeration



## -description
The DXVA_DestinationFlags enumeration type contains a collection of flags that identify changes in the current destination surface from the previous destination surface.



## -syntax

````
typedef enum _DXVA_DestinationFlags { 
  DXVA_DestinationFlagMask                 = DXVABit(3)|DXVABit(2)|DXVABit(1)|DXVABit(0),
  DXVA_DestinationFlag_Background_Changed  = 0x0001,
  DXVA_DestinationFlag_TargetRect_Changed  = 0x0002,
  DXVA_DestinationFlag_ColorData_Changed   = 0x0004,
  DXVA_DestinationFlag_Alpha_Changed       = 0x0008
} DXVA_DestinationFlags;
````


## -enum-fields

### -field DXVA_DestinationFlagMask

Specifies the destination-flag mask, which consists of the first 4 bits of a DWORD.


### -field DXVA_DestinationFlag_Background_Changed

Indicates that the background color of the destination surface changed. 


### -field DXVA_DestinationFlag_TargetRect_Changed

Indicates that the target rectangle of the destination surface changed. 


### -field DXVA_DestinationFlag_ColorData_Changed

Indicates that format information for the destination surface changed. 



### -field DXVA_DestinationFlag_Alpha_Changed

Indicates that the planar alpha value for the destination surface changed.


## -remarks


## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/12a0e467-54f8-4cca-8ec0-aa8d04480ab6">DeinterlaceBltEx</a>
</dt>
<dt>
<a href="..\dxva\ns-dxva-_dxva_deinterlacebltex.md">DXVA_DeinterlaceBltEx</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXVA_DestinationFlags enumeration%20 RELEASE:%20(12/29/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

