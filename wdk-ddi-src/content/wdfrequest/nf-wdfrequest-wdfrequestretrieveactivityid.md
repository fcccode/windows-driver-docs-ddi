---
UID: NF.wdfrequest.WdfRequestRetrieveActivityId
title: WdfRequestRetrieveActivityId function
author: windows-driver-content
description: The WdfRequestRetrieveActivityId method retrieves the current activity identifier associated with an I/O request.
old-location: wdf\wdfrequestretrieveactivityid.htm
old-project: wdf
ms.assetid: 6E38514E-75BD-4F98-AD12-FA4E31654C3E
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WdfRequestRetrieveActivityId
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfrequest.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 2.0
req.alt-api: WdfRequestRetrieveActivityId
req.alt-loc: WUDFx02000.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: WUDFx02000.lib
req.dll: WUDFx02000.dll; TBD
req.irql: PASSIVE_LEVEL
req.product: Windows 10 or later.
---

# WdfRequestRetrieveActivityId function



## -description
<p class="CCE_Message">[Applies to UMDF only]

The <b>WdfRequestRetrieveActivityId</b> method retrieves the current activity identifier associated with an I/O request.



## -syntax

````
NTSTATUS WdfRequestRetrieveActivityId(
  _In_  WDFREQUEST Request,
  _Out_ LPGUID     ActivityId
);
````


## -parameters

### -param Request [in]

A handle to a framework request object.


### -param ActivityId [out]

A pointer to a location to store the retrieved GUID.


## -returns
If the operation succeeds, <b>WdfRequestRetrieveActivityId</b> returns STATUS_SUCCESS. Additional return values include:
<dl>
<dt><b>STATUS_NOT_FOUND</b></dt>
</dl>No activity ID is associated with the request.

 

The method might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.


## -remarks
Requests reflected from kernel mode have an activity identifier available only if the Kernel Trace provider is enabled or if the UMDF driver called <a href="wdf.wdfrequestsetactivityid">WdfRequestSetActivityId</a> after receiving the request. For more information about Event Tracing for Windows (ETW), see <a href="etw.event_tracing_portal">Event Tracing</a>.

Requests initiated by the UMDF driver have an activity identifier available only if the UMDF driver previously called  <a href="wdf.wdfrequestsetactivityid">WdfRequestSetActivityId</a>.

The framework does not clear a request's activity identifier when the driver calls <a href="wdf.wdfrequestreuse">WdfRequestReuse</a>.

For more information about activity identifiers, see <a href="wdf.using_activity_identifiers">Using Activity Identifiers</a>.


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
Minimum support

</th>
<td width="70%">
Windows 8.1

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
<dt>WUDFx02000.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>WUDFx02000.dll; </dt>
<dt>TBD</dt>
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
<a href="wdf.wdfrequestsetactivityid">WdfRequestSetActivityId</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfRequestRetrieveActivityId method%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
