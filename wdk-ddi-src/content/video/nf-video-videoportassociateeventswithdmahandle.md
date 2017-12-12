---
UID: NF.video.VideoPortAssociateEventsWithDmaHandle
title: VideoPortAssociateEventsWithDmaHandle function
author: windows-driver-content
description: The VideoPortAssociateEventsWithDmaHandle function is obsolete in Windows 2000 and later.VideoPortAssociateEventsWithDmaHandle associates an event, which is shared by the video display driver and the video miniport driver, with a DMA handle.
old-location: display\videoportassociateeventswithdmahandle.htm
old-project: display
ms.assetid: d8a64a06-41b9-429b-a5ac-6de4996c702b
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: VideoPortAssociateEventsWithDmaHandle
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: video.h
req.include-header: Video.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows 2000 and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: VideoPortAssociateEventsWithDmaHandle
req.alt-loc: Videoprt.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Videoprt.lib
req.dll: Videoprt.sys
req.irql: 
req.product: Windows 10 or later.
---

# VideoPortAssociateEventsWithDmaHandle function



## -description
The <b>VideoPortAssociateEventsWithDmaHandle</b> function is <b>obsolete</b> in Windows 2000 and later.

<b>VideoPortAssociateEventsWithDmaHandle</b> associates an event, which is shared by the video display driver and the video miniport driver, with a DMA handle.



## -syntax

````
PDMA VideoPortAssociateEventsWithDmaHandle(
  _In_    PVOID                 HwDeviceExtension,
  _Inout_ PVIDEO_REQUEST_PACKET pVrp,
  _In_    PVOID                 MappedUserEvent,
  _In_    PVOID                 DisplayDriverEvent
);
````


## -parameters

### -param HwDeviceExtension [in]

Pointer to the miniport driver's device extension.


### -param pVrp [in, out]

Pointer to a <a href="display.video_request_packet">VIDEO_REQUEST_PACKET</a>. 


### -param MappedUserEvent [in]

Is reserved for system use.


### -param DisplayDriverEvent [in]

Is reserved for system use.


## -returns
<b>VideoPortAssociateEventsWithDmaHandle</b> always returns <b>NULL</b>.


## -remarks
See <a href="https://msdn.microsoft.com/fe6c2e16-d222-4948-b1df-34ed8d57d9d8">Bus-Master DMA in Video Miniport Drivers</a> for information about packet-based and common-buffer DMA transfers.


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
Version

</th>
<td width="70%">
Available in Windows 2000 and later versions of the Windows operating systems.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Video.h (include Video.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Videoprt.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>Videoprt.sys</dt>
</dl>
</td>
</tr>
</table>