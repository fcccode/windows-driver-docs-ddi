---
UID: NS.KS.KSPIN_MDL_CACHING_NOTIFICATION
title: KSPIN_MDL_CACHING_NOTIFICATION
author: windows-driver-content
description: This structure is used internally by the operating system.
old-location: stream\kspin_mdl_caching_notification.htm
old-project: stream
ms.assetid: 93BAAF88-3F82-4E32-B403-4028ECF21F9A
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: KSPIN_MDL_CACHING_NOTIFICATION, KSPIN_MDL_CACHING_NOTIFICATION, PKSPIN_MDL_CACHING_NOTIFICATION, *PKSPIN_MDL_CACHING_NOTIFICATION
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: ks.h
req.include-header: Ks.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSPIN_MDL_CACHING_NOTIFICATION
req.alt-loc: ks.h
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

# KSPIN_MDL_CACHING_NOTIFICATION structure



## -description
This structure is used internally by the operating system.



## -syntax

````
typedef struct {
  KSPIN_MDL_CACHING_EVENT Event;
  PVOID                   Buffer;
} KSPIN_MDL_CACHING_NOTIFICATION, *PKSPIN_MDL_CACHING_NOTIFICATION;
````


## -struct-fields

### -field Event

This member is used internally by the operating system.


### -field Buffer

This member is used internally by the operating system.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
</table>