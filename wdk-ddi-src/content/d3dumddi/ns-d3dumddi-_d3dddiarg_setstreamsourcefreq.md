---
UID: NS.D3DUMDDI._D3DDDIARG_SETSTREAMSOURCEFREQ
title: _D3DDDIARG_SETSTREAMSOURCEFREQ
author: windows-driver-content
description: The D3DDDIARG_SETSTREAMSOURCEFREQ structure describes how the frequency divisor for a portion of the vertex stream source is set.
old-location: display\d3dddiarg_setstreamsourcefreq.htm
old-project: display
ms.assetid: 16bf65c7-26b0-404c-97c0-48eeb7c10b03
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _D3DDDIARG_SETSTREAMSOURCEFREQ, D3DDDIARG_SETSTREAMSOURCEFREQ
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DDDIARG_SETSTREAMSOURCEFREQ
req.alt-loc: d3dumddi.h
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

# _D3DDDIARG_SETSTREAMSOURCEFREQ structure



## -description
The D3DDDIARG_SETSTREAMSOURCEFREQ structure describes how the frequency divisor for a portion of the vertex stream source is set. 



## -syntax

````
typedef struct _D3DDDIARG_SETSTREAMSOURCEFREQ {
  UINT Stream;
  UINT Divider;
} D3DDDIARG_SETSTREAMSOURCEFREQ;
````


## -struct-fields

### -field Stream

[in] The stream source to divide, which is a value between zero and the maximum number of streams that are specified by the driver.


### -field Divider

[in] The frequency divisor of the portion of the vertex stream.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Available in Windows Vista and later versions of the Windows operating systems.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\d3dumddi\nc-d3dumddi-pfnd3dddi_setstreamsourcefreq.md">SetStreamSourceFreq</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDIARG_SETSTREAMSOURCEFREQ structure%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
