---
UID: NF:ndis.NdisIfRegisterInterface
title: NdisIfRegisterInterface function
author: windows-driver-content
description: The NdisIfRegisterInterface function registers an NDIS network interface.
old-location: netvista\ndisifregisterinterface.htm
old-project: netvista
ms.assetid: d0b0ada7-afb1-4cb7-ada6-7c5c7abe7d19
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: NdisIfRegisterInterface
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisIfRegisterInterface
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Interfaces_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: PASSIVE_LEVEL
req.typenames: NDIS_SHARED_MEMORY_USAGE, *PNDIS_SHARED_MEMORY_USAGE
---

# NdisIfRegisterInterface function



## -description
The 
  <b>NdisIfRegisterInterface</b> function registers an NDIS network interface.



## -syntax

````
NDIS_STATUS NdisIfRegisterInterface(
  _In_  NDIS_HANDLE         NdisProviderHandle,
  _In_  NET_LUID            NetLuid,
  _In_  NDIS_HANDLE         ProviderIfContext,
  _In_  PNET_IF_INFORMATION pIfInfo,
  _Out_ PNET_IFINDEX        pIfIndex
);
````


## -parameters

### -param NdisProviderHandle [in]

A handle that identifies the network interface provider that is registering the interface. The
     caller obtained this handle from a previous call to the 
     <a href="..\ndis\nf-ndis-ndisifregisterprovider.md">
     NdisIfRegisterProvider</a> function.


### -param NetLuid [in]

The caller-supplied 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568747">NET_LUID</a> value that is associated with the
     interface. The interface provider used the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff565890">NDIS_MAKE_NET_LUID</a> macro to create this
     NET_LUID value. The interface provider should recover the NET_LUID value from persistent storage after
     the computer restarts and provide the same NET_LUID value each time it registers a particular
     interface.


### -param ProviderIfContext [in]

A handle to a caller-allocated context area that is associated with the interface. NDIS passes
     this handle to the callback functions that the caller registered with 
     <b>NdisIfRegisterProvider</b>.


### -param pIfInfo [in]

A pointer to a caller-allocated 
     <a href="..\ndis\ns-ndis-_net_if_information.md">NET_IF_INFORMATION</a> structure that
     provides information about the interface. This structure contains information that remains constant
     while the interface exists.


### -param pIfIndex [out]

A pointer to a caller-supplied interface index variable. If NDIS successfully registers an
     interface, NDIS allocates an interface index for that interface and sets the value at 
     <i>pIfIndex</i> . The interface index is a 24-bit value that is unique on the local computer. NDIS might
     not return the same interface index every time a provider registers an interface with the same NET_LUID
     value . The interface index value zero is reserved, and NDIS does not assign it to any interface. Do not
     confuse the interface index with a NET_LUID index.


## -returns
<b>NdisIfRegisterInterface</b> returns one of the following status values:
<dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl>The operation completed successfully.
<dl>
<dt><b>NDIS_STATUS_RESOURCES</b></dt>
</dl>The operation failed because of insufficient resources.
<dl>
<dt><b>NDIS_STATUS_INVALID_PARAMETER</b></dt>
</dl><b>NdisIfRegisterInterface</b> failed because some of the input parameters are invalid.
<dl>
<dt><b>NDIS_STATUS_DUPLICATE_OBJECTID</b></dt>
</dl><b>NdisIfRegisterInterface</b> failed because there is already an interface registered with the same
       NET_LUID value that the 
       <i>NetLuid</i> parameter specified.

 


## -remarks
NDIS interface providers call the 
    <b>NdisIfRegisterInterface</b> function to register a network interface. A call to this function does not
    imply that the interface is active.

Whenever a computer restarts, NDIS starts with an empty list of registered network interfaces. An
    interface provider calls the 
    <b>NdisIfRegisterInterface</b> function whenever an interface is started (or detected) and the interface's
    
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568747">NET_LUID</a> is known.

The method for detecting or starting an interface is application dependent. For example, if an LBFO
    MUX intermediate driver is an interface provider, that driver might register an internal interface when
    NDIS calls the driver's 
    <a href="..\ndis\nc-ndis-protocol_bind_adapter_ex.md">ProtocolBindAdapterEx</a> function
    for the first underlying miniport adapter.

An interface provider can put information about an interface in persistent storage and restore the
    interface as required for the particular application. For example, the provider can store additional
    information about the interface with the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568747">NET_LUID</a> and it can reregister the interface after
    the computer restarts.

If 
    <b>NdisIfRegisterInterface</b> is successful, NDIS adds the interface to the list of known interfaces and
    allocates a new interface index for this interface. Interface providers should register both enabled and
    disabled interfaces, wherever possible. All enabled interfaces 
    must be registered.

NDIS might not return the same interface index every time a provider registers an interface with the
    same NET_LUID value. For example, NDIS does not necessarily assign the same interface index when an
    interface is reregistered after a computer restarts or when the interface is deregistered and
    re-registered. The interface index value zero is reserved, and NDIS does not assign it to any
    interface.

To indicate that an interface should be removed from the list of known interfaces on the computer, an
    interface provider calls the 
    <a href="..\ndis\nf-ndis-ndisifderegisterinterface.md">
    NdisIfDeregisterInterface</a> function, for example, because the interface has been uninstalled. .


## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565890">NDIS_MAKE_NET_LUID</a>
</dt>
<dt>
<a href="..\ndis\nf-ndis-ndisifderegisterinterface.md">NdisIfDeregisterInterface</a>
</dt>
<dt>
<a href="..\ndis\nf-ndis-ndisifregisterprovider.md">NdisIfRegisterProvider</a>
</dt>
<dt>
<a href="..\ndis\ns-ndis-_net_if_information.md">NET_IF_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568747">NET_LUID</a>
</dt>
<dt>
<a href="..\ndis\nc-ndis-protocol_bind_adapter_ex.md">ProtocolBindAdapterEx</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisIfRegisterInterface function%20 RELEASE:%20(1/11/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

