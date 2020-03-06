---
UID: NE:dispmprt._DXGK_DIAG_DISPLAY_SCANOUT_STATE
title: DXGK_DIAG_DISPLAY_SCANOUT_STATE
ms.date: 03/24/2020
ms.topic: language-reference
targetos: Windows
description: DXGK_DIAG_DISPLAY_SCANOUT_STATE indicates whether the display pipeline is currently fetching and scanning out pixels actively to the given target/display.
tech.root: display
req.construct-type: enumeration
req.ddi-compliance: 
req.header: dispmprt.h
req.include-header: 
req.kmdf-ver: 
req.max-support: 
req.target-min-winverclnt: Windows 10, version 2004
req.target-min-winversvr: 
req.target-type: 
req.typenames: 
req.umdf-ver: 
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - dispmprt.h
api_name:
 - _DXGK_DIAG_DISPLAY_SCANOUT_STATE
 - DXGK_DIAG_DISPLAY_SCANOUT_STATE
f1_keywords:
 - dispmprt/_DXGK_DIAG_DISPLAY_SCANOUT_STATE
 - dispmprt/DXGK_DIAG_DISPLAY_SCANOUT_STATE
dev_langs:
 - c++
---

# DXGK_DIAG_DISPLAY_SCANOUT_STATE enumeration

## -description

**DXGK_DIAG_DISPLAY_SCANOUT_STATE** indicates whether the display pipeline is currently fetching and scanning out pixels actively to the given target/display.

## -enum-fields

### -field DXGK_DIAG_DISPLAY_SCANOUT_STATE_UNINITIALIZED

Reserved for OS use during diagnostic initialization.

### -field DXGK_DIAG_DISPLAY_SCANOUT_DISABLED

The display hardware is currently not scanning out any pixels to the vidpntarget/monitor.

### -field DXGK_DIAG_DISPLAY_SCANOUT_ACTIVE

The display hardware is actively scanning out pixels to the vidpntarget/monitor.

### -field DXGK_DIAG_DISPLAY_SCANOUT_ACTIVE_BLACK

The display hardware is actively scanning out a black pixel stream to the vidpntarget/monitor but not from the frame buffer. Instead, the pixels are being internally generated by the driver/hardware to simulate monitor visibility OFF for scenarios such as [**DdiSetVidPnSourceVisibility**](https://docs.microsoft.com/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_setvidpnsourcevisibility).

## -remarks

The **DXGK_DIAG_DISPLAY_SCANOUT_STATE** enumeration is a member of the [**DXGK_DISPLAYSTATE_INTRUSIVE**](ns-dispmprt-dxgk_displaystate_intrusive.md) structure. It is used while gathering display diagnostic information via calls to [**DxgkDdiGetDisplayStateIntrusive**](nc-dispmprt-dxgkddi_getdisplaystateintrusive.md).

## -see-also

[**DXGK_DISPLAYSTATE_INTRUSIVE**](ns-dispmprt-dxgk_displaystate_intrusive.md)

[**DXGKARG_GETDISPLAYSTATEINTRUSIVE**](ns-dispmprt-dxgkarg_getdisplaystateintrusive.md)

[**DxgkDdiGetDisplayStateIntrusive**](nc-dispmprt-dxgkddi_getdisplaystateintrusive.md)