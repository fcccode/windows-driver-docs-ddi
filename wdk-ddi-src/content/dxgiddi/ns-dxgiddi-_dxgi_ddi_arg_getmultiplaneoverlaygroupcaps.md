---
UID: NS.DXGIDDI._DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS
title: _DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS
author: windows-driver-content
description: Used in a call to the pfnGetMultiplaneOverlayGroupCaps function to get a group of overlay plane capabilities.
old-location: display\dxgi_ddi_arg_getmultiplaneoverlaygroupcaps.htm
old-project: display
ms.assetid: C63125FA-7ADF-406A-A729-67C6ACA47D96
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS, DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: dxgiddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: Windows Server 2012 R2
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS
req.alt-loc: Dxgiddi.h
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

# _DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS structure



## -description
Used in a call to the <a href="display.pfngetmultiplaneoverlaygroupcaps">pfnGetMultiplaneOverlayGroupCaps</a> function to get a group of overlay plane capabilities.



## -syntax

````
typedef struct _DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS {
  DXGI_DDI_HDEVICE                       hDevice;
  D3DDDI_VIDEO_PRESENT_SOURCE_ID         VidPnSourceId;
  UINT                                   GroupIndex;
  DXGI_DDI_MULTIPLANE_OVERLAY_GROUP_CAPS MultiplaneOverlayGroupCaps;
} DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS;
````


## -struct-fields

### -field hDevice

[in] A handle to the display device (graphics context) for which overlay plane capabilities are needed.

The Direct3D runtime passed this handle to the driver in the <b>hDrvDevice</b> member of the <a href="..\d3d10umddi\ns-d3d10umddi-d3d10ddiarg_createdevice.md">D3D10DDIARG_CREATEDEVICE</a> structure when it created the device by calling the <a href="..\d3d10umddi\nc-d3d10umddi-pfnd3d10ddi_createdevice.md">CreateDevice(D3D10)</a> routine.


### -field VidPnSourceId

[in] The zero-based video present network (VidPN) source identification number of the input for which the capabilities are queried.


### -field GroupIndex

[in] The index of the overlay capability group for which capabilities are queried. This value is always between zero and (<a href="..\dxgiddi\ns-dxgiddi-dxgi_ddi_multiplane_overlay_caps.md">DXGI_DDI_MULTIPLANE_OVERLAY_CAPS</a>.<b>NumCapabilityGroups</b> – 1).


### -field MultiplaneOverlayGroupCaps

[out] The overlay plane capabilities for the requested capability group, given as a <a href="..\dxgiddi\ns-dxgiddi-dxgi_ddi_multiplane_overlay_group_caps.md">DXGI_DDI_MULTIPLANE_OVERLAY_GROUP_CAPS</a> structure.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 8.1

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2012 R2

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Dxgiddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\d3d10umddi\nc-d3d10umddi-pfnd3d10ddi_createdevice.md">CreateDevice(D3D10)</a>
</dt>
<dt>
<a href="..\d3d10umddi\ns-d3d10umddi-d3d10ddiarg_createdevice.md">D3D10DDIARG_CREATEDEVICE</a>
</dt>
<dt>
<a href="..\dxgiddi\ns-dxgiddi-dxgi_ddi_multiplane_overlay_caps.md">DXGI_DDI_MULTIPLANE_OVERLAY_CAPS</a>
</dt>
<dt>
<a href="..\dxgiddi\ns-dxgiddi-dxgi_ddi_multiplane_overlay_group_caps.md">DXGI_DDI_MULTIPLANE_OVERLAY_GROUP_CAPS</a>
</dt>
<dt>
<a href="display.pfngetmultiplaneoverlaygroupcaps">pfnGetMultiplaneOverlayGroupCaps</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGI_DDI_ARG_GETMULTIPLANEOVERLAYGROUPCAPS structure%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
