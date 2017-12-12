---
UID: NF.wdfpdo.WdfPdoInitAddDeviceText
title: WdfPdoInitAddDeviceText function
author: windows-driver-content
description: The WdfPdoInitAddDeviceText method adds a device description and device location to a device, for a specified locale.
old-location: wdf\wdfpdoinitadddevicetext.htm
old-project: wdf
ms.assetid: e46a9aee-8d96-41f5-b0f9-01846fefe4cb
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfPdoInitAddDeviceText
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfpdo.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfPdoInitAddDeviceText
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: ChildDeviceInitAPI, DriverCreate, InitFreeDeviceCallback, InitFreeDeviceCreate, InitFreeNull, KmdfIrql, KmdfIrql2, PdoDeviceInitAPI, PdoInitFreeDeviceCallback, PdoInitFreeDeviceCreate
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

# WdfPdoInitAddDeviceText function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WdfPdoInitAddDeviceText</b> method adds a device description and device location to a device, for a specified locale.



## -syntax

````
NTSTATUS WdfPdoInitAddDeviceText(
  _In_ PWDFDEVICE_INIT  DeviceInit,
  _In_ PCUNICODE_STRING DeviceDescription,
  _In_ PCUNICODE_STRING DeviceLocation,
  _In_ LCID             LocaleId
);
````


## -parameters

### -param DeviceInit [in]

A pointer to a <a href="wdf.wdfdevice_init">WDFDEVICE_INIT</a> structure.


### -param DeviceDescription [in]

A pointer to a <a href="kernel.unicode_string">UNICODE_STRING</a> structure that contains a device description, formatted for the given locale. The driver can allocate the string's buffer from paged pool.


### -param DeviceLocation [in]

A pointer to a <a href="kernel.unicode_string">UNICODE_STRING</a> structure that contains a description of the location on the bus where the parent device found the child. The driver can allocate the string's buffer from paged pool.


### -param LocaleId [in]

A locale identifier (LCID) that represents the locale of the Unicode strings. For more information, see <a href="intl.locale_identifiers">Locale Identifiers</a>.


## -returns
If the operation succeeds, the method returns STATUS_SUCCESS. Additional return values include:
<dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl>The driver is initializing an FDO instead of a PDO.
<dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl>The driver could not allocate space to store the strings.

 

The method might also return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.


## -remarks
The framework stores the specified device text and passes it to the PnP manager in response to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff551674">IRP_MN_QUERY_DEVICE_TEXT</a> request. The text that you supply should help the user to identify the device. The PnP manager sometimes displays the text while attempting to install additional drivers for the device.

You can call <b>WdfPdoInitAddDeviceText</b> multiple times, adding device text for multiple locales. When the system displays the text, it chooses the text that matches the current locale, if available. Otherwise, it will use the string for the default locale. The driver can specify the driver's default locale by calling <a href="wdf.wdfpdoinitsetdefaultlocale">WdfPdoInitSetDefaultLocale</a>.

The driver must call <b>WdfPdoInitAddDeviceText</b> before calling <a href="wdf.wdfdevicecreate">WdfDeviceCreate</a>. For more information about calling <b>WdfDeviceCreate</b>, see <a href="wdf.creating_a_framework_device_object">Creating a Framework Device Object</a>.

The following code example provides Unicode strings for a device's location and description. The description includes an instance number. For a complete example that uses <b>WdfPdoInitAddDeviceText</b>, see the <a href="wdf.sample_kmdf_drivers">KbFiltr</a> sample driver.


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
<a href="devtest.kmdf_childdeviceinitapi">ChildDeviceInitAPI</a>, <a href="devtest.kmdf_drivercreate">DriverCreate</a>, <a href="devtest.kmdf_initfreedevicecallback">InitFreeDeviceCallback</a>, <a href="devtest.kmdf_initfreedevicecreate">InitFreeDeviceCreate</a>, <a href="devtest.kmdf_initfreenull">InitFreeNull</a>, <a href="devtest.kmdf_kmdfirql">KmdfIrql</a>, <a href="devtest.kmdf_kmdfirql2">KmdfIrql2</a>, <a href="devtest.kmdf_pdodeviceinitapi">PdoDeviceInitAPI</a>, <a href="devtest.kmdf_pdoinitfreedevicecallback">PdoInitFreeDeviceCallback</a>, <a href="devtest.kmdf_pdoinitfreedevicecreate">PdoInitFreeDeviceCreate</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="wdf.wdfpdoinitsetdefaultlocale">WdfPdoInitSetDefaultLocale</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfPdoInitAddDeviceText method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
