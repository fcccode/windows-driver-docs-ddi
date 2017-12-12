---
UID: NC.ucxusbdevice.EVT_UCX_USBDEVICE_DISABLE
title: EVT_UCX_USBDEVICE_DISABLE
author: windows-driver-content
description: The client driver's implementation that UCX calls to release controller resources associated with the device and its default endpoint.
old-location: buses\evt_ucx_usbdevice_disable.htm
old-project: usbref
ms.assetid: 85aa1d5e-e660-4fd7-a58d-8d32bbd966f2
ms.author: windowsdriverdev
ms.date: 12/6/2017
ms.keywords: _STREAM_INFO, *PSTREAM_INFO, STREAM_INFO
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: ucxusbdevice.h
req.include-header: Ucxclass.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: PEVT_UCX_USBDEVICE_DISABLE
req.alt-loc: ucxusbdevice.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: DISPATCH_LEVEL
req.product: Windows 10 or later.
---

# EVT_UCX_USBDEVICE_DISABLE callback



## -description
The client driver's implementation that UCX calls to release controller resources associated with the device and its default endpoint.



## -prototype

````
EVT_UCX_USBDEVICE_DISABLE EvtUcxUsbDeviceDisable;

VOID EvtUcxUsbDeviceDisable(
  _In_ UCXCONTROLLER UcxController,
  _In_ WDFREQUEST    Request
)
{ ... }

typedef EVT_UCX_USBDEVICE_DISABLE PEVT_UCX_USBDEVICE_DISABLE;
````


## -parameters

### -param UcxController [in]

 A handle to the UCX controller that the client driver received in a previous call to  the <a href="buses._ucxcontrollercreate">UcxControllerCreate</a> method.


### -param Request [in]

A structure of type <a href="buses._usbdevice_disable">USBDEVICE_DISABLE</a>.


## -returns
This callback function does not return a value.


## -remarks
The UCX client driver registers this callback function with the USB host controller extension (UCX) by calling the <a href="buses._ucxusbdevicecreate">UcxUsbDeviceCreate</a> method.

When the client driver has released controller resources, it completes the WDFREQUEST.  After completion, the only callback function that UCX  calls referencing this USB device is <a href="..\ucxusbdevice\nc-ucxusbdevice-evt_ucx_usbdevice_enable.md">EVT_UCX_USBDEVICE_ENABLE</a>.

  While the device is disabled, UCX does not schedule transfers
    for it.

    

To
    transition the device to the desired state, the host controller driver communicates with the hardware to complete the request.

The client driver returns completion status in <i>Request</i>.  The driver can complete the WDFREQUEST asynchronously.


## -requirements
<table>
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
Minimum UMDF version

</th>
<td width="70%">
2.0

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ucxusbdevice.h (include Ucxclass.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
DISPATCH_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="buses._ucxusbdevicecreate">UcxUsbDeviceCreate</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20EVT_UCX_USBDEVICE_DISABLE callback function%20 RELEASE:%20(12/6/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
