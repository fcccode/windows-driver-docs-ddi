---
UID: NF.portcls.PcAddAdapterDevice
title: PcAddAdapterDevice function
author: windows-driver-content
description: The PcAddAdapterDevice function adds an adapter device to the WDM device stack.
old-location: audio\pcaddadapterdevice.htm
old-project: audio
ms.assetid: fa571ca0-194c-4018-9b93-a3cc687f7632
ms.author: windowsdriverdev
ms.date: 12/6/2017
ms.keywords: PcAddAdapterDevice
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: portcls.h
req.include-header: Portcls.h
req.target-type: Universal
req.target-min-winverclnt: Available starting in Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PcAddAdapterDevice
req.alt-loc: Portcls.lib,Portcls.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Portcls.lib
req.dll: 
req.irql: PASSIVE_LEVEL
---

# PcAddAdapterDevice function



## -description
The <b>PcAddAdapterDevice</b> function adds an adapter device to the WDM device stack.



## -syntax

````
NTSTATUS PcAddAdapterDevice(
  _In_ PDRIVER_OBJECT   DriverObject,
  _In_ PDEVICE_OBJECT   PhysicalDeviceObject,
  _In_ PCPFNSTARTDEVICE StartDevice,
  _In_ ULONG            MaxObjects,
  _In_ ULONG            DeviceExtensionSize
);
````


## -parameters

### -param DriverObject [in]

Pointer to the driver object. This pointer is passed as a parameter to the adapter's <a href="kernel.adddevice">AddDevice</a> handler. The driver object is a system structure of type <a href="kernel.driver_object">DRIVER_OBJECT</a>.


### -param PhysicalDeviceObject [in]

Pointer to the device's <a href="wdkgloss.p#wdkgloss.physical_device_object__pdo_#wdkgloss.physical_device_object__pdo_"><i>physical device object (PDO)</i></a>. PortCls passes this pointer as a call parameter to the adapter's <i>AddDevice</i> handler. The PDO is a system structure of type <a href="kernel.device_object">DEVICE_OBJECT</a>.


### -param StartDevice [in]

Pointer to the function that the operating system calls in order to start the device. For more information, see the following <b>Remarks</b> section.


### -param MaxObjects [in]

Specifies the maximum number of subdevices to be registered by calls to <a href="audio.pcregistersubdevice">PcRegisterSubdevice</a>. This count sets the upper limit to the total number of miniport objects that the adapter driver can instantiate.


### -param DeviceExtensionSize [in]

Specifies the device extension size. Use zero for default size. See the following <b>Remarks</b> section for user-supplied extension sizes.


## -returns
<b>PcAddAdapterDevice</b> returns STATUS_SUCCESS if the call was successful. Otherwise, it returns an appropriate error code.


## -remarks
This function does most of the work that the audio adapter driver's <a href="kernel.adddevice">AddDevice</a> handler needs to perform. <b>PcAddAdapterDevice</b> creates the device object, initializes the device context, and attaches the device object to the device stack.

An adapter driver calls <b>PcAddAdapterDevice</b> when it receives a call to its <i>AddDevice </i>handler. The adapter driver typically installs the <i>AddDevice </i>handler by calling <a href="audio.pcinitializeadapterdriver">PcInitializeAdapterDriver</a>, although the driver can also install the handler by other means. <b>PcAddAdapterDevice</b> creates the <a href="wdkgloss.f#wdkgloss.functional_device_object__fdo_#wdkgloss.functional_device_object__fdo_"><i>functional device object (FDO)</i></a> for the PDO that was passed to the <i>AddDevice</i> handler.

<i>DeviceExtensionSize</i> is typically zero. Some adapter drivers might need to reserve additional space in the device extension, in which case they should specify a <i>DeviceExtensionSize</i> greater than PORT_CLASS_DEVICE_EXTENSION_SIZE, which is the default size. Any value greater than zero and less than PORT_CLASS_DEVICE_EXTENSION_SIZE is illegal. Adapter drivers are free to use any part of the device extension after offset PORT_CLASS_DEVICE_EXTENSION_SIZE. They are also free to use bytes in the offset range of 16 to 31 inclusive in a system with 32-bit addressing and bytes in the offset range 32 to 63 in a system with 64-bit addressing. If the extension is regarded as an array of ULONG_PTR, array elements four through seven are available for use by the adapter driver.

The <i>StartDevice</i> parameter points to a function of type PCPFNSTARTDEVICE, which header file <i>portcls.h </i>defines as:

For more information about <b>PcAddAdapterDevice</b> and the adapter driver's device-startup and <i>AddDevice </i>routines, see <a href="https://msdn.microsoft.com/bf88b9de-f4c4-4f9c-9355-603789b9ad3d">Startup Sequence</a>.

The following example code shows how an adapter driver can use the <i>DeviceExtensionSize </i>parameter to append 64 bytes of device-specific extension data to the end of the storage block that PortCls allocates for the device context:

The <b>PcAddAdapterDevice</b> call above is similar to the example in <a href="https://msdn.microsoft.com/bf88b9de-f4c4-4f9c-9355-603789b9ad3d">Startup Sequence</a>, except that the last parameter that is passed to <b>PcAddAdapterDevice</b> is nonzero.

The adapter driver can then access the device-specific extension data, as shown in the following code fragment:

Variable <i>FunctionalDeviceObject</i> is a pointer to the audio adapter's FDO, and <i>pMyExtensionData</i> is a temporary pointer to the extension data. Avoid confusing the FDO with the PDO, which belongs to the PCI bus driver. The adapter driver must not modify data in the PDO because doing so corrupts memory owned by the PCI bus driver and can cause the system to crash.


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
Minimum support

</th>
<td width="70%">
Available starting in Windows 2000. 

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Portcls.h (include Portcls.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Portcls.lib</dt>
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
<a href="kernel.adddevice">AddDevice</a>
</dt>
<dt>
<a href="kernel.driver_object">DRIVER_OBJECT</a>
</dt>
<dt>
<a href="kernel.device_object">DEVICE_OBJECT</a>
</dt>
<dt>
<a href="audio.pcregistersubdevice">PcRegisterSubdevice</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PcAddAdapterDevice function%20 RELEASE:%20(12/6/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
