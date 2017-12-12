---
UID: NF.ntddk.IoGetTransactionParameterBlock
title: IoGetTransactionParameterBlock function
author: windows-driver-content
description: The IoGetTransactionParameterBlock routine returns the transaction parameter block for a transacted file operation.
old-location: ifsk\iogettransactionparameterblock.htm
old-project: ifsk
ms.assetid: f07919f8-644f-43a4-98d7-d0f1a91d405d
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: IoGetTransactionParameterBlock
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntddk.h
req.include-header: Ntddk.h, Ntifs.h, Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: Windows Vista and later
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoGetTransactionParameterBlock
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

# IoGetTransactionParameterBlock function



## -description
The <b>IoGetTransactionParameterBlock</b> routine returns the transaction parameter block for a transacted file operation. 



## -syntax

````
PTXN_PARAMETER_BLOCK IoGetTransactionParameterBlock(
  _In_ PFILE_OBJECT FileObject
);
````


## -parameters

### -param FileObject [in]

A pointer to a file object for the file. 


## -returns
The <b>IoGetTransactionParameterBlock</b> routine returns a pointer to the <a href="ifsk.txn_parameter_block">TXN_PARAMETER_BLOCK</a> structure if the file operation is transacted, otherwise it returns <b>NULL</b>. 


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
Version

</th>
<td width="70%">
Windows Vista and later

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h, Ntifs.h, or Fltkernel.h)</dt>
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
<a href="ifsk.txn_parameter_block">TXN_PARAMETER_BLOCK</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20IoGetTransactionParameterBlock routine%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
