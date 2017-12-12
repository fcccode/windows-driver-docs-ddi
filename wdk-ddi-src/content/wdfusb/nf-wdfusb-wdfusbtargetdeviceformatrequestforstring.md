---
UID: NF.wdfusb.WdfUsbTargetDeviceFormatRequestForString
title: WdfUsbTargetDeviceFormatRequestForString function
author: windows-driver-content
description: The WdfUsbTargetDeviceFormatRequestForString method builds a request for the USB string descriptor that is associated with a USB device's string index value.
old-location: wdf\wdfusbtargetdeviceformatrequestforstring.htm
old-project: wdf
ms.assetid: f1875578-33c1-4d9e-865b-f1f5391f4aca
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfUsbTargetDeviceFormatRequestForString
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfusb.h
req.include-header: Wdfusb.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfUsbTargetDeviceFormatRequestForString
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2, RequestFormattedValid, RequestForUrbXrb, RequestSendAndForgetNoFormatting, RequestSendAndForgetNoFormatting2, UsbKmdfIrql, UsbKmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); WUDFx02000.dll (UMDF)
req.dll: 
req.irql: <=DISPATCH_LEVEL
req.product: Windows 10 or later.
---

# WdfUsbTargetDeviceFormatRequestForString function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]

The <b>WdfUsbTargetDeviceFormatRequestForString</b> method builds a request for the USB string descriptor that is associated with a USB device's string index value. 



## -syntax

````
NTSTATUS WdfUsbTargetDeviceFormatRequestForString(
  _In_     WDFUSBDEVICE      UsbDevice,
  _In_     WDFREQUEST        Request,
  _In_     WDFMEMORY         Memory,
  _In_opt_ PWDFMEMORY_OFFSET Offset,
  _In_     UCHAR             StringIndex,
  _In_opt_ USHORT            LangID
);
````


## -parameters

### -param UsbDevice [in]

A handle to a USB device object that was obtained from a previous call to <a href="wdf.wdfusbtargetdevicecreatewithparameters">WdfUsbTargetDeviceCreateWithParameters</a>.


### -param Request [in]

A handle to a framework request object.


### -param Memory [in]

A handle to a framework memory object.


### -param Offset [in, optional]

A pointer to a caller-allocated <a href="wdf.wdfmemory_offset">WDFMEMORY_OFFSET</a> structure that supplies optional byte offset and length values. The framework uses these values to determine the beginning address and length, within the output buffer, for storing the string descriptor. If this pointer is <b>NULL</b>, the descriptor is stored at the beginning of the output buffer, and the maximum string length is the buffer length. 


### -param StringIndex [in]

An index value that identifies the string. This index value is obtained from a <a href="buses.usb_device_descriptor">USB_DEVICE_DESCRIPTOR</a>, <a href="buses.usb_configuration_descriptor">USB_CONFIGURATION_DESCRIPTOR</a>, or <a href="buses.usb_interface_descriptor">USB_INTERFACE_DESCRIPTOR</a> structure.


### -param LangID [in, optional]

A language identifier. The string will be retrieved for the language that this identifier specifies. For information about obtaining a device's supported language identifiers, see the USB specification. 


## -returns
<b>WdfUsbTargetDeviceFormatRequestForString</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, this method can return one of the following values:
<dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl>The buffer's byte count was not an even number.
<dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl>There was insufficient memory.
<dl>
<dt><b>STATUS_INTEGER_OVERFLOW</b></dt>
</dl>The offset that <i>Offset</i> specifies was invalid.

 

This method also might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.

A bug check occurs if the driver supplies an invalid object handle.




## -remarks
After <b>WdfUsbTargetDeviceFormatRequestForString</b> returns, the driver must call <a href="wdf.wdfrequestsend">WdfRequestSend</a> to send the request. After <b>WdfRequestSend</b> returns, the driver can pass the <i>Memory</i> handle to <a href="wdf.wdfmemorygetbuffer">WdfMemoryGetBuffer</a> to obtain a pointer to the memory buffer. The buffer will contain a <a href="buses.usb_string_descriptor">USB_STRING_DESCRIPTOR</a> structure that describes the string descriptor.

For more information about the <b>WdfUsbTargetDeviceFormatRequestForString</b> method and USB I/O targets, see <a href="wdf.usb_i_o_targets">USB I/O Targets</a>.

The following code example creates a request object and a memory object, and it passes the object handles to <b>WdfUsbTargetDeviceFormatRequestForString</b>. Then, the example sets a <a href="..\wdfrequest\nc-wdfrequest-evt_wdf_request_completion_routine.md">CompletionRoutine</a> callback function for the request and sends the request to an I/O target.


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
<dt>Wdfusb.h (include Wdfusb.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (KMDF); </dt>
<dt>WUDFx02000.dll (UMDF)</dt>
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
<a href="devtest.kmdf_drivercreate">DriverCreate</a>, <a href="devtest.kmdf_kmdfirql">KmdfIrql</a>, <a href="devtest.kmdf_kmdfirql2">KmdfIrql2</a>, <a href="devtest.kmdf_requestformattedvalid">RequestFormattedValid</a>, <a href="devtest.kmdf_requestforurbxrb">RequestForUrbXrb</a>, <a href="devtest.kmdf_requestsendandforgetnoformatting">RequestSendAndForgetNoFormatting</a>, <a href="devtest.kmdf_requestsendandforgetnoformatting2">RequestSendAndForgetNoFormatting2</a>, <a href="devtest.kmdf_usbkmdfirql">UsbKmdfIrql</a>, <a href="devtest.kmdf_usbkmdfirql2">UsbKmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="buses.usb_configuration_descriptor">USB_CONFIGURATION_DESCRIPTOR</a>
</dt>
<dt>
<a href="buses.usb_device_descriptor">USB_DEVICE_DESCRIPTOR</a>
</dt>
<dt>
<a href="buses.usb_interface_descriptor">USB_INTERFACE_DESCRIPTOR</a>
</dt>
<dt>
<a href="buses.usb_string_descriptor">USB_STRING_DESCRIPTOR</a>
</dt>
<dt>
<a href="wdf.wdfmemory_offset">WDFMEMORY_OFFSET</a>
</dt>
<dt>
<a href="wdf.wdfmemorygetbuffer">WdfMemoryGetBuffer</a>
</dt>
<dt>
<a href="wdf.wdfrequestsend">WdfRequestSend</a>
</dt>
<dt>
<a href="wdf.wdfrequestsetcompletionroutine">WdfRequestSetCompletionRoutine</a>
</dt>
<dt>
<a href="wdf.wdfusbtargetdeviceallocandquerystring">WdfUsbTargetDeviceAllocAndQueryString</a>
</dt>
<dt>
<a href="wdf.wdfusbtargetdevicecreatewithparameters">WdfUsbTargetDeviceCreateWithParameters</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfUsbTargetDeviceFormatRequestForString method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
