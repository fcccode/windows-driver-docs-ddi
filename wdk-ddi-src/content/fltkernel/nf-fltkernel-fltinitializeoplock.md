---
UID: NF.fltkernel.FltInitializeOplock
title: FltInitializeOplock function
author: windows-driver-content
description: The FltInitializeOplock routine initializes an opportunistic lock (oplock) pointer.
old-location: ifsk\fltinitializeoplock.htm
old-project: ifsk
ms.assetid: 9878f614-89dc-4b23-8095-2a8c2b80c79d
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: FltInitializeOplock
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltInitializeOplock
req.alt-loc: fltmgr.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: Fltmgr.sys
req.irql: <= APC_LEVEL
---

# FltInitializeOplock function



## -description
The <b>FltInitializeOplock</b> routine initializes an opportunistic lock (oplock) pointer. 



## -syntax

````
VOID FltInitializeOplock(
  _Out_ POPLOCK Oplock
);
````


## -parameters

### -param Oplock [out]

Caller-supplied pointer variable that receives the initialized opaque oplock pointer. This variable must be initialized to <b>NULL</b> before the initial call to <b>FltInitializeOplock</b>. 


## -returns
None 


## -remarks
When the oplock pointer is no longer needed, it can be uninitialized by calling <a href="ifsk.fltuninitializeoplock">FltUninitializeOplock</a>. The uninitialized oplock pointer can then be initialized for reuse by calling <b>FltInitializeOplock</b>. 

To request an oplock or respond to an oplock break notification, call <a href="ifsk.fltoplockfsctrl">FltOplockFsctrl</a>. 

For detailed information about opportunistic locks, see the Microsoft Windows SDK documentation. 


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
<dt>Fltkernel.h (include Fltkernel.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>FltMgr.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>Fltmgr.sys</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
&lt;= APC_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.fltcheckoplock">FltCheckOplock</a>
</dt>
<dt>
<a href="ifsk.fltcurrentbatchoplock">FltCurrentBatchOplock</a>
</dt>
<dt>
<a href="ifsk.fltoplockfsctrl">FltOplockFsctrl</a>
</dt>
<dt>
<a href="ifsk.fltoplockisfastiopossible">FltOplockIsFastIoPossible</a>
</dt>
<dt>
<a href="ifsk.fltuninitializeoplock">FltUninitializeOplock</a>
</dt>
<dt>
<a href="ifsk.fsrtlinitializeoplock">FsRtlInitializeOplock</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltInitializeOplock routine%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
