---
UID: NF:wdfinterrupt.WdfInterruptSetExtendedPolicy
title: WdfInterruptSetExtendedPolicy function
author: windows-driver-content
description: The WdfInterruptSetExtendedPolicy method specifies the interrupt priority, processor affinity, affinity policy, and processor group for a specified interrupt.
old-location: wdf\wdfinterruptsetextendedpolicy.htm
old-project: wdf
ms.assetid: 043c15dc-ebd7-4d91-8f65-d89d6064cc7c
ms.author: windowsdriverdev
ms.date: 1/11/2018
ms.keywords: WdfInterruptSetExtendedPolicy
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfinterrupt.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.9
req.umdf-ver: 2.0
req.alt-api: WdfInterruptSetExtendedPolicy
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); WUDFx02000.dll (UMDF)
req.dll: 
req.irql: <=DISPATCH_LEVEL
req.typenames: WDF_INTERRUPT_PRIORITY, *PWDF_INTERRUPT_PRIORITY
req.product: Windows 10 or later.
---

# WdfInterruptSetExtendedPolicy function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]

The <b>WdfInterruptSetExtendedPolicy</b> method specifies the interrupt priority, processor affinity, affinity policy, and processor group for a specified interrupt.



## -syntax

````
VOID WdfInterruptSetExtendedPolicy(
  _In_ WDFINTERRUPT                   Interrupt,
  _In_ PWDF_INTERRUPT_EXTENDED_POLICY PolicyAndGroup
);
````


## -parameters

### -param Interrupt [in]

A handle to a framework interrupt object.


### -param PolicyAndGroup [in]

A pointer to a <a href="..\wudfinterrupt\ns-wudfinterrupt-_wdf_interrupt_extended_policy.md">WDF_INTERRUPT_EXTENDED_POLICY</a> structure that the caller allocates and initializes.


## -returns
None.

A bug check occurs if the driver supplies an invalid object handle.




## -remarks
Windows Vista and later versions of the operating system allow drivers to use the <a href="..\wdfinterrupt\nf-wdfinterrupt-wdfinterruptsetpolicy.md">WdfInterruptSetPolicy</a> method to specify an interrupt's priority, processor affinity, and affinity policy. In addition, versions 1.9 and later of KMDF allow drivers to use the <b>WdfInterruptSetExtendedPolicy</b> method to specify an interrupt's priority, processor affinity, affinity policy, and processor group.

For information about how to use the registry to override the values that <b>WdfInterruptSetExtendedPolicy</b> sets, see <a href="https://msdn.microsoft.com/e36a52d0-3a94-4017-b4a1-0b41f737523c">Interrupt Affinity and Priority</a>.

If a driver is running on an operating system version that is earlier than Windows 7, the framework ignores the value that the driver specifies for the processor group number when it calls <b>WdfInterruptSetExtendedPolicy</b>.

If a driver is running on an operating system version that is earlier than Windows Vista, the framework ignores all values that the driver specifies when it calls <a href="..\wdfinterrupt\nf-wdfinterrupt-wdfinterruptsetpolicy.md">WdfInterruptSetPolicy</a> or <b>WdfInterruptSetExtendedPolicy</b>.

For more information about registry values and INF sections that specify an interrupt's priority, processor affinity, and affinity policy, see <a href="https://msdn.microsoft.com/e36a52d0-3a94-4017-b4a1-0b41f737523c">Interrupt Affinity and Priority</a>.

If a driver calls <b>WdfInterruptSetExtendedPolicy</b>, it typically does so in its <a href="..\wdfdriver\nc-wdfdriver-evt_wdf_driver_device_add.md">EvtDriverDeviceAdd</a> callback function, after calling <a href="..\wdfinterrupt\nf-wdfinterrupt-wdfinterruptcreate.md">WdfInterruptCreate</a>.

If your driver creates interrupts in <a href="..\wdfdevice\nc-wdfdevice-evt_wdf_device_prepare_hardware.md">EvtDevicePrepareHardware</a>, do not use <a href="..\wdfinterrupt\nf-wdfinterrupt-wdfinterruptsetpolicy.md">WdfInterruptSetPolicy</a> or <b>WdfInterruptSetExtendedPolicy</b>. Instead, you can instead apply policy in <a href="https://msdn.microsoft.com/7d9b38b5-989d-45a3-8771-57a8d1f98725">EvtDeviceFilterAddResourceRequirements</a>, by directly manipulating the interrupt resource requirement that this callback function receives in its <i>IoResourceRequirementsList</i> parameter.

For more information about handling interrupts in framework-based drivers, see <a href="https://msdn.microsoft.com/08460510-6e5f-4c02-8086-9caa9b4b4c2d">Handling Hardware Interrupts</a>.

The following code example calls <a href="..\wudfinterrupt\nf-wudfinterrupt-wdf_interrupt_extended_policy_init.md">WDF_INTERRUPT_EXTENDED_POLICY_INIT</a> to initialize a <a href="..\wudfinterrupt\ns-wudfinterrupt-_wdf_interrupt_extended_policy.md">WDF_INTERRUPT_EXTENDED_POLICY</a> structure; sets values for the policy, priority, and target processor set; and calls <b>WdfInterruptSetExtendedPolicy</b>. The example sets normal priority for the interrupt and assigns the interrupt to processor 0 in processor group 2. 


## -see-also
<dl>
<dt>
<a href="..\wdfinterrupt\nf-wdfinterrupt-wdfinterruptsetpolicy.md">WdfInterruptSetPolicy</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfInterruptSetExtendedPolicy method%20 RELEASE:%20(1/11/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

