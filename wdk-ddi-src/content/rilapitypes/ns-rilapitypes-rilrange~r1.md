---
UID: NS.RILAPITYPES.RILRANGE~R1
title: RILRANGE
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilrange_2.htm
old-project: netvista
ms.assetid: f14aa2bc-1eeb-4c17-836a-52046ba388f1
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: RILRANGE, RILRANGE, *LPRILRANGE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: rilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILRANGE
req.alt-loc: rilapitypes.h
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

# RILRANGE structure



## -description
This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. 



## -syntax

````
typedef struct _RILRANGE {
  DWORD  dwMinValue;
  DWORD  dwMaxValue;
} RILRANGE, RILRANGE;
````


## -struct-fields

### -field dwMinValue


### -field dwMaxValue


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Rilapitypes.h</dt>
</dl>
</td>
</tr>
</table>