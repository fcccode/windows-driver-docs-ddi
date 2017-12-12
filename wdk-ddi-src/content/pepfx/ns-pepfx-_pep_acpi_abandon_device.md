---
UID: NS.PEPFX._PEP_ACPI_ABANDON_DEVICE
title: _PEP_ACPI_ABANDON_DEVICE
author: windows-driver-content
description: The PEP_ACPI_ABANDON_DEVICE structure indicates whether the platform extension plug-in (PEP) accepts ownership of an abandoned device.
old-location: kernel\pep_acpi_abandon_device.htm
old-project: kernel
ms.assetid: A8D0FA24-664F-4A2B-BF08-300D6E30F7E2
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: _PEP_ACPI_ABANDON_DEVICE, *PPEP_ACPI_ABANDON_DEVICE, PEP_ACPI_ABANDON_DEVICE
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
req.alt-api: PEP_ACPI_ABANDON_DEVICE
req.alt-loc: pepfx.h
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

# _PEP_ACPI_ABANDON_DEVICE structure



## -description
The <b>PEP_ACPI_ABANDON_DEVICE</b> structure indicates whether the platform extension plug-in (PEP) accepts ownership of an abandoned device.



## -syntax

````
typedef struct _PEP_ACPI_ABANDON_DEVICE {
  PANSI_STRING AcpiDeviceName;
  BOOLEAN      DeviceAccepted;
} PEP_ACPI_ABANDON_DEVICE, *PPEP_ACPI_ABANDON_DEVICE;
````


## -struct-fields

### -field AcpiDeviceName

[in] A pointer to an <a href="kernel.ansi_string">ANSI_STRING</a> structure that contains the fully qualified BIOS name for the device. This name specifies the the path and name of the device in the ACPI namespace. For more information, see <a href="https://msdn.microsoft.com/fe0553df-a5b9-46c4-8e1d-8b89a7d4ad67">Enumerating Child Devices and Control Methods</a>.


### -field DeviceAccepted

[out] Whether the PEP claims ownership of the device specified by the <b>AcpiDeviceName</b> member. Set to TRUE if the PEP claims ownership, and to FALSE if the PEP does not own the device.


## -remarks
This structure is used by the <a href="kernel.pep_notify_acpi_abandon_device">PEP_NOTIFY_ACPI_ABANDON_DEVICE</a> notification. This notification provides an opportunity for the PEP to clean up any remaining device state after the operating system has abandoned the device. The <b>AcpiDeviceName</b> member of the structure contains an input value that is supplied by the Windows <a href="kernel.power_management_framework__pofx__routines">power management framework</a> (PoFx). The <b>DeviceAccepted</b> member contains an output value that the PEP writes to the structure in response to the notification.


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
<a href="kernel.ansi_string">ANSI_STRING</a>
</dt>
<dt>
<a href="kernel.pep_notify_acpi_abandon_device">PEP_NOTIFY_ACPI_ABANDON_DEVICE</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20PEP_ACPI_ABANDON_DEVICE structure%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
