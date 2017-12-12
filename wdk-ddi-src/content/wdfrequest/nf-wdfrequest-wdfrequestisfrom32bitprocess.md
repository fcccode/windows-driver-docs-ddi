---
UID: NF.wdfrequest.WdfRequestIsFrom32BitProcess
title: WdfRequestIsFrom32BitProcess function
author: windows-driver-content
description: The WdfRequestIsFrom32BitProcess method checks whether the originator of a specified I/O request is a 32-bit user-mode application.
old-location: wdf\wdfrequestisfrom32bitprocess.htm
old-project: wdf
ms.assetid: 0d55c1e0-0458-414c-afd6-2fa2576ffa4a
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfRequestIsFrom32BitProcess
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfrequest.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfRequestIsFrom32BitProcess
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate, InvalidReqAccess, InvalidReqAccessLocal, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); WUDFx02000.dll (UMDF)
req.dll: 
req.irql: <=DISPATCH_LEVEL
req.product: Windows 10 or later.
---

# WdfRequestIsFrom32BitProcess function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]

The <b>WdfRequestIsFrom32BitProcess</b> method checks whether the originator of a specified I/O request is a 32-bit user-mode application.



## -syntax

````
BOOLEAN WdfRequestIsFrom32BitProcess(
  _In_ WDFREQUEST Request
);
````


## -parameters

### -param Request [in]

A handle to a framework request object.


## -returns
On 64-bit systems,<b>WdfRequestIsFrom32BitProcess</b> returns <b>TRUE</b> if the originator of the current I/O request is a 32-bit user-mode process, and <b>FALSE</b> otherwise. On 32-bit systems, <b>WdfRequestIsFrom32BitProcess</b> always returns <b>TRUE</b>.

A bug check occurs if the driver supplies an invalid object handle.


## -remarks
Drivers can call <b>WdfRequestIsFrom32BitProcess</b> to determine whether an I/O request is likely to contain data elements that need to be converted, or "thunked," before they can be used in a 64-bit driver.

The specified request handle must have been obtained from one of the driver's I/O queues and not from a call to <a href="wdf.wdfrequestcreate">WdfRequestCreate</a>.

The following code example determines if an I/O request came from a 32-bit application.


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
<dt>Wdfrequest.h (include Wdf.h)</dt>
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
&lt;=DISPATCH_LEVEL

</td>
</tr>
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.kmdf_drivercreate">DriverCreate</a>, <a href="devtest.kmdf_invalidreqaccess">InvalidReqAccess</a>, <a href="devtest.kmdf_invalidreqaccesslocal">InvalidReqAccessLocal</a>, <a href="devtest.kmdf_kmdfirql">KmdfIrql</a>, <a href="devtest.kmdf_kmdfirql2">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="wdf.wdfrequestcreate">WdfRequestCreate</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfRequestIsFrom32BitProcess method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
