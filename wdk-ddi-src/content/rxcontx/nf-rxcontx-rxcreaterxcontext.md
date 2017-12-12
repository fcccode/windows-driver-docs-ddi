---
UID: NF.rxcontx.RxCreateRxContext
title: RxCreateRxContext function
author: windows-driver-content
description: RxCreateRxContext allocates a new RX_CONTEXT structure and initializes the data structure.
old-location: ifsk\rxcreaterxcontext.htm
old-project: ifsk
ms.assetid: ff39aebb-03c0-4ba4-844a-417579ed2bbf
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: RxCreateRxContext
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: rxcontx.h
req.include-header: Rxprocs.h  rxcontx.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxCreateRxContext
req.alt-loc: rxcontx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
req.product: Windows 10 or later.
---

# RxCreateRxContext function



## -description
<b>RxCreateRxContext</b> allocates a new RX_CONTEXT structure and initializes the data structure. 



## -syntax

````
PRX_CONTEXT RxCreateRxContext(
  _In_opt_ PIRP                 Irp,
  _In_     PRDBSS_DEVICE_OBJECT RxDeviceObject,
  _In_     ULONG                InitialContextFlags
);
````


## -parameters

### -param Irp [in, optional]

A pointer to the IRP to be encapsulated by this RX_CONTEXT structure.


### -param RxDeviceObject [in]

A pointer to the device object to which this RX_CONTEXT and IRP apply.


### -param InitialContextFlags [in]

The set of initial values for the <b>Flags</b> member of the RX_CONTEXT data structure to be stored in the RX_CONTEXT structure. These initial values can be any combination of the following enumerations:




### -param RX_CONTEXT_FLAG_WAIT 

When this value is set, the IRP should be not be posted for later execution by the file system process, but should be waited on to complete.


### -param RX_CONTEXT_FLAG_MUST_SUCCEED

When this value is set, the operation must succeed. This value is not currently used by RDBSS, but it may be used by network mini-redirector drivers. 


### -param RX_CONTEXT_FLAG_MUST_SUCCEED_NONBLOCKING

When this value is set, the operation must succeed for non-blocking operations. This value is not currently used by RDBSS, but it may be used by network mini-redirector drivers. 

</dd>
</dl>

## -returns
<b>RxCreateRxContext</b> returns a pointer to an allocated RX_CONTEXT data structure on success or a <b>NULL</b> pointer on failure. 


## -remarks
<b>RxCreateRxContext</b> calls <a href="ifsk.rxinitializecontext">RxInitializeContext</a> to initialize the newly created RX_CONTEXT structure before returning. 

<b>RxCreateRxContext</b> allocates non-paged pool memory when creating a new RX_CONTEXT data structure and sets the following value in the Flags member of the RX_CONTEXT:



When this value is set, the RX_CONTEXT structure was allocated from non-paged pool memory.


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Rxcontx.h (include Rxprocs.h and rxcontx.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
&lt;= APC_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.rxcompleterequest">RxCompleteRequest</a>
</dt>
<dt>
<a href="ifsk.rxcompleterequest_real">RxCompleteRequest_Real</a>
</dt>
<dt>
<a href="ifsk.rxdereference">RxDereference</a>
</dt>
<dt>
<a href="ifsk.rxdereferenceanddeleterxcontext_real">RxDereferenceAndDeleteRxContext_Real</a>
</dt>
<dt>
<a href="ifsk.rxinitializecontext">RxInitializeContext</a>
</dt>
<dt>
<a href="ifsk.rxpreparecontextforreuse">RxPrepareContextForReuse</a>
</dt>
<dt>
<a href="ifsk.rxresumeblockedoperations_serially">RxResumeBlockedOperations_Serially</a>
</dt>
<dt>
<a href="ifsk.__rxsynchronizeblockingoperations">__RxSynchronizeBlockingOperations</a>
</dt>
<dt>
<a href="ifsk.__rxsynchronizeblockingoperationsmaybedroppingfcblock">__RxSynchronizeBlockingOperationsMaybeDroppingFcbLock</a>
</dt>
<dt>
<a href="ifsk.rx_context">RX_CONTEXT</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxCreateRxContext function%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
