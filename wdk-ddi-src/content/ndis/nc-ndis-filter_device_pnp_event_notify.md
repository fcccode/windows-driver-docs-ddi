---
UID: NC.ndis.FILTER_DEVICE_PNP_EVENT_NOTIFY
title: FILTER_DEVICE_PNP_EVENT_NOTIFY
author: windows-driver-content
description: NDIS calls a filter driver's FilterDevicePnPEventNotify function to notify the driver of device Plug and Play (PnP) and Power Management events.Note  You must declare the function by using the FILTER_DEVICE_PNP_EVENT_NOTIFY type.
old-location: netvista\filterdevicepnpeventnotify.htm
old-project: netvista
ms.assetid: dea4ab30-ba1d-4c9c-9f00-e48cc3cc0b46
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: RxNameCacheInitialize
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FilterDevicePnPEventNotify
req.alt-loc: Ndis.h
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

# FILTER_DEVICE_PNP_EVENT_NOTIFY callback



## -description
NDIS calls a filter driver's 
  <i>FilterDevicePnPEventNotify</i> function to notify the driver of device Plug and Play (PnP) and Power
  Management events.



## -prototype

````
FILTER_DEVICE_PNP_EVENT_NOTIFY FilterDevicePnPEventNotify;

VOID FilterDevicePnPEventNotify(
  _In_ NDIS_HANDLE           FilterModuleContext,
  _In_ PNET_DEVICE_PNP_EVENT NetDevicePnPEvent
)
{ ... }
````


## -parameters

### -param FilterModuleContext [in]

A handle to the context area for the filter module. The filter driver created and initialized this
     context area in the 
     <a href="..\ndis\nc-ndis-filter_attach.md">FilterAttach</a> function.


### -param NetDevicePnPEvent [in]

A pointer to a 
     <a href="netvista.net_device_pnp_event">NET_DEVICE_PNP_EVENT</a> structure that
     describes a device Plug and Play event.


## -returns
None


## -remarks
<i>FilterDevicePnPEventNotify</i> is an optional function. If a filter driver does not use device PnP
    requests, it can set the entry point for this function to <b>NULL</b> when it calls the 
    <a href="netvista.ndisfregisterfilterdriver">
    NdisFRegisterFilterDriver</a> function.

<i>FilterDevicePnPEventNotify</i> is similar to a miniport driver's 
    <a href="..\ndis\nc-ndis-miniport_device_pnp_event_notify.md">
    MiniportDevicePnPEventNotify</a> function. Filter drivers can forward these notifications to underlying
    drivers. To forward a request, call the 
    <a href="netvista.ndisfdevicepnpeventnotify">
    NdisFDevicePnPEventNotify</a> function.

NDIS calls 
    <i>FilterDevicePnPEventNotify</i> at IRQL = PASSIVE_LEVEL.

To define a <i>FilterDevicePnPEventNotify</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="https://msdn.microsoft.com/2F3549EF-B50F-455A-BDC7-1F67782B8DCA">Code Analysis for Drivers</a>, <a href="https://msdn.microsoft.com/74feeb16-387c-4796-987a-aff3fb79b556">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.

For example, to define a <i>FilterDevicePnPEventNotify</i> function that is named "MyDevicePnPEventNotify", use the <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> type as shown in this code example:

Then, implement your function as follows:

The <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="https://msdn.microsoft.com/232c4272-0bf0-4a4e-9560-3bceeca8a3e3">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. 


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Supported in NDIS 6.0 and later.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="..\ndis\nc-ndis-filter_attach.md">FilterAttach</a>
</dt>
<dt>
<a href="..\ndis\nc-ndis-miniport_device_pnp_event_notify.md">
   MiniportDevicePnPEventNotify</a>
</dt>
<dt>
<a href="netvista.ndisfdevicepnpeventnotify">NdisFDevicePnPEventNotify</a>
</dt>
<dt>
<a href="netvista.ndisfregisterfilterdriver">NdisFRegisterFilterDriver</a>
</dt>
<dt>
<a href="netvista.ndiswriteeventlogentry">NdisWriteEventLogEntry</a>
</dt>
<dt>
<a href="netvista.net_device_pnp_event">NET_DEVICE_PNP_EVENT</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FILTER_DEVICE_PNP_EVENT_NOTIFY callback function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
