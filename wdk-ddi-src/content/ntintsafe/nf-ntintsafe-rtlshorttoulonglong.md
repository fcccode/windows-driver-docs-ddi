---
UID: NF.ntintsafe.RtlShortToULongLong
title: RtlShortToULongLong function
author: windows-driver-content
description: Converts a value of type SHORT to a value of type ULONGLONG.
old-location: kernel\rtlshorttoulonglong.htm
old-project: kernel
ms.assetid: DC25A607-F329-44F2-8D26-A6F7E3050A33
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: RtlShortToULongLong
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntintsafe.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlShortToULongLong
req.alt-loc: Ntintsafe.h
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
---

# RtlShortToULongLong function



## -description
Converts a value of type <b>SHORT</b> to a value of type <b>ULONGLONG</b>.



## -syntax

````
NTSTATUS RtlShortToULongLong(
  _In_  SHORT     sOperand,
  _Out_ ULONGLONG *pullResult
);
````


## -parameters

### -param sOperand [in]

The value to be converted.


### -param pullResult [out]

A pointer to the converted value. In the case where the conversion causes a truncation of the original value, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.


## -remarks
This is one of a set of inline functions designed to provide type conversions and perform validity checks with minimal impact on performance.

This function uses the following alternate name:


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntintsafe.h</dt>
</dl>
</td>
</tr>
</table>