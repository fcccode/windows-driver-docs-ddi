---
UID: NF.wdfpdo.WdfPdoRequestEject
title: WdfPdoRequestEject function
author: windows-driver-content
description: The WdfPdoRequestEject method informs the framework that a specified device is about to be ejected from its docking station.
old-location: wdf\wdfpdorequesteject.htm
old-project: wdf
ms.assetid: 40cd83c0-701a-436f-a3c3-b0ab14848a92
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfPdoRequestEject
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
req.alt-api: WdfPdoRequestEject
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
req.irql: <= DISPATCH_LEVEL
req.product: Windows 10 or later.
---

# WdfPdoRequestEject function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WdfPdoRequestEject</b> method informs the framework that a specified device is about to be ejected from its docking station.



## -syntax

````
VOID WdfPdoRequestEject(
  _In_ WDFDEVICE Device
);
````


## -parameters

### -param Device [in]

A handle to a framework device object that represents the device's physical device object (PDO).


## -returns
None.

A system bug check occurs if the driver supplies an invalid object handle.


## -remarks
A bus driver can call <b>WdfPdoRequestEject</b> or <a href="wdf.wdfchildlistrequestchildeject">WdfChildListRequestChildEject</a> to report that the driver has detected an attempt to eject one of its enumerated child devices from the device's docking station. For example, the driver might detect that a user has pushed an eject button. 

If the framework device object for the device's PDO is available, the driver can call <b>WdfPdoRequestEject</b>. If the driver is using dynamic bus enumeration and if the device's identification description is available, the driver can call <a href="wdf.wdfchildlistrequestchildeject">WdfChildListRequestChildEject</a>.

For more information about <b>WdfPdoRequestEject</b> and <a href="wdf.wdfchildlistrequestchildeject">WdfChildListRequestChildEject</a>, see <a href="wdf.supporting_ejectable_devices">Supporting Ejectable Devices</a>.

The following code example searches a list of child devices to find one that matches a specified serial number. When the example finds the correct child, it calls <b>WdfPdoRequestEject</b> to indicate that the child is being ejected. This example was taken from the <a href="wdf.sample_kmdf_drivers">Toaster</a> sample bus driver and simplified.


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
&lt;= DISPATCH_LEVEL

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
<a href="wdf.wdffdolockstaticchildlistforiteration">WdfFdoLockStaticChildListForIteration</a>
</dt>
<dt>
<a href="wdf.wdffdoretrievenextstaticchild">WdfFdoRetrieveNextStaticChild</a>
</dt>
<dt>
<a href="wdf.wdffdounlockstaticchildlistfromiteration">WdfFdoUnlockStaticChildListFromIteration</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfPdoRequestEject method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
