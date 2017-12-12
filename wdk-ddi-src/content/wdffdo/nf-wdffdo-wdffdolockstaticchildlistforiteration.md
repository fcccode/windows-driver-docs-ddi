---
UID: NF.wdffdo.WdfFdoLockStaticChildListForIteration
title: WdfFdoLockStaticChildListForIteration function
author: windows-driver-content
description: The WdfFdoLockStaticChildListForIteration method prepares the framework for retrieving items from the static child list that belongs to a specified parent device.
old-location: wdf\wdffdolockstaticchildlistforiteration.htm
old-project: wdf
ms.assetid: 79ff278c-a30e-49f6-9146-badf24970de2
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfFdoLockStaticChildListForIteration
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdffdo.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfFdoLockStaticChildListForIteration
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

# WdfFdoLockStaticChildListForIteration function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WdfFdoLockStaticChildListForIteration</b> method prepares the framework for retrieving items from the static child list that belongs to a specified parent device. 



## -syntax

````
VOID WdfFdoLockStaticChildListForIteration(
  _In_ WDFDEVICE Fdo
);
````


## -parameters

### -param Fdo [in]

A handle to a framework device object that represents the parent device.


## -returns
None.

A system bug check occurs if the driver supplies an invalid object handle.


## -remarks
Bus drivers that use static bus enumeration can call <b>WdfFdoLockStaticChildListForIteration</b>. 

After calling <b>WdfFdoLockStaticChildListForIteration</b>, the driver can repeatedly call <a href="wdf.wdffdoretrievenextstaticchild">WdfFdoRetrieveNextStaticChild</a> to obtain information about each child device in the child list. 

After the driver has finished calling <a href="wdf.wdffdoretrievenextstaticchild">WdfFdoRetrieveNextStaticChild</a>, it must call <a href="wdf.wdffdounlockstaticchildlistfromiteration">WdfFdoUnlockStaticChildListFromIteration</a>.

If the driver makes changes to the child list after calling <b>WdfFdoLockStaticChildListForIteration</b>, the framework stores all of the changes and notifies the Plug and Play (PnP) manager of the changes when the driver calls <a href="wdf.wdffdounlockstaticchildlistfromiteration">WdfFdoUnlockStaticChildListFromIteration</a>.

The driver can nest calls to <b>WdfFdoLockStaticChildListForIteration</b> and <a href="wdf.wdffdounlockstaticchildlistfromiteration">WdfFdoUnlockStaticChildListFromIteration</a>. If the driver nests calls to these methods, the framework stores all of the changes until the last call to <b>WdfFdoUnlockStaticChildListFromIteration</b>.

For more information about static child lists, see <a href="wdf.static_enumeration">Static Enumeration</a>.

For a code example that uses <b>WdfFdoLockStaticChildListForIteration</b>, see <a href="wdf.wdffdoretrievenextstaticchild">WdfFdoRetrieveNextStaticChild</a>.


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
<dt>Wdffdo.h (include Wdf.h)</dt>
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
<a href="wdf.wdffdounlockstaticchildlistfromiteration">WdfFdoUnlockStaticChildListFromIteration</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfFdoLockStaticChildListForIteration method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
