---
UID: NI.ntddstor.IOCTL_STORAGE_PROTOCOL_COMMAND
title: IOCTL_STORAGE_PROTOCOL_COMMAND
author: windows-driver-content
description: A driver can use IOCTL_STORAGE_PROTOCOL_COMMAND to pass vendor-specific commands to a storage device.
old-location: storage\ioctl_storage_protocol_command.htm
old-project: storage
ms.assetid: 1AA59350-2475-4BF7-B447-42FDDB311882
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _STORAGE_ZONE_CONDITION, *PSTORAGE_ZONE_CONDITION, STORAGE_ZONE_CONDITION
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: ntddstor.h
req.include-header: Ntddstor.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_STORAGE_PROTOCOL_COMMAND
req.alt-loc: ntddstor.h
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

# IOCTL_STORAGE_PROTOCOL_COMMAND IOCTL



## -description
A driver can use <b>IOCTL_STORAGE_PROTOCOL_COMMAND</b> to pass vendor-specific commands to a storage device.

<b>Parameters.DeviceIoControl.OutputBufferLength</b> in the I/O stack location indicates the size, in bytes, of the parameter buffer, which must be &gt;= <b>sizeof</b>(<a href="storage.storage_protocol_command">STORAGE_PROTOCOL_COMMAND</a>). 

The driver returns the results of the vendor-specific command to the buffer at <b>Irp-&gt;AssociatedIrp.SystemBuffer</b>. Cast the structure returned to a <a href="storage.storage_protocol_command">STORAGE_PROTOCOL_COMMAND</a> and check its <b>ReturnStatus</b> field to determine the status of the command request.

The <b>Information</b> field is set to the number of bytes returned. The <b>Status</b> field is set to <b>STATUS_SUCCESS</b>, or possibly to <b>STATUS_INSUFFICIENT_RESOURCES</b>.



## -ioctlparameters

### -input-buffer
<a id="Input_Buffer"></a><a id="input_buffer"></a><a id="INPUT_BUFFER"></a>Input Buffer
<b>Parameters.DeviceIoControl.OutputBufferLength</b> in the I/O stack location indicates the size, in bytes, of the parameter buffer, which must be &gt;= <b>sizeof</b>(<a href="storage.storage_protocol_command">STORAGE_PROTOCOL_COMMAND</a>). 
<b>Parameters.DeviceIoControl.OutputBufferLength</b>Parameters.DeviceIoControl.OutputBufferLength in the I/O stack location indicates the size, in bytes, of the parameter buffer, which must be >= <b>sizeof</b>sizeof(<a href="storage.storage_protocol_command">STORAGE_PROTOCOL_COMMAND</a><b>STORAGE_PROTOCOL_COMMAND</b>STORAGE_PROTOCOL_COMMAND). 


### -input-buffer-length

<text></text>

### -output-buffer
<a id="Output_Buffer"></a><a id="output_buffer"></a><a id="OUTPUT_BUFFER"></a>Output Buffer
The driver returns the results of the vendor-specific command to the buffer at <b>Irp-&gt;AssociatedIrp.SystemBuffer</b>. Cast the structure returned to a <a href="storage.storage_protocol_command">STORAGE_PROTOCOL_COMMAND</a> and check its <b>ReturnStatus</b> field to determine the status of the command request.</p>The driver returns the results of the vendor-specific command to the buffer at <b>Irp-&gt;AssociatedIrp.SystemBuffer</b>Irp->AssociatedIrp.SystemBuffer. Cast the structure returned to a <a href="storage.storage_protocol_command">STORAGE_PROTOCOL_COMMAND</a><b>STORAGE_PROTOCOL_COMMAND</b>STORAGE_PROTOCOL_COMMAND and check its <b>ReturnStatus</b>ReturnStatus field to determine the status of the command request.


### -output-buffer-length

<text></text>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
<a id="I_O_Status_Block"></a><a id="i_o_status_block"></a><a id="I_O_STATUS_BLOCK"></a>I/O Status Block
The <b>Information</b> field is set to the number of bytes returned. The <b>Status</b> field is set to <b>STATUS_SUCCESS</b>, or possibly to <b>STATUS_INSUFFICIENT_RESOURCES</b>.</p>The <b>Information</b>Information field is set to the number of bytes returned. The <b>Status</b>Status field is set to <b>STATUS_SUCCESS</b>STATUS_SUCCESS, or possibly to <b>STATUS_INSUFFICIENT_RESOURCES</b>STATUS_INSUFFICIENT_RESOURCES.


## -remarks


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
Header

</th>
<td width="70%">
<dl>
<dt>Ntddstor.h (include Ntddstor.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.storage_protocol_command">STORAGE_PROTOCOL_COMMAND</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20IOCTL_STORAGE_PROTOCOL_COMMAND control code%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
