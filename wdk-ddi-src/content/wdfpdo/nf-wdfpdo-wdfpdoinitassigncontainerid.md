---
UID: NF.wdfpdo.WdfPdoInitAssignContainerID
title: WdfPdoInitAssignContainerID function
author: windows-driver-content
description: The WdfPdoInitAssignContainerID method updates the container ID for a child device.
old-location: wdf\wdfpdoinitassigncontainerid.htm
old-project: wdf
ms.assetid: 603bff9f-fd18-40bd-9b2b-8f013f99ec61
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfPdoInitAssignContainerID
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfpdo.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.9
req.umdf-ver: 
req.alt-api: WdfPdoInitAssignContainerID
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: PASSIVE_LEVEL
req.product: Windows 10 or later.
---

# WdfPdoInitAssignContainerID function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WdfPdoInitAssignContainerID</b> method updates the container ID for a child device.



## -syntax

````
NTSTATUS WdfPdoInitAssignContainerID(
  _In_ PWDFDEVICE_INIT  DeviceInit,
  _In_ PCUNICODE_STRING ContainerID
);
````


## -parameters

### -param DeviceInit [in]

A pointer to a <a href="wdf.wdfdevice_init">WDFDEVICE_INIT</a> structure.


### -param ContainerID [in]

A pointer to a <a href="kernel.unicode_string">UNICODE_STRING</a> structure that contains a container ID string. The driver can allocate the string's buffer from paged pool.


## -returns
If the operation succeeds, the method returns STATUS_SUCCESS. Additional return values include:
<dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl>The driver is initializing an FDO instead of a PDO.
<dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl>The driver could not allocate space to store the container ID string.

 

The method might also return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.


## -remarks
For more information about container IDs, see <a href="devinst.device_identification_strings">Device Identification Strings</a>.

The driver must call <b>WdfPdoInitAssignContainerID</b> before calling <a href="wdf.wdfdevicecreate">WdfDeviceCreate</a>. For more information about calling <b>WdfDeviceCreate</b>, see <a href="wdf.creating_a_framework_device_object">Creating a Framework Device Object</a>.

The following code example initializes a <a href="kernel.unicode_string">UNICODE_STRING</a> structure, stores a Unicode string in the structure, and then registers the Unicode string as the device's container ID.


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
<dt>Wdfpdo.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (see <a href="wdf.framework_library_versioning">Framework Library Versioning</a>.)</dt>
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
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.kmdf_drivercreate">DriverCreate</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.rtlinitunicodestring">RtlInitUnicodeString</a>
</dt>
<dt>
<a href="wdf.wdfpdoinitassigndeviceid">WdfPdoInitAssignDeviceID</a>
</dt>
<dt>
<a href="wdf.wdfpdoinitassigninstanceid">WdfPdoInitAssignInstanceID</a>
</dt>
<dt>
<a href="wdf.wdfpdoinitaddhardwareid">WdfPdoInitAddHardwareID</a>
</dt>
<dt>
<a href="wdf.wdfpdoinitaddcompatibleid">WdfPdoInitAddCompatibleID</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfPdoInitAssignContainerID method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
