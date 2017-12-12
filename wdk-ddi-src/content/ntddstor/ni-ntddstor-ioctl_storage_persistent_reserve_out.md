---
UID: NI.ntddstor.IOCTL_STORAGE_PERSISTENT_RESERVE_OUT
title: IOCTL_STORAGE_PERSISTENT_RESERVE_OUT
author: windows-driver-content
description: The generic storage class driver (classpnp.sys) exposes an I/O control (IOCTL) interface for issuing Persistent Reserve Out commands.
old-location: storage\ioctl_storage_persistent_reserve_out.htm
old-project: storage
ms.assetid: a9863ac9-46e2-4888-879e-7d56e9260142
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _STORAGE_ZONE_CONDITION, *PSTORAGE_ZONE_CONDITION, STORAGE_ZONE_CONDITION
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: ntddstor.h
req.include-header: Ntddstor.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_STORAGE_PERSISTENT_RESERVE_OUT
req.alt-loc: Ntddstor.h
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

# IOCTL_STORAGE_PERSISTENT_RESERVE_OUT IOCTL



## -description
The generic storage class driver (<i>classpnp.sys</i>) exposes an I/O control (IOCTL) interface for issuing Persistent Reserve Out commands. The behavior of the storage device when a Persistent Reserve Out command is received is described in the <a href="http://go.microsoft.com/fwlink/p/?linkid=153142">SCSI Primary Commands - 2 (SPC-2)</a> specification. The IOCTL interface requires the caller to have read/write access to the physical device for Persistent Reserve Out commands. User-mode applications, services, and kernel-mode drivers can use this IOCTL to control persistent reservations. If called from a driver, this IOCTL must be called from a thread running at IRQL &lt; DISPATCH_LEVEL. This IOCTL is defined with FILE_READ_ACCESS and FILE_WRITE_ACCESS, requiring a device handle to have both read and write permissions to issue the Persistent Reserve Out command.

The buffer at <b>Irp-&gt;AssociatedIrp.SystemBuffer</b> contains a <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a> structure. You must allocate the buffer from nonpaged pool and must align it correctly for the  target device and adapter.

PR_OUT.ServiceAction can be one of the following:

RESERVATION_ACTION_REGISTER

RESERVATION_ACTION_RESERVE

RESERVATION_ACTION_RELEASE

RESERVATION_ACTION_CLEAR

RESERVATION_ACTION_PREEMPT

RESERVATION_ACTION_PREEMPT_ABORT

RESERVATION_ACTION_REGISTER_IGNORE_EXISTING

PR_OUT.Scope can be one of the following:

RESERVATION_SCOPE_LU

RESERVATION_SCOPE_ELEMENT

PR_OUT.Type can be one of the following:

RESERVATION_TYPE_WRITE_EXCLUSIVE

RESERVATION_TYPE_EXCLUSIVE

RESERVATION_TYPE_WRITE_EXCLUSIVE_REGISTRANTS

RESERVATION_TYPE_EXCLUSIVE_REGISTRANTS

PR_OUT.ParameterList is used to hold the <a href="storage.pro_parameter_list">PRO_PARAMETER_LIST</a> structure. This structure is required and must be contiguous with the rest of the <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a> structure.

None

The <b>Information</b> field is set to zero.

The <b>Status</b> field is set to one of the following:



The operation was successful.

The input buffer structure is incorrectly sized or populated.

The I/O control code (IOCTL_STORAGE_PERSISTENT_RESERVE_OUT) is not supported by the storage drivers.

The command failed because of a Reservation Conflict (for more information, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=153142">SCSI Primary Commands - 2 (SPC-2)</a> specification).

The device does not support the Persistent Reserve Out command.

The input buffer is not aligned correctly for the device or adapter.  This status could only be returned when a driver sends an IOCTL to the storage stack.  This status will not be returned when a user-mode application sends the IOCTL through the DeviceIoControl API as the I/O Manager automatically aligns the buffers.

The input buffer length for the IOCTL is less than sizeof(PERSISTENT_RESERVE_COMMAND) or the size that is specified in the <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a> data structure is less than sizeof(PERSISTENT_RESERVE_COMMAND).



## -ioctlparameters

### -input-buffer
<a id="Input_Buffer"></a><a id="input_buffer"></a><a id="INPUT_BUFFER"></a>Input Buffer
The buffer at <b>Irp-&gt;AssociatedIrp.SystemBuffer</b> contains a <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a> structure. You must allocate the buffer from nonpaged pool and must align it correctly for the  target device and adapter.</p>The buffer at <b>Irp-&gt;AssociatedIrp.SystemBuffer</b>Irp->AssociatedIrp.SystemBuffer contains a <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a><b>PERSISTENT_RESERVE_COMMAND</b>PERSISTENT_RESERVE_COMMAND structure. You must allocate the buffer from nonpaged pool and must align it correctly for the  target device and adapter.
PR_OUT.ServiceAction can be one of the following:</p>PR_OUT.ServiceAction can be one of the following:
<ul>
<li>
RESERVATION_ACTION_REGISTER

</li>
<li>
RESERVATION_ACTION_RESERVE

</li>
<li>
RESERVATION_ACTION_RELEASE

</li>
<li>
RESERVATION_ACTION_CLEAR

</li>
<li>
RESERVATION_ACTION_PREEMPT

</li>
<li>
RESERVATION_ACTION_PREEMPT_ABORT

</li>
<li>
RESERVATION_ACTION_REGISTER_IGNORE_EXISTING

</li>
</ul>
<li>
RESERVATION_ACTION_REGISTER

</li>
RESERVATION_ACTION_REGISTER</p>RESERVATION_ACTION_REGISTER

<li>
RESERVATION_ACTION_RESERVE

</li>
RESERVATION_ACTION_RESERVE</p>RESERVATION_ACTION_RESERVE

<li>
RESERVATION_ACTION_RELEASE

</li>
RESERVATION_ACTION_RELEASE</p>RESERVATION_ACTION_RELEASE

<li>
RESERVATION_ACTION_CLEAR

</li>
RESERVATION_ACTION_CLEAR</p>RESERVATION_ACTION_CLEAR

<li>
RESERVATION_ACTION_PREEMPT

</li>
RESERVATION_ACTION_PREEMPT</p>RESERVATION_ACTION_PREEMPT

<li>
RESERVATION_ACTION_PREEMPT_ABORT

</li>
RESERVATION_ACTION_PREEMPT_ABORT</p>RESERVATION_ACTION_PREEMPT_ABORT

<li>
RESERVATION_ACTION_REGISTER_IGNORE_EXISTING

</li>
RESERVATION_ACTION_REGISTER_IGNORE_EXISTING</p>RESERVATION_ACTION_REGISTER_IGNORE_EXISTING


PR_OUT.Scope can be one of the following:</p>PR_OUT.Scope can be one of the following:
<ul>
<li>
RESERVATION_SCOPE_LU

</li>
<li>
RESERVATION_SCOPE_ELEMENT

</li>
</ul>
<li>
RESERVATION_SCOPE_LU

</li>
RESERVATION_SCOPE_LU</p>RESERVATION_SCOPE_LU

<li>
RESERVATION_SCOPE_ELEMENT

</li>
RESERVATION_SCOPE_ELEMENT</p>RESERVATION_SCOPE_ELEMENT


PR_OUT.Type can be one of the following:</p>PR_OUT.Type can be one of the following:
<ul>
<li>
RESERVATION_TYPE_WRITE_EXCLUSIVE

</li>
<li>
RESERVATION_TYPE_EXCLUSIVE

</li>
<li>
RESERVATION_TYPE_WRITE_EXCLUSIVE_REGISTRANTS

</li>
<li>
RESERVATION_TYPE_EXCLUSIVE_REGISTRANTS

</li>
</ul>
<li>
RESERVATION_TYPE_WRITE_EXCLUSIVE

</li>
RESERVATION_TYPE_WRITE_EXCLUSIVE</p>RESERVATION_TYPE_WRITE_EXCLUSIVE

<li>
RESERVATION_TYPE_EXCLUSIVE

</li>
RESERVATION_TYPE_EXCLUSIVE</p>RESERVATION_TYPE_EXCLUSIVE

<li>
RESERVATION_TYPE_WRITE_EXCLUSIVE_REGISTRANTS

</li>
RESERVATION_TYPE_WRITE_EXCLUSIVE_REGISTRANTS</p>RESERVATION_TYPE_WRITE_EXCLUSIVE_REGISTRANTS

<li>
RESERVATION_TYPE_EXCLUSIVE_REGISTRANTS

</li>
RESERVATION_TYPE_EXCLUSIVE_REGISTRANTS</p>RESERVATION_TYPE_EXCLUSIVE_REGISTRANTS


PR_OUT.ParameterList is used to hold the <a href="storage.pro_parameter_list">PRO_PARAMETER_LIST</a> structure. This structure is required and must be contiguous with the rest of the <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a> structure.</p>PR_OUT.ParameterList is used to hold the <a href="storage.pro_parameter_list">PRO_PARAMETER_LIST</a><b>PRO_PARAMETER_LIST</b>PRO_PARAMETER_LIST structure. This structure is required and must be contiguous with the rest of the <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a><b>PERSISTENT_RESERVE_COMMAND</b>PERSISTENT_RESERVE_COMMAND structure.


### -input-buffer-length

<text></text>

### -output-buffer
<a id="Output_Buffer"></a><a id="output_buffer"></a><a id="OUTPUT_BUFFER"></a>Output Buffer
None</p>None


### -output-buffer-length

<text></text>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
<a id="I_O_Status_Block"></a><a id="i_o_status_block"></a><a id="I_O_STATUS_BLOCK"></a>I/O Status Block
The <b>Information</b> field is set to zero.</p>The <b>Information</b>Information field is set to zero.
The <b>Status</b> field is set to one of the following:</p>The <b>Status</b>Status field is set to one of the following:


<dl>
<dt><a id="STATUS_SUCCESS"></a><a id="status_success"></a>STATUS_SUCCESS</dt>
<dd>
The operation was successful.

</dd>
<dt><a id="STATUS_INVALID_PARAMETER__ERROR_INVALID_PARAMETER_"></a><a id="status_invalid_parameter__error_invalid_parameter_"></a>STATUS_INVALID_PARAMETER (ERROR_INVALID_PARAMETER)</dt>
<dd>
The input buffer structure is incorrectly sized or populated.

</dd>
<dt><a id="STATUS_INVALID_DEVICE_REQUEST__ERROR_INVALID_FUNCTION_"></a><a id="status_invalid_device_request__error_invalid_function_"></a>STATUS_INVALID_DEVICE_REQUEST (ERROR_INVALID_FUNCTION)</dt>
<dd>
The I/O control code (IOCTL_STORAGE_PERSISTENT_RESERVE_OUT) is not supported by the storage drivers.

</dd>
<dt><a id="STATUS_DEVICE_BUSY__ERROR_BUSY_"></a><a id="status_device_busy__error_busy_"></a>STATUS_DEVICE_BUSY (ERROR_BUSY)</dt>
<dd>
The command failed because of a Reservation Conflict (for more information, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=153142">SCSI Primary Commands - 2 (SPC-2)</a> specification).

</dd>
<dt><a id="STATUS_IO_DEVICE_ERROR__ERROR_IO_DEVICE_"></a><a id="status_io_device_error__error_io_device_"></a>STATUS_IO_DEVICE_ERROR (ERROR_IO_DEVICE)</dt>
<dd>
The device does not support the Persistent Reserve Out command.

</dd>
<dt><a id="STATUS_INVALID_USER_BUFFER__ERROR_INVALID_USER_BUFFER_"></a><a id="status_invalid_user_buffer__error_invalid_user_buffer_"></a>STATUS_INVALID_USER_BUFFER (ERROR_INVALID_USER_BUFFER)</dt>
<dd>
The input buffer is not aligned correctly for the device or adapter.  This status could only be returned when a driver sends an IOCTL to the storage stack.  This status will not be returned when a user-mode application sends the IOCTL through the DeviceIoControl API as the I/O Manager automatically aligns the buffers.

</dd>
<dt><a id="STATUS_INFO_LENGTH_MISMATCH"></a><a id="status_info_length_mismatch"></a>STATUS_INFO_LENGTH_MISMATCH</dt>
<dd>
The input buffer length for the IOCTL is less than sizeof(PERSISTENT_RESERVE_COMMAND) or the size that is specified in the <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a> data structure is less than sizeof(PERSISTENT_RESERVE_COMMAND).

</dd>
</dl>
<dt><a id="STATUS_SUCCESS"></a><a id="status_success"></a>STATUS_SUCCESS</dt><a id="STATUS_SUCCESS"></a><a id="status_success"></a>STATUS_SUCCESS
<dd>
The operation was successful.

</dd>
The operation was successful.</p>The operation was successful.

<dt><a id="STATUS_INVALID_PARAMETER__ERROR_INVALID_PARAMETER_"></a><a id="status_invalid_parameter__error_invalid_parameter_"></a>STATUS_INVALID_PARAMETER (ERROR_INVALID_PARAMETER)</dt><a id="STATUS_INVALID_PARAMETER__ERROR_INVALID_PARAMETER_"></a><a id="status_invalid_parameter__error_invalid_parameter_"></a>STATUS_INVALID_PARAMETER (ERROR_INVALID_PARAMETER)
<dd>
The input buffer structure is incorrectly sized or populated.

</dd>
The input buffer structure is incorrectly sized or populated.</p>The input buffer structure is incorrectly sized or populated.

<dt><a id="STATUS_INVALID_DEVICE_REQUEST__ERROR_INVALID_FUNCTION_"></a><a id="status_invalid_device_request__error_invalid_function_"></a>STATUS_INVALID_DEVICE_REQUEST (ERROR_INVALID_FUNCTION)</dt><a id="STATUS_INVALID_DEVICE_REQUEST__ERROR_INVALID_FUNCTION_"></a><a id="status_invalid_device_request__error_invalid_function_"></a>STATUS_INVALID_DEVICE_REQUEST (ERROR_INVALID_FUNCTION)
<dd>
The I/O control code (IOCTL_STORAGE_PERSISTENT_RESERVE_OUT) is not supported by the storage drivers.

</dd>
The I/O control code (IOCTL_STORAGE_PERSISTENT_RESERVE_OUT) is not supported by the storage drivers.</p>The I/O control code (IOCTL_STORAGE_PERSISTENT_RESERVE_OUT) is not supported by the storage drivers.

<dt><a id="STATUS_DEVICE_BUSY__ERROR_BUSY_"></a><a id="status_device_busy__error_busy_"></a>STATUS_DEVICE_BUSY (ERROR_BUSY)</dt><a id="STATUS_DEVICE_BUSY__ERROR_BUSY_"></a><a id="status_device_busy__error_busy_"></a>STATUS_DEVICE_BUSY (ERROR_BUSY)
<dd>
The command failed because of a Reservation Conflict (for more information, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=153142">SCSI Primary Commands - 2 (SPC-2)</a> specification).

</dd>
The command failed because of a Reservation Conflict (for more information, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=153142">SCSI Primary Commands - 2 (SPC-2)</a> specification).</p>The command failed because of a Reservation Conflict (for more information, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=153142">SCSI Primary Commands - 2 (SPC-2)</a>SCSI Primary Commands - 2 (SPC-2) specification).

<dt><a id="STATUS_IO_DEVICE_ERROR__ERROR_IO_DEVICE_"></a><a id="status_io_device_error__error_io_device_"></a>STATUS_IO_DEVICE_ERROR (ERROR_IO_DEVICE)</dt><a id="STATUS_IO_DEVICE_ERROR__ERROR_IO_DEVICE_"></a><a id="status_io_device_error__error_io_device_"></a>STATUS_IO_DEVICE_ERROR (ERROR_IO_DEVICE)
<dd>
The device does not support the Persistent Reserve Out command.

</dd>
The device does not support the Persistent Reserve Out command.</p>The device does not support the Persistent Reserve Out command.

<dt><a id="STATUS_INVALID_USER_BUFFER__ERROR_INVALID_USER_BUFFER_"></a><a id="status_invalid_user_buffer__error_invalid_user_buffer_"></a>STATUS_INVALID_USER_BUFFER (ERROR_INVALID_USER_BUFFER)</dt><a id="STATUS_INVALID_USER_BUFFER__ERROR_INVALID_USER_BUFFER_"></a><a id="status_invalid_user_buffer__error_invalid_user_buffer_"></a>STATUS_INVALID_USER_BUFFER (ERROR_INVALID_USER_BUFFER)
<dd>
The input buffer is not aligned correctly for the device or adapter.  This status could only be returned when a driver sends an IOCTL to the storage stack.  This status will not be returned when a user-mode application sends the IOCTL through the DeviceIoControl API as the I/O Manager automatically aligns the buffers.

</dd>
The input buffer is not aligned correctly for the device or adapter.  This status could only be returned when a driver sends an IOCTL to the storage stack.  This status will not be returned when a user-mode application sends the IOCTL through the DeviceIoControl API as the I/O Manager automatically aligns the buffers.</p>The input buffer is not aligned correctly for the device or adapter.  This status could only be returned when a driver sends an IOCTL to the storage stack.  This status will not be returned when a user-mode application sends the IOCTL through the DeviceIoControl API as the I/O Manager automatically aligns the buffers.

<dt><a id="STATUS_INFO_LENGTH_MISMATCH"></a><a id="status_info_length_mismatch"></a>STATUS_INFO_LENGTH_MISMATCH</dt><a id="STATUS_INFO_LENGTH_MISMATCH"></a><a id="status_info_length_mismatch"></a>STATUS_INFO_LENGTH_MISMATCH
<dd>
The input buffer length for the IOCTL is less than sizeof(PERSISTENT_RESERVE_COMMAND) or the size that is specified in the <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a> data structure is less than sizeof(PERSISTENT_RESERVE_COMMAND).

</dd>
The input buffer length for the IOCTL is less than sizeof(PERSISTENT_RESERVE_COMMAND) or the size that is specified in the <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a> data structure is less than sizeof(PERSISTENT_RESERVE_COMMAND).</p>The input buffer length for the IOCTL is less than sizeof(PERSISTENT_RESERVE_COMMAND) or the size that is specified in the <a href="storage.persistent_reserve_command">PERSISTENT_RESERVE_COMMAND</a><b>PERSISTENT_RESERVE_COMMAND</b>PERSISTENT_RESERVE_COMMAND data structure is less than sizeof(PERSISTENT_RESERVE_COMMAND).


## -remarks


## -requirements
<table>
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