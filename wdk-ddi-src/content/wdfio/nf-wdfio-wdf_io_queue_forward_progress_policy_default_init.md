---
UID: NF.wdfio.WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT
title: WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT function
author: windows-driver-content
description: The WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT function initializes a driver's WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY structure.
old-location: wdf\wdf_io_queue_forward_progress_policy_default_init.htm
old-project: wdf
ms.assetid: d4342c72-6737-4f9a-927a-dbfdd69da38d
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfio.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.9
req.umdf-ver: 
req.alt-api: WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT
req.alt-loc: wdfio.h
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
req.product: Windows 10 or later.
---

# WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT</b> function initializes a driver's <a href="wdf.wdf_io_queue_forward_progress_policy">WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY</a> structure.



## -syntax

````
VOID WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT(
  _Out_ PWDF_IO_QUEUE_FORWARD_PROGRESS_POLICY Policy,
  _In_  ULONG                                 TotalForwardProgressRequests
);
````


## -parameters

### -param Policy [out]

A pointer to the driver's <a href="wdf.wdf_io_queue_forward_progress_policy">WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY</a> structure.


### -param TotalForwardProgressRequests [in]

The number of request objects that the framework will attempt to reserve for use in low-memory situations. This number must be greater than zero.


## -returns
None.


## -remarks
The <b>WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT</b> function zeros the specified <a href="wdf.wdf_io_queue_forward_progress_policy">WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY</a> structure and sets its <b>Size</b> member. It also sets the structure's <b>TotalForwardProgressRequests </b>member to the specified value and sets the <b>ForwardProgressReservedPolicy</b> member to <b>WdfIoForwardProgressReservedPolicyAlwaysUseReservedRequest</b>.

The following code example initializes a <a href="wdf.wdf_io_queue_forward_progress_policy">WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY</a> structure and then calls <a href="wdf.wdfioqueueassignforwardprogresspolicy">WdfIoQueueAssignForwardProgressPolicy</a>. In the example, the driver is specifying that the framework should allocate and reserve 10 request objects for low-memory situations.


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
1.9

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wdfio.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="wdf.wdf_io_queue_forward_progress_policy_examine_init">WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_EXAMINE_INIT</a>
</dt>
<dt>
<a href="wdf.wdf_io_queue_forward_progress_policy_pagingio_init">WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_PAGINGIO_INIT</a>
</dt>
<dt>
<a href="wdf.wdfioqueueassignforwardprogresspolicy">WdfIoQueueAssignForwardProgressPolicy</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY_DEFAULT_INIT function%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
