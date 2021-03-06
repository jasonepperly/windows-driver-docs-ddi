---
UID: NF:ks.KsQueueWorkItem
title: KsQueueWorkItem function
author: windows-driver-content
description: The KsQueueWorkItem function queues the specified work item with a worker previous created by the KsRegisterWorker function.
old-location: stream\ksqueueworkitem.htm
old-project: stream
ms.assetid: a700979e-aee4-4bce-8f98-b44b864fbb43
ms.author: windowsdriverdev
ms.date: 1/9/2018
ms.keywords: KsQueueWorkItem
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsQueueWorkItem
req.alt-loc: Ks.lib,Ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: 
req.typenames: 
---

# KsQueueWorkItem function



## -description
The <b>KsQueueWorkItem</b> function queues the specified work item with a worker previous created by the <a href="..\ks\nf-ks-ksregisterworker.md">KsRegisterWorker</a> function.



## -syntax

````
NTSTATUS KsQueueWorkItem(
  _In_ PKSWORKER        Worker,
  _In_ PWORK_QUEUE_ITEM WorkItem
);
````


## -parameters

### -param Worker [in]

Specifies the previously allocated worker.


### -param WorkItem [in]

Specifies the initialized work item to queue. This work item is only associated with the worker as long as the worker is on a queue. The work item must have been initialized by <a href="..\wdm\nf-wdm-ioallocateworkitem.md">IoAllocateWorkItem</a>.


## -returns
The <b>KsQueueWorkItem</b> function returns STATUS_SUCCESS if the work item was queued, or if unsuccessful the function returns an error when attempting to create a new worker if no threads are currently available.


## -remarks
The worker can only be on a queue in one place, so subsequent queuing of the worker must wait until the work item has begun executing. This function may be called at <b>DISPATCH_LEVEL</b>.</p>