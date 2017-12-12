---
UID: NF.wdfregistry.WdfRegistryQueryValue
title: WdfRegistryQueryValue function
author: windows-driver-content
description: The WdfRegistryQueryValue method retrieves the data that is currently assigned to a specified registry value.
old-location: wdf\wdfregistryqueryvalue.htm
old-project: wdf
ms.assetid: 1d61e35a-64c6-42e0-b20d-969ded8b9750
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfRegistryQueryValue
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfregistry.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfRegistryQueryValue
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); WUDFx02000.dll (UMDF)
req.dll: 
req.irql: PASSIVE_LEVEL
req.product: Windows 10 or later.
---

# WdfRegistryQueryValue function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]

The <b>WdfRegistryQueryValue</b> method retrieves the data that is currently assigned to a specified registry value.



## -syntax

````
NTSTATUS WdfRegistryQueryValue(
  _In_      WDFKEY           Key,
  _In_      PCUNICODE_STRING ValueName,
  _In_      ULONG            ValueLength,
  _Out_opt_ PVOID            Value,
  _Out_opt_ PULONG           ValueLengthQueried,
  _Out_opt_ PULONG           ValueType
);
````


## -parameters

### -param Key [in]

A handle to a registry-key object that represents an opened registry key.


### -param ValueName [in]

A pointer to a <a href="kernel.unicode_string">UNICODE_STRING</a> structure that contains a value name. 


### -param ValueLength [in]

The length, in bytes, of the buffer that <i>Value</i> points to.


### -param Value [out, optional]

A pointer to a driver-allocated buffer that receives the registry value's data. If this pointer is <b>NULL</b>, <b>WdfRegistryQueryValue</b> retrieves the data length but not the data.


### -param ValueLengthQueried [out, optional]

A pointer to a location that receives the registry value's data length. This pointer is optional and can be <b>NULL</b>.


### -param ValueType [out, optional]

A pointer to a location that receives the registry value's data type. For a list of data type values, see the <b>Type</b> member of <a href="kernel.key_value_basic_information">KEY_VALUE_BASIC_INFORMATION</a>. This pointer is optional and can be <b>NULL</b>.


## -returns
<b>WdfRegistryQueryValue</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, the method might return one of the following values:
<dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl>
<a href="wdf.wdfregistryqueryvalue">WdfRegistryQueryValue</a> was not called at IRQL = PASSIVE_LEVEL. 
<dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl>An invalid parameter was specified.
<dl>
<dt><b>STATUS_ACCESS_DENIED</b></dt>
</dl>The driver did not open the registry key with KEY_QUERY_VALUE, KEY_READ, or KEY_ALL_ACCESS access.
<dl>
<dt><b>STATUS_BUFFER_OVERFLOW</b></dt>
</dl>The buffer that the <i>Value</i> parameter points to is too small, and only partial data has been written to the buffer.
<dl>
<dt><b>STATUS_BUFFER_OVERFLOW</b></dt>
</dl>The <i>Value</i> buffer is too small, and no data has been written to the buffer.
<dl>
<dt><b>STATUS_OBJECT_NAME_NOT_FOUND</b></dt>
</dl>The registry value was not available.

 

This method also might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.

A bug check occurs if the driver supplies an invalid object handle.




## -remarks
For more information about registry-key objects, see <a href="wdf.using_the_registry_in_kmdf_drivers">Using the Registry in Framework-Based Drivers</a>.

The following code example opens a device's hardware key and retrieves the data that is assigned to the <b>NumberOfToasters</b> value, which is stored under the device's hardware key.


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
<dt>Wdfregistry.h (include Wdf.h)</dt>
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
PASSIVE_LEVEL

</td>
</tr>
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.kmdf_drivercreate">DriverCreate</a>, <a href="devtest.kmdf_kmdfirql">KmdfIrql</a>, <a href="devtest.kmdf_kmdfirql2">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.key_value_basic_information">KEY_VALUE_BASIC_INFORMATION</a>
</dt>
<dt>
<a href="kernel.unicode_string">UNICODE_STRING</a>
</dt>
<dt>
<a href="wdf.wdfdeviceopenregistrykey">WdfDeviceOpenRegistryKey</a>
</dt>
<dt>
<a href="wdf.wdfregistryquerymemory">WdfRegistryQueryMemory</a>
</dt>
<dt>
<a href="wdf.wdfregistryquerymultistring">WdfRegistryQueryMultiString</a>
</dt>
<dt>
<a href="wdf.wdfregistryquerystring">WdfRegistryQueryString</a>
</dt>
<dt>
<a href="wdf.wdfregistryqueryulong">WdfRegistryQueryULong</a>
</dt>
<dt>
<a href="wdf.wdfregistryqueryunicodestring">WdfRegistryQueryUnicodeString</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfRegistryQueryValue method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
