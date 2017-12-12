---
UID: NF.wdfhwaccess.WDF_WRITE_REGISTER_BUFFER_ULONG
title: WDF_WRITE_REGISTER_BUFFER_ULONG function
author: windows-driver-content
description: The WDF_WRITE_REGISTER_BUFFER_ULONG function writes a number of ULONG values from a buffer to the specified register.
old-location: wdf\wdf_write_register_buffer_ulong.htm
old-project: wdf
ms.assetid: D52888A2-4CC1-4C5A-890E-5585424339E0
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WDF_WRITE_REGISTER_BUFFER_ULONG
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfhwaccess.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 2.0
req.alt-api: WDF_WRITE_REGISTER_BUFFER_ULONG
req.alt-loc: Wdfhwaccess.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
req.product: Windows 10 or later.
---

# WDF_WRITE_REGISTER_BUFFER_ULONG function



## -description
<p class="CCE_Message">[Applies to UMDF only]

The <b>WDF_WRITE_REGISTER_BUFFER_ULONG</b> function writes a number of ULONG values from a buffer to the specified register.



## -syntax

````
void WDF_WRITE_REGISTER_BUFFER_ULONG(
  _In_ WDFDEVICE Device,
  _In_ PULONG    Register,
  _In_ PULONG    Buffer,
  _In_ ULONG     Count 
);
````


## -parameters

### -param Device [in]

A handle to a framework device object.


### -param Register [in]

A pointer to the register, which must be a mapped range in memory space.


### -param Buffer [in]

A pointer to a buffer from which an array of ULONG values is to be written.


### -param Count  [in]

Specifies the number of ULONG values to write to the register.


## -returns
This function does not return a value.


## -remarks
The size of the buffer must be large enough to contain at least the specified number of bytes.


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
<dt>Wdfhwaccess.h</dt>
</dl>
</td>
</tr>
</table>