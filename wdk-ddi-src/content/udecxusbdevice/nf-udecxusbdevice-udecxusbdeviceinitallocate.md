---
UID: NF.udecxusbdevice.UdecxUsbDeviceInitAllocate
title: UdecxUsbDeviceInitAllocate function
author: windows-driver-content
description: Allocates memory for a UDECXUSBDEVICE_INIT structure that is used to initialize a virtual USB device.
old-location: buses\udecxusbdeviceinitallocate.htm
old-project: usbref
ms.assetid: 127D132B-6A40-4F6F-BCDA-473F89A1A747
ms.author: windowsdriverdev
ms.date: 12/6/2017
ms.keywords: UdecxUsbDeviceInitAllocate
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: udecxusbdevice.h
req.include-header: Udecx.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 1.15
req.umdf-ver: 
req.alt-api: UdecxUsbDeviceInitAllocate
req.alt-loc: Udecxstub.lib,Udecxstub.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Udecxstub.lib
req.dll: 
req.irql: PASSIVE_LEVEL
req.product: Windows 10 or later.
---

# UdecxUsbDeviceInitAllocate function



## -description
Allocates memory for a  <b>UDECXUSBDEVICE_INIT</b> structure that is used to initialize a virtual USB device.



## -syntax

````
FORCEINLINE PUDECXUSBDEVICE_INIT UdecxUsbDeviceInitAllocate(
  _In_ WDFDEVICE UdecxWdfDevice
);
````


## -parameters

### -param UdecxWdfDevice [in]

A handle to a framework device object that represents the a USB device. The client driver initialized this object in the previous call to <a href="buses.udecxwdfdeviceaddusbdeviceemulation">UdecxWdfDeviceAddUsbDeviceEmulation</a>.


## -returns
This method returns a pointer to an opaque <b>UDECXUSBDEVICE_INIT</b> that contains the initialization parameters. The structure is allocated by the USB device emulation  class extension (UdeCx).


## -remarks
The UDE client driver calls this method to allocate parameters for the virtual device that is created by a subsequent call to <a href="buses.udecxusbdevicecreate">UdecxUsbDeviceCreate</a>. If the device is not created or the driver is finished using the resources, the driver must free the resources by calling <a href="buses.udecxusbdeviceinitfree">UdecxUsbDeviceInitFree</a>.


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 10

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2016

</td>
</tr>
<tr>
<th width="30%">
Minimum KMDF version

</th>
<td width="70%">
1.15

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>UdecxUsbDevice.h (include Udecx.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Udecxstub.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
PASSIVE_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="buses.usb_emulated_device__ude__architecture">Architecture: USB Device Emulation (UDE)</a>
</dt>
<dt>
<a href="buses.writing_a_ude_client_driver">Write a UDE client driver</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20UdecxUsbDeviceInitAllocate function%20 RELEASE:%20(12/6/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
