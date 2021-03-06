---
UID: NS:ntddndis._NDIS_INTERRUPT_MODERATION_PARAMETERS
title: _NDIS_INTERRUPT_MODERATION_PARAMETERS
author: windows-driver-content
description: The NDIS_INTERRUPT_MODERATION_PARAMETERS structure defines interrupt parameters for the OID_GEN_INTERRUPT_MODERATION OID.
old-location: netvista\ndis_interrupt_moderation_parameters.htm
old-project: netvista
ms.assetid: e2270dbc-0bc3-4bef-9e11-26006d8f0d71
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: _NDIS_INTERRUPT_MODERATION_PARAMETERS, *PNDIS_INTERRUPT_MODERATION_PARAMETERS, NDIS_INTERRUPT_MODERATION_PARAMETERS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: ntddndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_INTERRUPT_MODERATION_PARAMETERS
req.alt-loc: ntddndis.h
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
req.typenames: *PNDIS_INTERRUPT_MODERATION_PARAMETERS, NDIS_INTERRUPT_MODERATION_PARAMETERS
---

# _NDIS_INTERRUPT_MODERATION_PARAMETERS structure



## -description
The NDIS_INTERRUPT_MODERATION_PARAMETERS structure defines interrupt parameters for the 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff569590">OID_GEN_INTERRUPT_MODERATION</a> OID.
  
  



## -syntax

````
typedef struct _NDIS_INTERRUPT_MODERATION_PARAMETERS {
  NDIS_OBJECT_HEADER        Header;
  ULONG                     Flags;
  NDIS_INTERRUPT_MODERATION InterruptModeration;
} NDIS_INTERRUPT_MODERATION_PARAMETERS, *PNDIS_INTERRUPT_MODERATION_PARAMETERS;
````


## -struct-fields

### -field Header

The 
     <a href="..\ntddndis\ns-ntddndis-_ndis_object_header.md">NDIS_OBJECT_HEADER</a> structure for the
     NDIS_INTERRUPT_MODERATION_PARAMETERS structure. Set the 
     <b>Type</b> member of the structure that 
     <b>Header</b> specifies to NDIS_OBJECT_TYPE_DEFAULT, the 
     <b>Revision</b> member to NDIS_INTERRUPT_MODERATION_PARAMETERS_REVISION_1, and the 
     <b>Size</b> member to NDIS_SIZEOF_INTERRUPT_MODERATION_PARAMETERS_REVISION_1.


### -field Flags

A bitwise OR of the following flags:
     




### -field NDIS_INTERRUPT_MODERATION_CHANGE_NEEDS_RESET

A network interface card (NIC) must have a hardware reset to enable or disable interrupt
       moderation.


### -field NDIS_INTERRUPT_MODERATION_CHANGE_NEEDS_REINITIALIZE

A miniport driver must complete a halt and reinitialize cycle to enable or disable interrupt
       moderation. If this flag is enabled, there is also a hardware reset.

</dd>
</dl>

### -field InterruptModeration

An NDIS_INTERRUPT_MODERATION-typed value that indicates or specifies the current interrupt
     moderation status.
     

The following values are supported:




### -field NdisInterruptModerationUnknown

In an OID query, this value indicates that the miniport driver cannot determine whether
       interrupt moderation is enabled or disabled on a NIC. This value is invalid for a set request.


### -field NdisInterruptModerationNotSupported

In an OID query, this value indicates that the NIC or its miniport driver does not support
       interrupt moderation. This value is invalid for a set request.


### -field NdisInterruptModerationEnabled

In an OID query, this value indicates that interrupt moderation is enabled on the NIC. In an OID
       set, 
       <b>NdisInterruptModerationEnabled</b> indicates that interrupt moderation should be enabled on the
       NIC.


### -field NdisInterruptModerationDisabled

In an OID query, this value indicates that interrupt moderation is disabled on the NIC. In an
       OID set, 
       <b>NdisInterruptModerationDisabled</b> indicates that interrupt moderation should be disabled on the
       NIC.

</dd>
</dl>

## -remarks
The NDIS_INTERRUPT_MODERATION_PARAMETERS structure defines interrupt parameters for the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff569590">OID_GEN_INTERRUPT_MODERATION</a> OID
    query and set operations. Only the 
    <b>NdisInterruptModerationEnabled</b> and 
    <b>NdisInterruptModerationDisabled</b> values for the 
    <b>InterruptModeration</b> member apply to set operations.


## -see-also
<dl>
<dt>
<a href="..\ntddndis\ns-ntddndis-_ndis_object_header.md">NDIS_OBJECT_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff569590">OID_GEN_INTERRUPT_MODERATION</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_INTERRUPT_MODERATION_PARAMETERS structure%20 RELEASE:%20(1/11/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

