---
UID: NF.ntddk.ExRaiseDatatypeMisalignment
title: ExRaiseDatatypeMisalignment function
author: windows-driver-content
description: The ExRaiseDatatypeMisalignment routine can be used with structured exception handling to throw a driver-determined exception for a misaligned data type that occurs when a driver processes I/O requests.
old-location: kernel\exraisedatatypemisalignment.htm
old-project: kernel
ms.assetid: 5c8bfd13-31e0-461f-93d2-53ce15c53cdb
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: ExRaiseDatatypeMisalignment
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ExRaiseDatatypeMisalignment
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IrqlExPassive, PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL (see Remarks section)
---

# ExRaiseDatatypeMisalignment function



## -description
The <b>ExRaiseDatatypeMisalignment</b> routine can be used with structured exception handling to throw a driver-determined exception for a misaligned data type that occurs when a driver processes I/O requests.



## -syntax

````
VOID ExRaiseDatatypeMisalignment(void);
````


## -parameters


## -returns
None

None

None


## -remarks
<b>ExRaiseDatatypeMisalignment</b> raises an exception with the exception code set to STATUS_DATATYPE_MISALIGNMENT.

Because <b>ExRaiseDatatypeMisalignment</b> can only be used at IRQL = PASSIVE_LEVEL, only high-level drivers typically use this routine — for example, file system drivers.


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
Version

</th>
<td width="70%">
Available starting with Windows 2000.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h)</dt>
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
PASSIVE_LEVEL (see Remarks section)

</td>
</tr>
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.wdm_irqlexpassive">IrqlExPassive</a>, <a href="devtest.wdm_powerirpddis">PowerIrpDDis</a>, <a href="devtest.storport_hwstorportprohibitedddis">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.exraiseaccessviolation">ExRaiseAccessViolation</a>
</dt>
<dt>
<a href="kernel.exraisestatus">ExRaiseStatus</a>
</dt>
<dt>
<a href="kernel.ioallocateerrorlogentry">IoAllocateErrorLogEntry</a>
</dt>
<dt>
<a href="kernel.kebugcheckex">KeBugCheckEx</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ExRaiseDatatypeMisalignment routine%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
