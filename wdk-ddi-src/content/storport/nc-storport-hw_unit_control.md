---
UID: NC:storport.HW_UNIT_CONTROL
title: HW_UNIT_CONTROL
author: windows-driver-content
description: A miniport driver's HwStorUnitControl routine is called to perform synchronous operations to control the state of storage unit device. The miniport driver is notified to start a unit or handle a power state transition for a unit device.
old-location: storage\hwstorunitcontrol.htm
old-project: storage
ms.assetid: 33534C7A-C88D-4980-98A7-2B94488D3550
ms.author: windowsdriverdev
ms.date: 1/10/2018
ms.keywords: _STORAGE_DEVICE_UNIQUE_IDENTIFIER, *PSTORAGE_DEVICE_UNIQUE_IDENTIFIER, STORAGE_DEVICE_UNIQUE_IDENTIFIER
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HwStorUnitControl
req.alt-loc: Storport.h
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
req.typenames: *PSTORAGE_DEVICE_UNIQUE_IDENTIFIER, STORAGE_DEVICE_UNIQUE_IDENTIFIER
req.product: Windows 10 or later.
---

# HW_UNIT_CONTROL callback



## -description
A miniport driver's <b>HwStorUnitControl</b> routine is called to perform synchronous operations to control the state of storage unit device. The miniport driver is notified to  start a unit or handle a power state transition for a unit device.



## -prototype

````
HW_UNIT_CONTROL HwStorUnitControl;

SCSI_UNIT_CONTROL_STATUS HwStorUnitControl(
  _In_ PVOID                     DeviceExtension,
  _In_ SCSI_ADAPTER_CONTROL_TYPE ControlType,
  _In_ PVOID                     Parameters
)
{ ... }
````


## -parameters

### -param DeviceExtension [in]

A pointer to the miniport driver's per-unit storage area. 


### -param ControlType [in]

Specifies  an unit control operation. Each control type initiates an action by the miniport driver. The following are the  control types and their meanings.

<table>
<tr>
<th>Control Type</th>
<th>Meaning</th>
<th>IRQL</th>
<th>Spinlock</th>
</tr>
<tr>
<td>
<b>ScsiQuerySupportedUnitControlTypes</b>

</td>
<td>
Reports the unit-control operations implemented by the miniport driver. The Storport driver calls <b>HwStorUnitControl</b> with this control type after the HBA has been initialized but before the first I/O. The miniport driver fills in the SCSI_SUPPORTED_CONTROL_TYPE_LIST structure at <i>Parameters</i> with the operations it supports. After <b>HwStorUnitControl</b> returns from this call, the Storport driver calls the miniport driver's <b>HwStorUnitControl</b> only for supported operations.

</td>
<td>
PASSIVE_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitUsage</b>

</td>
<td>
Notifies the miniport if  the logical unit is used for any supported usage types. Storport driver will call  <b>HwStorUnitControl</b>  separately for each usage type supported.

</td>
<td>
PASSIVE_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitStart</b>

</td>
<td>
Notifies the miniport to start a unit device.

</td>
<td>
PASSIVE_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitPower</b>

</td>
<td>
Reports the unit power on or power off states. If the miniport supports this control type, it will not receive a storage request block with SRB_FUNCTION_POWER.

</td>
<td>
DISPATCH_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerInfo</b>

</td>
<td>
Notifies the miniport if idle power management is enabled or disabled on the unit component. The miniport should call <a href="..\storport\nf-storport-storportinitializepofxpower.md">StorPortInitializePoFxPower</a> within this unit control if idle power management was enabled and it if supports runtime power management for the unit device.

</td>
<td>
PASSIVE_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerRequired</b>

</td>
<td>
Notifies the miniport whether power is required or not for the unit component.

</td>
<td>
DISPATCH_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerActive</b>

</td>
<td>
Notifies the miniport that the unit component is either active or idle.

</td>
<td>
DISPATCH_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerSetFState</b>

</td>
<td>
Notifies the miniport to set the unit component to the given functional power state (F-state). The miniport must support this control type if is specifies more than one F-state in the call to <a href="..\storport\nf-storport-storportinitializepofxpower.md">StorPortInitializePoFxPower</a>.

</td>
<td>
DISPATCH_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerControl</b>

</td>
<td>
Requests a power engine plug-in (PEP) initiated private power control operation for the miniport to execute for the unit.

</td>
<td>
DISPATCH_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitRemove</b>

</td>
<td>
Notifies the miniport that the unit has been removed.

</td>
<td>
PASSIVE_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitSurpriseRemoval</b>

</td>
<td>
Notifies the miniport that the unit has been surprise-removed.

</td>
<td>
PASSIVE_LEVEL

</td>
<td>
None

</td>
</tr>
<tr>
<td>
<b>ScsiUnitRichDescription</b>

</td>
<td>
The miniport can choose to support this if the device reports a longer vendor ID, model number, or firmware revision than is defined in the SCSI spec.


</td>
<td>
PASSIVE_LEVEL

</td>
<td>
None

</td>
</tr>
</table>
 


### -param Parameters [in]

Contains information related to the <i>ControlType</i>.  

<table>
<tr>
<th>Control Type</th>
<th>Parameters</th>
</tr>
<tr>
<td>
<b>ScsiQuerySupportedUnitControlTypes</b>

</td>
<td>
Caller-allocated SCSI_SUPPORTED_CONTROL_TYPE_LIST structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _SCSI_SUPPORTED_CONTROL_TYPE_LIST { 
    IN ULONG MaxControlType;
    OUT BOOLEAN SupportedTypeList[0];
} SCSI_SUPPORTED_CONTROL_TYPE_LIST, *PSCSI_SUPPORTED_CONTROL_TYPE_LIST;</pre>
</td>
</tr>
</table></span></div>



### -param MaxControlType

Specifies the number of entries in the <b>SupportedTypeList</b> array.


### -param SupportedTypeList

Points to a caller-allocated array of <b>BOOLEAN</b> values that indicate the control types implemented by the miniport driver. The port driver initializes each element to <b>FALSE</b>. 

The miniport driver sets the corresponding array element to <b>TRUE</b> for each operation it supports:



### -param SupportedTypeList[ScsiQuerySupportedControlTypes]
### -param SupportedTypeList[ScsiUnitUsage]
### -param SupportedTypeList[ScsiUnitStart]
### -param SupportedTypeList[ScsiUnitPower]
### -param SupportedTypeList[ScsiUnitPoFxPowerInfo] 
### -param SupportedTypeList[ScsiUnitPoFxPowerRequired]
### -param SupportedTypeList[ScsiUintPoFxPowerActive]
### -param SupportedTypeList[ScsiUnitPoFxPowerSetFState]
### -param SupportedTypeList[ScsiUnitPoFxPowerControl]
### -param SupportedTypeList[ScsiUnitRemove]
### -param SupportedTypeList[ScsiUnitSurpriseRemoval]
### -param SupportedTypeList[ScsiUnitRichDescription]



The miniport driver must not set any element beyond <b>SupportedTypeList</b>[<b>MaxControlType</b> - 1].

</dd>
</dl>
</td>
</tr>
<tr>
<td>
<b>ScsiUnitUsage</b>

</td>
<td>
Caller-allocated STOR_UC_DEVICE_USAGE structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _STOR_UC_DEVICE_USAGE {
    PSTOR_ADDRESS   Address;
    SCSI_UC_DEVICE_USAGE_TYPE   UsageType;
    BOOLEAN InUse;
} STOR_UC_DEVICE_USAGE, *PSTOR_UC_DEVICE_USAGE;
</pre>
</td>
</tr>
</table></span></div>



### -param Address

The device address for the usage notification.


### -param UsageType

The usage type from a PnP  device usage notification.


### -param InUse

<b>TRUE</b> if the unit is used for the type in <b>UsageType</b>. Otherwise, <b>FALSE</b>.

</dd>
</dl>
</td>
</tr>
<tr>
<td>
<b>ScsiUnitStart</b>

</td>
<td>
The  <b>STOR_ADDR_BTL8</b> address of the unit to start.

</td>
</tr>
<tr>
<td>
<b>ScsiUnitPower</b>

</td>
<td>
Caller-allocated STOR_UNIT_CONTROL_POWER structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _STOR_UNIT_CONTROL_POWER {
    PSTOR_ADDRESS               Address;
    STOR_POWER_ACTION           PowerAction;
    STOR_DEVICE_POWER_STATE     PowerState;
} STOR_UNIT_CONTROL_POWER, *PSTOR_UNIT_CONTROL_POWER;
</pre>
</td>
</tr>
</table></span></div>



### -param Address

The device address for the power notification.


### -param PowerAction

The power action indicator. For a runtime power transition, <b>PowerAction</b> set to <b>StorPowerActionNone</b>.


### -param PowerState

The current unit power state. This is either <b>StorPowerDeviceD0</b> or <b>StorPowerDeviceD3</b> for  the power on or power of states respectively.

</dd>
</dl>
</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerInfo</b>

</td>
<td>
Caller-allocated STOR_POFX_UNIT_POWER_INFO structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _STOR_POFX_UNIT_POWER_INFO {
    STOR_POWER_CONTROL_HEADER   Header;
    BOOLEAN                     IdlePowerEnabled;
} STOR_POFX_UNIT_POWER_INFO, *PSTOR_POFX_UNIT_POWER_INFO;
</pre>
</td>
</tr>
</table></span></div>



### -param Header

The power control header structure.


### -param IdlePowerEnabled

<b>TRUE</b> if idle power management is enabled for the unit. Otherwise, <b>FALSE</b>.

</dd>
</dl>
</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerRequired</b>

</td>
<td>
Caller-allocated STOR_POFX_POWER_REQUIRED_CONTEXT structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _STOR_POFX_POWER_REQUIRED_CONTEXT {
    STOR_POWER_CONTROL_HEADER Header;
    BOOLEAN                   PowerRequired;ScsiUnitRichDescription
} STOR_POFX_POWER_REQUIRED_CONTEXT, *PSTOR_POFX_POWER_REQUIRED_CONTEXT;
</pre>
</td>
</tr>
</table></span></div>



### -param Header

The power control header structure.


### -param PowerRequired

<b>TRUE</b> if the unit component requires power. Otherwise, <b>FALSE.</b>

</dd>
</dl>
</td>
</tr>
<tr>
<td>
<b>ScsiUintPoFxPowerActive</b>

</td>
<td>
Caller-allocated STOR_POFX_ACTIVE_CONTEXT structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _STOR_POFX_ACTIVE_CONTEXT {
    STOR_POWER_CONTROL_HEADER   Header;
    ULONG                       ComponentIndex;
    BOOLEAN                     Active;
} STOR_POFX_ACTIVE_CONTEXT, *PSTOR_POFX_ACTIVE_CONTEXT;
</pre>
</td>
</tr>
</table></span></div>



### -param Header

The power control header structure.


### -param ComponentIndex

Index of the device component with the active status. The component index is always 0 for a unit device.


### -param Active

The active status of the component. <b>Active</b> is  set to <b>TRUE</b> if the unit is active. Otherwise, <b>FALSE</b> if idle.

</dd>
</dl>
</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerSetFState</b>

</td>
<td>
Caller-allocated STOR_POFX_FSTATE_CONTEXT structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _STOR_POFX_FSTATE_CONTEXT {
    STOR_POWER_CONTROL_HEADER   Header;
    ULONG                       ComponentIndex;
    ULONG                       FState;
} STOR_POFX_FSTATE_CONTEXT, *PSTOR_POFX_FSTATE_CONTEXT;
</pre>
</td>
</tr>
</table></span></div>



### -param Header

The power control header structure.


### -param ComponentIndex

Index of the device component with the active status. The component index is always 0 for a unit device.


### -param FState

The F-state to set for the unit component.

</dd>
</dl>
</td>
</tr>
<tr>
<td>
<b>ScsiUnitPoFxPowerControl</b>

</td>
<td>
Caller-allocated STOR_POFX_POWER_CONTROL structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _STOR_POFX_POWER_CONTROL {
    STOR_POWER_CONTROL_HEADER   Header;
    LPCGUID                     PowerControlCode;
    SIZE_T                      InBufferSize;
    SIZE_T                      OutBufferSize;
    PVOID                       InBuffer;
    PVOID                       OutBuffer;
    PSIZE_T                     BytesReturned;
} STOR_POFX_POWER_CONTROL, *PSTOR_POFX_POWER_CONTROL;
</pre>
</td>
</tr>
</table></span></div>



### -param Header

The power control header structure.


### -param PowerControlCode

A power control code GUID identifying the private control private control operation to execute for the unit.


### -param InBufferSize

The size, in bytes, of the input buffer at <i>InBuffer</i>.


### -param OutBufferSize

The size, in bytes, of the output buffer at <i>OutBuffer</i>.


### -param InBuffer

The buffer containing input parameters and data for the private power control call.


### -param OutBuffer

The buffer where the resulting output parameters and data are returned for the private power control call.


### -param BytesReturned

The size, in bytes, of the data returned in <i>OutBuffer</i>.

</dd>
</dl>
</td>
</tr>
<tr>
<td>
<b>ScsiUnitRemove</b>

</td>
<td>
The <b>STOR_ADDR_BTL8</b> address of the unit being removed.

</td>
</tr>
<tr>
<td>
<b>ScsiUnitSurpriseRemoval</b>

</td>
<td>
The <b>STOR_ADDR_BTL8</b> address of the unit being surprise-removed.

</td>
</tr>
<tr>
<td>
<b>ScsiUnitRichDescription</b>

</td>
<td>
Caller-allocated <b>STOR_RICH_DEVICE_DESCRIPTION</b> structure.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>#define STOR_RICH_DEVICE_DESCRIPTION_STRUCTURE_VERSION_V2   0x2

typedef struct _STOR_RICH_DEVICE_DESCRIPTION_V2 {

    ULONG   Version;
    ULONG   Size;

    CHAR    VendorId[STOR_VENDOR_ID_LENGTH + 1];
    CHAR    ModelNumber[STOR_MODEL_NUMBER_LENGTH + 1];
    CHAR    FirmwareRevision[STOR_FIRMWARE_REVISION_LENGTH + 1];

    PSTOR_ADDRESS Address;

} STOR_RICH_DEVICE_DESCRIPTION_V2, *PSTOR_RICH_DEVICE_DESCRIPTION_V2;
</pre>
</td>
</tr>
</table></span></div>



### -param Version

The version of the structure.  Should be <i>STOR_RICH_DEVICE_DESCRIPTION_STRUCTURE_VERSION_V2</i>.


### -param Size

The size of the structure.  Should be <i>sizeof(STOR_RICH_DEVICE_DESCRIPTION_V2)</i>.


### -param VendorId

A string representing the device’s vendor ID.  May be an empty string if <i>ModelNumber</i> is provided. The miniport should fill this in.


### -param ModelNumber

A string representing the device’s model.  The miniport should fill this in.


### -param FirmwareRevision

A string representing the device’s currently active firmware revision.  The miniport should fill this in.


### -param Address

The address of the device for which the rich device description is desired.  This is provided by Storport.

</dd>
</dl>
</td>
</tr>
</table>
 

For the structures that contain the STOR_POWER_CONTROL_HEADER header, it has the following definition in <i>storport.h</i>.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _STOR_POWER_CONTROL_HEADER {
    ULONG Version;
    ULONG Size;
    PSTOR_ADDRESS Address;
} STOR_POWER_CONTROL_HEADER, *PSTOR_POWER_CONTROL_HEADER;
</pre>
</td>
</tr>
</table></span></div>



### -param Version

The version of the parent structure.


### -param Size

The size, in bytes, of the parent structure.


### -param Address

The address of the unit the control operation is specified for.

</dd>
</dl>

## -returns
Depending on the control type, <b>HwStorUnitControl</b> returns one of the following SCSI_UNIT_CONTROL_STATUS values:
<dl>
<dt><b>
        ScsiUnitControlSuccess</b></dt>
</dl>The miniport driver completed the requested operation successfully.
<dl>
<dt><b>
        ScsiUnitControlUnsuccessful</b></dt>
</dl>The unit control operation was not successful.

 


## -remarks
The name <b>HwStorUnitControl</b>  is just a placeholder. The actual prototype of this routine is defined in <i>storport.h</i> as follows:


## -see-also
<dl>
<dt>
<a href="..\storport\nc-storport-hw_adapter_control.md">HwStorAdapterControl</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20HW_UNIT_CONTROL routine%20 RELEASE:%20(1/10/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

