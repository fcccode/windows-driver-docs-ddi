---
UID: NS.PEPFX._PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES
title: _PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES
author: windows-driver-content
description: The PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES structure contains a list of raw resources that are needed to control power to the device.
old-location: kernel\pep_acpi_query_device_control_resources.htm
old-project: kernel
ms.assetid: 7DBDC5A7-1BF4-41B6-A72E-1B53CAC06823
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: _PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES, *PPEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES, PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: pepfx.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Supported starting with Windows 10.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES
req.alt-loc: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
---

# _PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES structure



## -description
The <b>PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES</b> structure contains a list of raw  resources that are needed to control power to the device.



## -syntax

````
struct PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES {
  PEPHANDLE            DeviceHandle;
  ULONG                RequestFlags;
  NTSTATUS             Status;
  SIZE_T               BiosResourcesSize;
  ACPI_METHOD_ARGUMENT BiosResources;
};
````


## -struct-fields

### -field DeviceHandle

[in] A PEPHANDLE value that identifies the device's registration for ACPI services. The platform extension plug-in (PEP) supplied this handle in response to a previous <a href="kernel.pep_notify_acpi_register_device">PEP_NOTIFY_ACPI_REGISTER_DEVICE</a> notification.


### -field RequestFlags

[in] A set of input flags. No flags are currently defined for this member, which is always set to PEP_ACPI_QDCR_FLAG_NONE (0x0).


### -field Status

[out] An NTSTATUS value that indicates the status of this query. Set this member to STATUS_SUCCESS if the PEP succeeded in providing the requested list of resources. Set to STATUS_BUFFER_TOO_SMALL to indicate that the output buffer is not large enough to contain the resource list.


### -field BiosResourcesSize

[in, out] On input, the size, in bytes, of the buffer allocated for the <b>BiosResources</b> member. This buffer size includes any associated data that might follow this member.

If this buffer is not large enough to contain the <b>ACPI_METHOD_ARGUMENT</b> structure and its associated data, the PEP overwrites the input value of <b>BiosResourcesSize</b> with the required size and sets the <b>Status</b> member to STATUS_BUFFER_TOO_SMALL.


### -field BiosResources

[in] An output buffer to which the PEP writes an <a href="acpi.acpi_method_argument">ACPI_METHOD_ARGUMENT</a> structure that contains the requested resource list. The <b>Data</b> member of this structure is the first member in an array that might extend past the end of the structure. The buffer size specified by <b>BiosResourcesSize</b> includes both the <b>ACPI_METHOD_ARGUMENT</b> structure and any <b>Data</b> array elements that follow this structure. For more information, see TBD.


## -remarks
This structure is used by the <a href="kernel.pep_notify_acpi_query_device_control_resources">PEP_NOTIFY_ACPI_QUERY_DEVICE_CONTROL_RESOURCES</a> notification. The <b>RequestFlags</b>, <b>BiosResourcesSize</b>, and <b>BiosResources</b> members of the structure contain input values supplied by the Windows <a href="kernel.power_management_framework__pofx__routines">power management framework</a> (PoFx) when this notification is sent. If the <b>BiosResourcesSize</b> input value is too small, the PEP should overwrite this value. The <b>Status</b> member contains an output value that the PEP writes to this structure in response to the notification.

If the input value specified in the <b>BiosResourcesSize</b> member is less than the required size, the PEP overwrites the <b>BiosResourcesSize</b> input value with the required size, and sets the <b>Status</b> member to STATUS_BUFFER_TOO_SMALL. In response, PoFx will try to allocate a buffer of the required size and send a second <b>PEP_NOTIFY_ACPI_QUERY_DEVICE_CONTROL_RESOURCES</b> notification to the PEP for this device.


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Supported starting with Windows 10.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Pepfx.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="acpi.acpi_method_argument">ACPI_METHOD_ARGUMENT</a>
</dt>
<dt>
<a href="kernel.pep_notify_acpi_query_device_control_resources">PEP_NOTIFY_ACPI_QUERY_DEVICE_CONTROL_RESOURCES</a>
</dt>
<dt>
<a href="kernel.pep_notify_acpi_register_device">PEP_NOTIFY_ACPI_REGISTER_DEVICE</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20PEP_ACPI_QUERY_DEVICE_CONTROL_RESOURCES structure%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
