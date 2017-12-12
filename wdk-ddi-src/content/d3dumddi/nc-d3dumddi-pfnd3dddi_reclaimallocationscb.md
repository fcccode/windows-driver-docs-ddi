---
UID: NC.d3dumddi.PFND3DDDI_RECLAIMALLOCATIONSCB
title: PFND3DDDI_RECLAIMALLOCATIONSCB
author: windows-driver-content
description: Called by the user-mode display driver to reclaim video memory allocations that were previously offered for reuse.
old-location: display\pfnreclaimallocationscb.htm
old-project: display
ms.assetid: BAC27F24-B348-48D5-9E9B-20897B4D8E2D
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _DXGK_PTE, DXGK_PTE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Desktop
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: pfnReclaimAllocationsCb
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

# PFND3DDDI_RECLAIMALLOCATIONSCB callback



## -description
Called by the user-mode display driver   to reclaim video memory allocations that were previously offered  for reuse.



## -prototype

````
PFND3DDDI_RECLAIMALLOCATIONSCB pfnReclaimAllocationsCb;

__checkReturn HRESULT APIENTRY pfnReclaimAllocationsCb(
  _In_       HANDLE                      hDevice,
  _In_ const D3DDDICB_RECLAIMALLOCATIONS *pData
)
{ ... }
````


## -parameters

### -param hDevice [in]

 A handle to the display device (graphics context).


### -param pData [in]

 A pointer to a <a href="display.d3dddicb_reclaimallocations">D3DDDICB_RECLAIMALLOCATIONS</a> structure that defines the allocations to reclaim.


## -returns

      Returns one of the following values.
<dl>
<dt><b>S_OK</b></dt>
</dl>The allocations were successfully reclaimed.
<dl>
<dt><b>E_INVALIDARG</b></dt>
</dl>An invalid parameter was supplied.
<dl>
<dt><b>D3DDDIERR_DEVICEREMOVED</b></dt>
</dl>The video memory manager or display miniport driver could not complete the operation because either a Plug and Play (PnP) Stop event or a Timeout Detection and Recovery (TDR) event occurred.

 


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 8

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2012

</td>
</tr>
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
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="display.d3dddicb_reclaimallocations">D3DDDICB_RECLAIMALLOCATIONS</a>
</dt>
<dt>
<a href="display.d3dddi_devicecallbacks">D3DDDI_DEVICECALLBACKS</a>
</dt>
<dt>
<a href="display.pfnreclaimresources">pfnReclaimResources</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20pfnReclaimAllocationsCb callback function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
