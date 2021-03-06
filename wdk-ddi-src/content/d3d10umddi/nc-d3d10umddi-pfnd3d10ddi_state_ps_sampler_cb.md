---
UID: NC:d3d10umddi.PFND3D10DDI_STATE_PS_SAMPLER_CB
title: PFND3D10DDI_STATE_PS_SAMPLER_CB
author: windows-driver-content
description: The pfnStatePsSamplerCb function causes the Microsoft Direct3D 10 runtime to refresh the pixel shader stage's bound samplers.
old-location: display\pfnstatepssamplercb.htm
old-project: display
ms.assetid: 8cf25918-1acf-40b6-be51-2c1afc419f2a
ms.author: windowsdriverdev
ms.date: 3/29/2018
ms.keywords: PFND3D10DDI_STATE_PS_SAMPLER_CB, d3d10state_functions_2e14a132-dd8b-4a78-905e-b2d74d9e669d.xml, d3d10umddi/pfnStatePsSamplerCb, display.pfnstatepssamplercb, pfnStatePsSamplerCb, pfnStatePsSamplerCb callback function [Display Devices]
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
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
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	d3d10umddi.h
api_name:
-	pfnStatePsSamplerCb
product:
- Windows
targetos: Windows
req.typenames: SETRESULT_INFO, *PSETRESULT_INFO
---

# PFND3D10DDI_STATE_PS_SAMPLER_CB callback


## -description


The <b>pfnStatePsSamplerCb</b> function causes the Microsoft Direct3D 10 runtime to refresh the pixel shader stage's bound samplers.


## -parameters




### -param Arg1


### -param Arg2


### -param Arg3








#### - Base [in]

 The beginning sampler for which the runtime should refresh state. 


#### - Count [in]

 The total number of samplers. The number can be -1, which specifies that the Direct3D runtime will use its high watermarks to substitute an optimal value (which is typically less than the maximum valid value for <i>Count</i>). However, no non-NULL binding exists in a slot larger than the optimal <i>Count</i> value.


#### - hRuntimeDevice [in]

 A handle to a context for the core Direct3D 10 runtime. This handle is supplied to the driver in a call to the driver's <a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a> function. 


## -returns



None




## -see-also




<a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff541820">D3D10DDI_CORELAYER_DEVICECALLBACKS</a>
 

 

