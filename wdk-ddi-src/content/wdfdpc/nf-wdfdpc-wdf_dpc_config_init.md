---
UID: NF.wdfdpc.WDF_DPC_CONFIG_INIT
title: WDF_DPC_CONFIG_INIT function
author: windows-driver-content
description: The WDF_DPC_CONFIG_INIT function initializes a driver's WDF_DPC_CONFIG structure.
old-location: wdf\wdf_dpc_config_init.htm
old-project: wdf
ms.assetid: 12b34b79-0154-4b25-83e7-b15642154b05
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: WDF_DPC_CONFIG_INIT
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdfdpc.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WDF_DPC_CONFIG_INIT
req.alt-loc: wdfdpc.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Any level
req.product: Windows 10 or later.
---

# WDF_DPC_CONFIG_INIT function



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WDF_DPC_CONFIG_INIT</b> function initializes a driver's <a href="wdf.wdf_dpc_config">WDF_DPC_CONFIG</a> structure.



## -syntax

````
VOID WDF_DPC_CONFIG_INIT(
  _Out_ PWDF_DPC_CONFIG Config,
  _In_  PFN_WDF_DPC     EvtDpcFunc
);
````


## -parameters

### -param Config [out]

A pointer to a driver-allocated <a href="wdf.wdf_dpc_config">WDF_DPC_CONFIG</a> structure.


### -param EvtDpcFunc [in]

A pointer to a driver-supplied <a href="wdf.evtdpcfunc">EvtDpcFunc</a> callback function.


## -returns
None


## -remarks
The <b>WDF_DPC_CONFIG_INIT</b> function stores the specified <a href="wdf.evtdpcfunc">EvtDpcFunc</a> pointer and sets the <b>AutomaticSerialization</b> member of the WDF_DPC_CONFIG structure to <b>TRUE</b>.

For a code example that uses the <b>WDF_DPC_CONFIG_INIT</b> function, see <a href="wdf.wdfdpccreate">WdfDpcCreate</a>.


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Minimum KMDF version

</th>
<td width="70%">
1.0

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wdfdpc.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
Any level

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="wdf.wdf_dpc_config">WDF_DPC_CONFIG</a>
</dt>
<dt>
<a href="wdf.evtdpcfunc">EvtDpcFunc</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_DPC_CONFIG_INIT function%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
