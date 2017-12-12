---
UID: NF.ks.KsQueryDevicePnpObject
title: KsQueryDevicePnpObject function
author: windows-driver-content
description: The KsQueryDevicePnpObject function returns the PnP device object that can be stored in the device header. This is the next device object on the PnP stack and is the device object that PnP requests are forwarded to if KsDefaultDispatchPnp is used.
old-location: stream\ksquerydevicepnpobject.htm
old-project: stream
ms.assetid: 207b776a-8f51-4385-a171-a9d0e84e70b5
ms.author: windowsdriverdev
ms.date: 12/6/2017
ms.keywords: KsQueryDevicePnpObject
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsQueryDevicePnpObject
req.alt-loc: Ks.lib,Ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: 
---

# KsQueryDevicePnpObject function



## -description
The <b>KsQueryDevicePnpObject</b> function returns the PnP device object that can be stored in the device header. This is the next device object on the PnP stack and is the device object that PnP requests are forwarded to if <b>KsDefaultDispatchPnp</b> is used.



## -syntax

````
PDEVICE_OBJECT KsQueryDevicePnpObject(
  _In_ KSDEVICE_HEADER Header
);
````


## -parameters

### -param Header [in]

Points to a header previously allocated by <a href="stream.ksallocatedeviceheader">KsAllocateDeviceHeader</a> whose PnP device object is to be returned.


## -returns
The <b>KsQueryDevicePnpObject</b> function returns the previously set PnP device object. If none was set, it returns <b>NULL</b>.


## -remarks


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
Header

</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Ks.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="stream.ksdefaultdispatchpnp">KsDefaultDispatchPnp</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsQueryDevicePnpObject function%20 RELEASE:%20(12/6/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
