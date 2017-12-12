---
UID: NS.WDFIOTARGET._WDF_IO_TARGET_OPEN_PARAMS
title: _WDF_IO_TARGET_OPEN_PARAMS
author: windows-driver-content
description: The WDF_IO_TARGET_OPEN_PARAMS structure contains parameters that the WdfIoTargetOpen method uses.
old-location: wdf\wdf_io_target_open_params.htm
old-project: wdf
ms.assetid: 9539868c-127b-4781-9a73-b56fbfda3233
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: _WDF_IO_TARGET_OPEN_PARAMS, WDF_IO_TARGET_OPEN_PARAMS, *PWDF_IO_TARGET_OPEN_PARAMS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wdfiotarget.h
req.include-header: Wdf.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WDF_IO_TARGET_OPEN_PARAMS
req.alt-loc: wdfiotarget.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Any level
req.product: Windows 10 or later.
---

# _WDF_IO_TARGET_OPEN_PARAMS structure



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]

The <b>WDF_IO_TARGET_OPEN_PARAMS</b> structure contains parameters that the <a href="wdf.wdfiotargetopen">WdfIoTargetOpen</a> method uses.



## -syntax

````
typedef struct _WDF_IO_TARGET_OPEN_PARAMS {
  ULONG                             Size;
  WDF_IO_TARGET_OPEN_TYPE           Type;
  PFN_WDF_IO_TARGET_QUERY_REMOVE    EvtIoTargetQueryRemove;
  PFN_WDF_IO_TARGET_REMOVE_CANCELED EvtIoTargetRemoveCanceled;
  PFN_WDF_IO_TARGET_REMOVE_COMPLETE EvtIoTargetRemoveComplete;
  PDEVICE_OBJECT                    TargetDeviceObject;
  PFILE_OBJECT                      TargetFileObject;
  UNICODE_STRING                    TargetDeviceName;
  ACCESS_MASK                       DesiredAccess;
  ULONG                             ShareAccess;
  ULONG                             FileAttributes;
  ULONG                             CreateDisposition;
  ULONG                             CreateOptions;
  PVOID                             EaBuffer;
  ULONG                             EaBufferLength;
  PLONGLONG                         AllocationSize;
  ULONG                             FileInformation;
  UNICODE_STRING                    FileName;
} WDF_IO_TARGET_OPEN_PARAMS, *PWDF_IO_TARGET_OPEN_PARAMS;
````


## -struct-fields

### -field Size

The size, in bytes, of this structure.


### -field Type

A <a href="wdf.wdf_io_target_open_type">WDF_IO_TARGET_OPEN_TYPE</a>-typed value, which indicates the type of open operation that <a href="wdf.wdfiotargetopen">WdfIoTargetOpen</a> will perform.


### -field EvtIoTargetQueryRemove

A pointer to the driver's <a href="..\wdfiotarget\nc-wdfiotarget-evt_wdf_io_target_query_remove.md">EvtIoTargetQueryRemove</a> event callback function, or <b>NULL</b>.


### -field EvtIoTargetRemoveCanceled

A pointer to the driver's <a href="..\wdfiotarget\nc-wdfiotarget-evt_wdf_io_target_remove_canceled.md">EvtIoTargetRemoveCanceled</a> event callback function, or <b>NULL</b>.


### -field EvtIoTargetRemoveComplete

A pointer to the driver's <a href="..\wdfiotarget\nc-wdfiotarget-evt_wdf_io_target_remove_complete.md">EvtIoTargetRemoveComplete</a> event callback function, or <b>NULL</b>.


### -field TargetDeviceObject

This member is not applicable to UMDF drivers.

<b>KMDF </b>
            If the value of <b>Type</b> is <b>WdfIoTargetOpenUseExistingDevice</b>, this is a pointer to a <a href="kernel.device_object">DEVICE_OBJECT</a> structure that represents the I/O target's device.  If the value of <b>Type</b> is not <b>WdfIoTargetOpenUseExistingDevice</b>, this member is ignored.


### -field TargetFileObject

This member is not applicable to UMDF drivers.

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenUseExistingDevice</b>, this is a pointer to a <a href="kernel.file_object">FILE_OBJECT</a> structure. This structure is included in all of the I/O requests that the driver sends to the I/O target (see <a href="wdf.wdfrequestgetfileobject">WdfRequestGetFileObject</a>). This member is optional and can be <b>NULL</b>. 
            If the value of <b>Type</b> is not <b>WdfIoTargetOpenUseExistingDevice</b>, this member is ignored.


### -field TargetDeviceName

If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this is a <a href="kernel.unicode_string">UNICODE_STRING</a> structure that contains the name of a device, file, or device interface. For information about the format of this name, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff557762">Object Names</a>.

If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.


### -field DesiredAccess

If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this is an <a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a> value. 

If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.

<b>KMDF </b>Possible values include FILE_<i>Xxxx</i>_ACCESS values, such as FILE_ANY_ACCESS, FILE_SPECIAL_ACCESS, FILE_READ_ACCESS, or
    FILE_WRITE_ACCESS, as well as GENERIC_READ,
    GENERIC_WRITE, and GENERIC_ALL.

<b>UMDF </b>The most commonly used values are GENERIC_READ, GENERIC_WRITE, or both (GENERIC_READ | GENERIC_WRITE). Note that <a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a> is a DWORD value. For more information about this member, see the <i>dwDesiredAccess</i> parameter of <a href="http://go.microsoft.com/fwlink/p/?linkid=152795">CreateFile</a> in the Windows SDK.


### -field ShareAccess

If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this is a bitwise OR of the following flags (which are defined in <i>Wdm.h</i>), or zero. <table>
<tr>
<th>ShareAccess flag</th>
<th>Meaning</th>
</tr>
<tr>
<td>
FILE_SHARE_READ

</td>
<td>
The driver does not require exclusive read access to the device.

</td>
</tr>
<tr>
<td>
FILE_SHARE_WRITE

</td>
<td>
The driver does not require exclusive write access to the device.

</td>
</tr>
<tr>
<td>
FILE_SHARE_DELETE

</td>
<td>
The driver does not require exclusive delete access to the device.

</td>
</tr>
</table>
 



<b>UMDF </b>For more information about this member, see the <i>dwShareMode</i> parameter of the <a href="fs.createfile">CreateFile</a> function in the 
    Windows SDK.

A value of zero in <b>ShareAccess</b> indicates that the driver requires exclusive access to the device.


### -field FileAttributes

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this is a bitwise OR of the FILE_ATTRIBUTE_<i>Xxxx</i> flags that are defined in <i>Wdm.h</i>. Most drivers specify FILE_ATTRIBUTE_NORMAL. For more information about these flags, see <a href="kernel.zwcreatefile">ZwCreateFile</a>.

<b>UMDF </b>For more information about 
    this member, see the <i>dwFlagsAndAttributes</i> parameter of the <a href="fs.createfile">CreateFile</a> function in the Windows SDK.

If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.


### -field CreateDisposition

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this value indicates an action for the system to take when opening a file. For a list of possible values, see <a href="kernel.zwcreatefile">ZwCreateFile</a>.

<b>UMDF </b>For more information about 
    this member, see the <i>dwCreationDisposition</i> parameter of the <a href="fs.createfile">CreateFile</a> function in the Windows SDK.

If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.


### -field CreateOptions

This member is not applicable to UMDF drivers.

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this is a bitwise OR of file option flags. For a list of possible flags, see <a href="kernel.zwcreatefile">ZwCreateFile</a>.
             If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.


### -field EaBuffer

This member is not applicable to UMDF drivers.

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this member points to an extended attributes buffer. Typically, drivers supply <b>NULL</b> for this value.
            If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.


### -field EaBufferLength

This member is not applicable to UMDF drivers.

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this is the length of the extended attributes buffer. Typically, drivers supply zero for this value. If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.


### -field AllocationSize

This member is not applicable to UMDF drivers.

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this member specifies the size, in bytes, that the system should initially allocate for the file, if it is creating a new file. This value is optional and can be zero. If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.


### -field FileInformation

This member is not applicable to UMDF drivers.

<b>KMDF </b>If the value of <b>Type</b> is <b>WdfIoTargetOpenByName</b>, this member receives status information when the call to <a href="wdf.wdfiotargetopen">WdfIoTargetOpen</a> returns. The information is one of the following values: FILE_CREATED, FILE_OPENED, FILE_OVERWRITTEN, FILE_SUPERSEDED, FILE_EXISTS, or FILE_DOES_NOT_EXIST. If the value of <b>Type</b> is not <b>WdfIoTargetOpenByName</b>, this member is ignored.


### -field FileName

This member is not applicable to KMDF drivers.

<b>UMDF </b>A UNICODE_STRING structure that contains the 
  name of the file from which to create a file object. This member is
  optional, and is applicable only when the value of <b>Type</b> is <b>WdfIoTargetOpenLocalTargetByFile</b>.   Most drivers specify <b>NULL</b> here unless the lower target supports <a href="https://msdn.microsoft.com/e5312297-849f-4b4e-835d-0ce5295c7ce2">Device Namespace Access</a>. If supplied, the string must not contain any path separator characters 
  (forward slash or backslash).


## -remarks
Drivers should initialize the <b>WDF_IO_TARGET_OPEN_PARAMS</b> structure by calling one of the following functions:


<a href="wdf.wdf_io_target_open_params_init_existing_device">WDF_IO_TARGET_OPEN_PARAMS_INIT_EXISTING_DEVICE</a>, if your driver can identify a target device by supplying a pointer to a <a href="kernel.device_object">DEVICE_OBJECT</a> structure. 


<a href="wdf.wdf_io_target_open_params_init_create_by_name">WDF_IO_TARGET_OPEN_PARAMS_INIT_CREATE_BY_NAME</a>, if the I/O target is a device, file, or device interface, and if your driver can supply the name of the device, file, or device interface. If you specify the name of a file that already exists, the system replaces the existing file. If the file does not exist, the system creates it.


<a href="wdf.wdf_io_target_open_params_init_open_by_name">WDF_IO_TARGET_OPEN_PARAMS_INIT_OPEN_BY_NAME</a>, if the I/O target is a device, file, or device interface, and if your driver can supply the name of the device, file, or device interface. If you specify the name of a file that already exists, the system opens the existing file. If the file does not exist, the open operation fails.


<a href="wdf.wdf_io_target_open_params_init_reopen">WDF_IO_TARGET_OPEN_PARAMS_INIT_REOPEN</a>, if your driver's <a href="..\wdfiotarget\nc-wdfiotarget-evt_wdf_io_target_remove_canceled.md">EvtIoTargetRemoveCanceled</a> callback function is reopening a remote I/O target because the device was not removed.


<a href="wdf.wdf_io_target_open_params_init_open_by_file">WDF_IO_TARGET_OPEN_PARAMS_INIT_OPEN_BY_FILE</a>, if your UMDF driver needs to send driver-created requests to lower targets that require an associated file object.


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
<dt>Wdfiotarget.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a>
</dt>
<dt>
<a href="kernel.device_object">DEVICE_OBJECT</a>
</dt>
<dt>
<a href="..\wdfiotarget\nc-wdfiotarget-evt_wdf_io_target_query_remove.md">EvtIoTargetQueryRemove</a>
</dt>
<dt>
<a href="..\wdfiotarget\nc-wdfiotarget-evt_wdf_io_target_remove_canceled.md">EvtIoTargetRemoveCanceled</a>
</dt>
<dt>
<a href="kernel.file_object">FILE_OBJECT</a>
</dt>
<dt>
<a href="kernel.unicode_string">UNICODE_STRING</a>
</dt>
<dt>
<a href="wdf.wdf_io_target_open_type">WDF_IO_TARGET_OPEN_TYPE</a>
</dt>
<dt>
<a href="wdf.wdfiotargetopen">WdfIoTargetOpen</a>
</dt>
<dt>
<a href="wdf.wdfrequestgetfileobject">WdfRequestGetFileObject</a>
</dt>
<dt>
<a href="kernel.zwcreatefile">ZwCreateFile</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_IO_TARGET_OPEN_PARAMS structure%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
