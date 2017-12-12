---
UID: NF.wdfdmatransaction.WdfDmaTransactionCreate
title: WdfDmaTransactionCreate function
author: windows-driver-content
description: The WdfDmaTransactionCreate method creates a DMA transaction.
old-location: wdf\wdfdmatransactioncreate.htm
old-project: wdf
ms.assetid: 9470e4a6-eee4-4a73-80b0-3d45f9d79934
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfDmaTransactionCreate
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfdmatransaction.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfDmaTransactionCreate
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <=DISPATCH_LEVEL
req.product: Windows 10 or later.
---

# WdfDmaTransactionCreate function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WdfDmaTransactionCreate</b> method creates a DMA transaction.  



## -syntax

````
NTSTATUS WdfDmaTransactionCreate(
  _In_     WDFDMAENABLER          DmaEnabler,
  _In_opt_ PWDF_OBJECT_ATTRIBUTES Attributes,
  _Out_    WDFDMATRANSACTION      *DmaTransaction
);
````


## -parameters

### -param DmaEnabler [in]

A handle to a DMA enabler object that the driver obtained from a previous call to <a href="wdf.wdfdmaenablercreate">WdfDmaEnablerCreate</a>.  


### -param Attributes [in, optional]

A pointer to a <a href="wdf.wdf_object_attributes">WDF_OBJECT_ATTRIBUTES</a> structure that specifies object attributes for the new DMA transaction object. (The structure's <b>ParentObject</b> member must be <b>NULL</b>.) This parameter is optional and can be WDF_NO_OBJECT_ATTRIBUTES.


### -param DmaTransaction [out]

A handle to a DMA transaction object.


## -returns
<b>WdfDmaTransactionCreate</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, this method might return one of the following values:
<dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl>An invalid parameter was detected.
<dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl>There was insufficient memory to create a new DMA transaction object.

 

For a list of other return values that the <b>WdfDmaTransactionCreate</b> method might return, see <a href="wdf.framework_object_creation_errors">Framework Object Creation Errors</a>.



This method also might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.

A bug check occurs if the driver supplies an invalid object handle.




## -remarks
After your driver calls <b>WdfDmaTransactionCreate</b>, it must call <a href="wdf.wdfdmatransactioninitialize">WdfDmaTransactionInitialize</a> or <a href="wdf.wdfdmatransactioninitializeusingrequest">WdfDmaTransactionInitializeUsingRequest</a> before calling <a href="wdf.wdfdmatransactionexecute">WdfDmaTransactionExecute</a>. 

The specified DMA enabler object becomes the parent of the new DMA transaction object. The driver cannot change this parent, and the <b>ParentObject</b> member or the <a href="wdf.wdf_object_attributes">WDF_OBJECT_ATTRIBUTES</a> structure must be <b>NULL</b>.

For more information about DMA transactions, see <a href="wdf.creating_and_initializing_a_dma_transaction">Creating and Initializing a DMA Transaction</a>. 

For a code example that uses <b>WdfDmaTransactionCreate</b>, see <a href="wdf.wdfdmatransactionexecute">WdfDmaTransactionExecute</a>.


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Minimum KMDF version

</th>
<td width="70%">
1.0

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wdfdmatransaction.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (see <a href="wdf.framework_library_versioning">Framework Library Versioning</a>.)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
&lt;=DISPATCH_LEVEL

</td>
</tr>
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.kmdf_drivercreate">DriverCreate</a>, <a href="devtest.kmdf_kmdfirql">KmdfIrql</a>, <a href="devtest.kmdf_kmdfirql2">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="wdf.wdf_object_attributes">WDF_OBJECT_ATTRIBUTES</a>
</dt>
<dt>
<a href="wdf.wdfdmaenablercreate">WdfDmaEnablerCreate</a>
</dt>
<dt>
<a href="wdf.wdfdmatransactionexecute">WdfDmaTransactionExecute</a>
</dt>
<dt>
<a href="wdf.wdfdmatransactioninitialize">WdfDmaTransactionInitialize</a>
</dt>
<dt>
<a href="wdf.wdfdmatransactioninitializeusingrequest">WdfDmaTransactionInitializeUsingRequest</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDmaTransactionCreate method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
