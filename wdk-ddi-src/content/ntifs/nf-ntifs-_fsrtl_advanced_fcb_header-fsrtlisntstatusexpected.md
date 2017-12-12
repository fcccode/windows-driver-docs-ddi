---
UID: NF.ntifs._FSRTL_ADVANCED_FCB_HEADER.FsRtlIsNtstatusExpected
title: FsRtlIsNtstatusExpected function
author: windows-driver-content
description: The FsRtlIsNtstatusExpected routine determines whether the specified exception is handled by the exception filter.
old-location: ifsk\fsrtlisntstatusexpected.htm
old-project: ifsk
ms.assetid: 7d495d67-fe43-43d5-8a35-50c070b78b8d
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: FsRtlIsNtstatusExpected
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FsRtlIsNtstatusExpected
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: Any level
---

# FsRtlIsNtstatusExpected function



## -description
The <b>FsRtlIsNtstatusExpected</b> routine determines whether the specified exception is handled by the exception filter.



## -syntax

````
BOOLEAN FsRtlIsNtstatusExpected(
  _In_ NTSTATUS Exception
);
````


## -parameters

### -param Exception [in]

Status value of the exception.


## -returns
<b>FsRtlIsNtstatusExpected</b> returns <b>TRUE</b> if the status value indicates a nonfatal system error status, <b>FALSE</b> otherwise.


## -remarks
File systems use <b>FsRtlIsNtstatusExpected</b> to determine whether to attempt to handle an exception. 


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
<dt>Ntifs.h (include Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
Any level

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.fsrtlnormalizentstatus">FsRtlNormalizeNtstatus</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FsRtlIsNtstatusExpected routine%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
