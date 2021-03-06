---
UID: NE:wwan._WWAN_PIN_STATE
title: _WWAN_PIN_STATE
author: windows-driver-content
description: The WWAN_PIN_STATE enumeration describes whether the MB device or Subscriber Identity Module (SIM card) requires the user to enter a Personal Identification Number (PIN) to proceed to the next state.
old-location: netvista\wwan_pin_state.htm
old-project: netvista
ms.assetid: e538f920-bf9e-484b-acea-f979bb952299
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: _WWAN_PIN_STATE, WWAN_PIN_STATE, *PWWAN_PIN_STATE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: enum
req.header: wwan.h
req.include-header: Wwan.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WWAN_PIN_STATE
req.alt-loc: wwan.h
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
req.typenames: WWAN_PIN_STATE, *PWWAN_PIN_STATE
req.product: Windows 10 or later.
---

# _WWAN_PIN_STATE enumeration



## -description
The WWAN_PIN_STATE enumeration describes whether the MB device or Subscriber Identity Module (SIM
  card) requires the user to enter a Personal Identification Number (PIN) to proceed to the next
  state.



## -syntax

````
typedef enum _WWAN_PIN_STATE { 
  WwanPinStateNone   = 0,
  WwanPinStateEnter,
  WwanPinStateMax
} WWAN_PIN_STATE, *PWWAN_PIN_STATE;
````


## -enum-fields

### -field WwanPinStateNone

The device does not require a PIN.


### -field WwanPinStateEnter

The device requires the user to enter a PIN.


### -field WwanPinStateMax

The total number of supported PIN states.


## -remarks


## -see-also
<dl>
<dt>
<a href="..\wwan\ns-wwan-_wwan_pin_info.md">WWAN_PIN_INFO</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WWAN_PIN_STATE enumeration%20 RELEASE:%20(1/11/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

