---
UID: NC.d3dumddi.PFND3DDDI_CREATEVERTEXSHADERFUNC
title: PFND3DDDI_CREATEVERTEXSHADERFUNC
author: windows-driver-content
description: The CreateVertexShaderFunc function converts vertex shader code into a hardware-specific format and associates the code with a shader handle.
old-location: display\createvertexshaderfunc.htm
old-project: display
ms.assetid: e986d37a-6039-4bc4-b5e8-6c4d4d7adedd
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _DXGK_PTE, DXGK_PTE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CreateVertexShaderFunc
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

# PFND3DDDI_CREATEVERTEXSHADERFUNC callback



## -description
The <b>CreateVertexShaderFunc</b> function converts vertex shader code into a hardware-specific format and associates the code with a shader handle.



## -prototype

````
PFND3DDDI_CREATEVERTEXSHADERFUNC CreateVertexShaderFunc;

__checkReturn HRESULT APIENTRY CreateVertexShaderFunc(
  _In_          HANDLE                           hDevice,
  _Inout_       D3DDDIARG_CREATEVERTEXSHADERFUNC *pData,
  _In_    const UINT                             *pCode
)
{ ... }
````


## -parameters

### -param hDevice [in]

 A handle to the display device (graphics context).


### -param pData [in, out]

 A pointer to a <a href="display.d3dddiarg_createvertexshaderfunc">D3DDDIARG_CREATEVERTEXSHADERFUNC</a> structure that retrieves the shader handle that is associated with the vertex shader code that is specified by <b>pCode</b>.


### -param pCode [in]

 An array of CONST UINT tokens that make up the vertex shader code.


## -returns
<b>CreateVertexShaderFunc</b> returns S_OK or an appropriate error result if the vertex shader code object is not successfully created.


## -remarks
For more information about programming shader assemblers, see <a href="https://msdn.microsoft.com/c858766c-b414-4971-b4d9-23ec94aca8ea">Processing Shader Codes</a>.


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
<a href="display.d3dddiarg_createvertexshaderfunc">D3DDDIARG_CREATEVERTEXSHADERFUNC</a>
</dt>
<dt>
<a href="display.d3dddi_devicefuncs">D3DDDI_DEVICEFUNCS</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3DDDI_CREATEVERTEXSHADERFUNC callback function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
