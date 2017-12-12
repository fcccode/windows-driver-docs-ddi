---
UID: NI.pmi.IOCTL_PMI_GET_MEASUREMENT
title: IOCTL_PMI_GET_MEASUREMENT
author: windows-driver-content
description: The IOCTL_PMI_GET_MEASUREMENT request returns the current measurement data from a power meter.
old-location: powermeter\ioctl_pmi_get_measurement.htm
old-project: powermeter
ms.assetid: 2f479147-cccb-44c8-bc86-37c6731cb95b
ms.author: windowsdriverdev
ms.date: 11/6/2017
ms.keywords: PMI_MEASUREMENT_UNIT, PMI_MEASUREMENT_UNIT
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: pmi.h
req.include-header: Pmi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7, Windows Server 2008 R2, and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_PMI_GET_MEASUREMENT
req.alt-loc: Pmi.h
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
---

# IOCTL_PMI_GET_MEASUREMENT IOCTL



## -description
The <b>IOCTL_PMI_GET_MEASUREMENT</b> request returns the current measurement data from a power meter.



## -ioctlparameters

### -input-buffer
The initiator-allocated output buffer that is pointed to by the <b>AssociatedIrp.SystemBuffer</b> member of the IRP.


### -input-buffer-length
The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the IRP's current I/O stack location (<a href="kernel.io_stack_location">IO_STACK_LOCATION</a>) is set to the size in bytes of the initiator-allocated output buffer that is pointed to by the <b>AssociatedIrp.SystemBuffer</b> member of the IRP. This size must be greater than or equal to <b>sizeof</b>(<a href="powermeter.pmi_measurement_data">PMI_MEASUREMENT_DATA</a>) or the request fails with an error status of STATUS_BUFFER_TOO_SMALL.


### -output-buffer
If the request completes successfully, the output buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member contains a <a href="powermeter.pmi_measurement_data">PMI_MEASUREMENT_DATA</a> structure. This structure contains the requested measurement data.


### -output-buffer-length
The size of a <a href="powermeter.pmi_measurement_data">PMI_MEASUREMENT_DATA</a> structure.


### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
The <b>Information</b> member is set to the size, in bytes, of a <a href="powermeter.pmi_measurement_data">PMI_MEASUREMENT_DATA</a> structure.

The <b>Status</b> member is set to one of the following values:



The WDM driver that supports the PMI interface has completed the IOCTL request successfully.

The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the <a href="kernel.irp">IRP</a> is less than the size, in bytes, of a <a href="powermeter.pmi_measurement_data">PMI_MEASUREMENT_DATA</a> structure.


## -remarks
The <b>IOCTL_PMI_GET_MEASUREMENT</b> request queries the current measurement data from the power meter. This measurement data is sampled and averaged based on the power meter's measurement configuration parameters. The measurement configuration parameters are queried through the <a href="..\pmi\ni-pmi-ioctl_pmi_get_configuration.md">IOCTL_PMI_GET_CONFIGURATION</a> request with an input <a href="..\pmi\ne-pmi-pmi_configuration_type.md">PMI_CONFIGURATION_TYPE</a> value of <b>PmiMeasurementConfiguration</b>.


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Available in Windows 7, Windows Server 2008 R2, and later versions of the Windows operating systems.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Pmi.h (include Pmi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\pmi\ni-pmi-ioctl_pmi_get_capabilities.md">IOCTL_PMI_GET_CAPABILITIES</a>
</dt>
<dt>
<a href="..\pmi\ni-pmi-ioctl_pmi_get_configuration.md">IOCTL_PMI_GET_CONFIGURATION</a>
</dt>
<dt>
<a href="kernel.io_stack_location">IO_STACK_LOCATION</a>
</dt>
<dt>
<a href="kernel.irp">IRP</a>
</dt>
<dt>
<a href="..\pmi\ne-pmi-pmi_configuration_type.md">PMI_CONFIGURATION_TYPE</a>
</dt>
<dt>
<a href="powermeter.pmi_measurement_data">PMI_MEASUREMENT_DATA</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [powermeter\powermeter]:%20IOCTL_PMI_GET_MEASUREMENT control code%20 RELEASE:%20(11/6/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
