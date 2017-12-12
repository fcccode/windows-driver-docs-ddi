---
UID: NF.wdfwmi.WdfWmiProviderGetTracingHandle
title: WdfWmiProviderGetTracingHandle function
author: windows-driver-content
description: The WdfWmiProviderGetTracingHandle method returns a handle to the event logger of a WPP software tracing session.
old-location: wdf\wdfwmiprovidergettracinghandle.htm
old-project: wdf
ms.assetid: 44ab1cf3-abd3-4100-a6ad-51f2322881b1
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfWmiProviderGetTracingHandle
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfwmi.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfWmiProviderGetTracingHandle
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <=DISPATCH_LEVEL
req.product: Windows 10 or later.
---

# WdfWmiProviderGetTracingHandle function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WdfWmiProviderGetTracingHandle</b> method returns a handle to the event logger of a <a href="https://msdn.microsoft.com/dab776b3-bac9-4157-a530-6e48868ba900">WPP software tracing</a> session. 



## -syntax

````
ULONGLONG WdfWmiProviderGetTracingHandle(
  _In_ WDFWMIPROVIDER WmiProvider
);
````


## -parameters

### -param WmiProvider [in]

A handle to a WMI provider object that the driver obtained by calling <a href="wdf.wdfwmiprovidercreate">WdfWmiProviderCreate</a> or <a href="wdf.wdfwmiinstancegetprovider">WdfWmiInstanceGetProvider</a>.


## -returns
<b>WdfWmiProviderGetTracingHandle</b> returns a handle to the event tracing logger.

A bug check occurs if the driver supplies an invalid object handle.




## -remarks
If a driver sets the <b>WdfWmiProviderTracing</b> flag in the <b>Flags</b> member of the WMI provider object's <a href="wdf.wdf_wmi_provider_config">WDF_WMI_PROVIDER_CONFIG</a> structure, it can call <b>WdfWmiProviderGetTracingHandle</b> to obtain a tracing handle after a provider instance has been registered. The driver can use the tracing handle as input to the <a href="kernel.wmitracemessage">WmiTraceMessage</a> routine.

For more information about the <b>WdfWmiProviderGetTracingHandle</b> method, see <a href="wdf.supporting_wmi_data_blocks_and_events_in_your_driver#supporting_wmi_event_tracing#supporting_wmi_event_tracing">Supporting WMI Event Tracing</a>. For more information about WMI, see <a href="wdf.supporting_wmi_in_kmdf_drivers">Supporting WMI in Framework-Based Drivers</a>.

The following code example obtains a handle to a WPP tracing session's event logger.


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
<dt>Wdfwmi.h (include Wdf.h)</dt>
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
&lt;=DISPATCH_LEVEL

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
<a href="wdf.wdf_wmi_provider_config">WDF_WMI_PROVIDER_CONFIG</a>
</dt>
<dt>
<a href="wdf.wdfwmiinstancegetprovider">WdfWmiInstanceGetProvider</a>
</dt>
<dt>
<a href="wdf.wdfwmiprovidercreate">WdfWmiProviderCreate</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfWmiProviderGetTracingHandle method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
