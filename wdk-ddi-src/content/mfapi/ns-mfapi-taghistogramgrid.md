---
UID: NS.MFAPI.TAGHISTOGRAMGRID
title: tagHistogramGrid
author: windows-driver-content
description: The HistogramGrid structure describes the blob format for MF_CAPTURE_METADATA_HISTOGRAM.
old-location: stream\histogramgrid.htm
old-project: stream
ms.assetid: 2B0BA5EC-3120-41A2-B06A-B63E57DC8766
ms.author: windowsdriverdev
ms.date: 12/6/2017
ms.keywords: tagHistogramGrid, HistogramGrid
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: mfapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HistogramGrid
req.alt-loc: mfapi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
---

# tagHistogramGrid structure



## -description
The  <b>HistogramGrid</b> structure describes the blob format for <b>MF_CAPTURE_METADATA_HISTOGRAM</b>.



## -syntax

````
typedef struct tagHistogramGrid {
  ULONG Width;
  ULONG Height;
  RECT  Region;
} HistogramGrid;
````


## -struct-fields

### -field Width

Width of the sensor output that histogram is collected from.


### -field Height

Height of the sensor output that histogram is collected from.


### -field Region

Absolute coordinates of the region on the sensor output that the histogram is collected for.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Mfapi.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="stream.histogramblobheader">HistogramBlobHeader</a>
</dt>
<dt>
<a href="stream.histogramdataheader">HistogramDataHeader</a>
</dt>
<dt>
<a href="stream.histogramheader">HistogramHeader</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20HistogramGrid structure%20 RELEASE:%20(12/6/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
