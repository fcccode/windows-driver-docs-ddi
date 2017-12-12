---
UID: NF.rxprocs.RxCompleteRequest_Real
title: RxCompleteRequest_Real function
author: windows-driver-content
description: RxCompleteRequest_Real completes the IRP request associated with an RX_CONTEXT structure.
old-location: ifsk\rxcompleterequest_real.htm
old-project: ifsk
ms.assetid: 54d8fab2-bde3-4b8a-8542-075c5e30afbb
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: RxCompleteRequest_Real
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: rxprocs.h
req.include-header: Rxprocs.h, Rxcontx.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxCompleteRequest_Real
req.alt-loc: rxprocs.h
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

# RxCompleteRequest_Real function



## -description
<b>RxCompleteRequest_Real</b> completes the IRP request associated with an RX_CONTEXT structure.



## -syntax

````
VOID RxCompleteRequest_Real(
  _In_ PRX_CONTEXT RxContext,
  _In_ PIRP        Irp,
  _In_ NTSTATUS    Status
);
````


## -parameters

### -param RxContext [in]

A pointer to the RX_CONTEXT structure associated with the IRP to complete.


### -param Irp [in]

A pointer to the IRP to complete.


### -param Status [in]

The status value to return when the IRP request is complete. This is the value that will be stored in the <b>IoStatus.Status</b> member of the associated IRP on completion.


## -returns
None


## -remarks
The <b>RxCompleteRequest_Real</b> routine is not normally called by network mini-redirector drivers directly. RDBSS calls this routine internally to complete an I/O request packet. 

If a <b>NULL</b> value is passed in for <i>Irp</i>, then <b>RxCompleteRequest_Real</b> will log this as an error in checked builds. If a non-<b>NULL</b> value is passed in for <i>RxContex</i>t, then <b>RxCompleteRequest_Real</b> internally calls <b>RxDereferenceAndDeleteRxContext</b> with the passed in <i>RxContext</i> parameter to dereference the RX_CONTEXT structure. 


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
<dt>Rxprocs.h (include Rxprocs.h or Rxcontx.h)</dt>
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
<a href="ifsk.rxcreaterxcontext">RxCreateRxContext</a>
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
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxCompleteRequest_Real function%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
