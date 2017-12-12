---
UID: NC.d3dumddi.PFND3DDDI_CREATEQUERY
title: PFND3DDDI_CREATEQUERY
author: windows-driver-content
description: The CreateQuery function creates driver-side resources for a query that the Microsoft Direct3D runtime subsequently issues for processing.
old-location: display\createquery.htm
old-project: display
ms.assetid: ac63b77b-2704-4d5b-bf1d-9d85e8a1e336
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
req.alt-api: CreateQuery
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

# PFND3DDDI_CREATEQUERY callback



## -description
The <b>CreateQuery</b> function creates driver-side resources for a query that the Microsoft Direct3D runtime subsequently issues for processing.



## -prototype

````
PFND3DDDI_CREATEQUERY CreateQuery;

__checkReturn HRESULT APIENTRY CreateQuery(
  _In_    HANDLE                hDevice,
  _Inout_ D3DDDIARG_CREATEQUERY *pData
)
{ ... }
````


## -parameters

### -param hDevice [in]

 A handle to the display device (graphics context).


### -param pData [in, out]

 A pointer to a <a href="display.d3dddiarg_createquery">D3DDDIARG_CREATEQUERY</a> structure that identifies the query.


## -returns
<b>CreateQuery</b> returns one of the following values:
<dl>
<dt><b>S_OK</b></dt>
</dl>The query is successfully created.
<dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl>
<a href="..\d3dumddi\nc-d3dumddi-pfnd3dddi_createquery.md">CreateQuery</a> could not allocate the required memory for it to complete.

 


## -remarks
The Direct3D runtime calls the user-mode display driver's <b>CreateQuery</b> function with a query type to create resources for a query. The user-mode display driver creates the following resources for query types:

BOOL for D3DDDIQUERYTYPE_EVENT. Before responding about an event, the driver must ensure that the graphics processing unit (GPU) is finished processing all of the operations that are related to the event. That is, the driver responds about an event after the issue end state occurs. The driver must always set the event's BOOL value to <b>TRUE</b> when responding. 

UINT for D3DDDIQUERYTYPE_OCCLUSION. The driver sets this UINT variable to the number of pixels for which the z-test passed for all of the primitives between the beginning and end states of the issue query. If the depth buffer is multisampled, the driver determines the number of pixels from the number of samples. However, if the display device is capable of z-test accuracy for each multisample, the conversion to number of pixels should generally be rounded up. An application can then check the occlusion result against 0, to effectively mean "fully occluded." Drivers that convert multisampled quantities to pixel quantities should detect render target multisampling changes and continue to compute the query results appropriately.

A <a href="display.d3dddidevinfo_vcache">D3DDDIDEVINFO_VCACHE</a> structure for D3DDDIQUERYTYPE_VCACHE. The driver responds after the issue end state occurs.

For more information about issue query states, see <a href="display.d3dddi_issuequeryflags">D3DDDI_ISSUEQUERYFLAGS</a>.


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
<a href="display.d3dddiarg_createquery">D3DDDIARG_CREATEQUERY</a>
</dt>
<dt>
<a href="display.d3dddidevinfo_vcache">D3DDDIDEVINFO_VCACHE</a>
</dt>
<dt>
<a href="display.d3dddi_issuequeryflags">D3DDDI_ISSUEQUERYFLAGS</a>
</dt>
<dt>
<a href="display.d3dddi_devicefuncs">D3DDDI_DEVICEFUNCS</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3DDDI_CREATEQUERY callback function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
