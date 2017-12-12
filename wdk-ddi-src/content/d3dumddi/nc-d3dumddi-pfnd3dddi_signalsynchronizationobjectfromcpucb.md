---
UID: NC.d3dumddi.PFND3DDDI_SIGNALSYNCHRONIZATIONOBJECTFROMCPUCB
title: PFND3DDDI_SIGNALSYNCHRONIZATIONOBJECTFROMCPUCB
author: windows-driver-content
description: pfnSignalSynchronizationObjectFromCpuCb enables a driver to signal a monitored fence.
old-location: display\pfnsignalsynchronizationobjectfromcpucb.htm
old-project: display
ms.assetid: E6FD5215-09CE-4DC8-B5AB-F65E68E2A884
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _DXGK_PTE, DXGK_PTE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Desktop
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: pfnSignalSynchronizationObjectFromCpuCb
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

# PFND3DDDI_SIGNALSYNCHRONIZATIONOBJECTFROMCPUCB callback



## -description
<b>pfnSignalSynchronizationObjectFromCpuCb</b> enables a driver to signal a monitored fence.



## -prototype

````
PFND3DDDI_SIGNALSYNCHRONIZATIONOBJECTFROMCPUCB pfnSignalSynchronizationObjectFromCpuCb;

HRESULT APIENTRY CALLBACK* pfnSignalSynchronizationObjectFromCpuCb(
  _In_ HANDLE                                      hDevice,
  _In_ D3DDDICB_SIGNALSYNCHRONIZATIONOBJECTFROMCPU *pData
)
{ ... }
````


## -parameters

### -param hDevice [in]

A handle to the display device.


### -param pData [in]

A pointer to a <a href="..\d3dumddi\ns-d3dumddi-d3dddicb_signalsynchronizationobjectfromcpu.md">D3DDDICB_SIGNALSYNCHRONIZATIONOBJECTFROMCPU</a> structure that provides the details of the requested operation.


## -returns
If this callback function succeeds, it returns <b xmlns:loc="http://microsoft.com/wdcml/l10n">S_OK</b>. Otherwise, it returns an <b xmlns:loc="http://microsoft.com/wdcml/l10n">HRESULT</b> error code.


## -remarks
When a monitored fence object is signaled by the CPU, the graphics kernel will update the fence memory location with the signaled value, so it becomes immediately visible to any user mode reader as well as immediately un-wait any satisfied waiters.
However, the caller cannot assume that the signal operation will be completed upon the return from this function. Instead, the caller should use appropriate <i>Wait</i> functions to check for signal completion.



## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 10

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2016

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