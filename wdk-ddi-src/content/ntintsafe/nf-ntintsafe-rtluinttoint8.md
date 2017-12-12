---
UID: NF.ntintsafe.RtlUIntToInt8
title: RtlUIntToInt8 function
author: windows-driver-content
description: Converts a value of type UINT to a value of type INT8.
old-location: kernel\rtluinttoint8.htm
old-project: kernel
ms.assetid: 8E9CA6F9-D0F1-4315-8A1B-CFA46B8458D7
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: RtlUIntToInt8
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
req.alt-api: RtlUIntToInt8
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

# RtlUIntToInt8 function



## -description
Converts a value of type <b>UINT</b> to a value of type <b>INT8</b>.



## -syntax

````
NTSTATUS RtlUIntToInt8(
  _In_  UINT uOperand,
  _Out_ INT8 *pi8Result
);
````


## -parameters

### -param uOperand [in]

The value to be converted.


### -param pi8Result [out]

A pointer to the converted value. In the case where the conversion causes a truncation of the original value, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.


## -remarks
This is one of a set of inline functions designed to provide type conversions and perform validity checks with minimal impact on performance.


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