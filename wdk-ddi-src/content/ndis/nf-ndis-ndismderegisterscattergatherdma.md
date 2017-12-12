---
UID: NF.ndis.NdisMDeregisterScatterGatherDma
title: NdisMDeregisterScatterGatherDma function
author: windows-driver-content
description: Bus-master miniport drivers call NdisMDeregisterScatterGatherDma to release DMA resources that were allocated with the NdisMRegisterScatterGatherDma function.
old-location: netvista\ndismderegisterscattergatherdma.htm
old-project: netvista
ms.assetid: 44792a1f-c6d5-4491-a06d-e00e41e40059
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: NdisMDeregisterScatterGatherDma
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisMDeregisterScatterGatherDma
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Init_RegisterSG, Irql_Gather_DMA_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: PASSIVE_LEVEL
---

# NdisMDeregisterScatterGatherDma function



## -description
Bus-master miniport drivers call 
  <b>NdisMDeregisterScatterGatherDma</b> to release DMA resources that were allocated with the 
  <a href="netvista.ndismregisterscattergatherdma">
  NdisMRegisterScatterGatherDma</a> function.



## -syntax

````
VOID NdisMDeregisterScatterGatherDma(
  _In_ NDIS_HANDLE NdisMiniportDmaHandle
);
````


## -parameters

### -param NdisMiniportDmaHandle [in]

A handle to a context area that NDIS uses to manage a DMA resource. The caller obtained this
     handle by calling the 
     <b>NdisMRegisterScatterGatherDma</b> function.


## -returns
None


## -remarks
An NDIS miniport driver calls 
    <b>NdisMDeregisterScatterGatherDma</b> from its 
    <a href="..\ndis\nc-ndis-miniport_halt.md">MiniportHaltEx</a> function to release the
    DMA resources it allocated and initialized in a previous call to 
    <b>NdisMRegisterScatterGatherDma</b>.


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
Version

</th>
<td width="70%">
Supported in NDIS 6.0 and later.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
PASSIVE_LEVEL

</td>
</tr>
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.ndis_init_registersg">Init_RegisterSG</a>, <a href="devtest.ndis_irql_gather_dma_function">Irql_Gather_DMA_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\ndis\nc-ndis-miniport_halt.md">MiniportHaltEx</a>
</dt>
<dt>
<a href="netvista.ndismregisterscattergatherdma">
   NdisMRegisterScatterGatherDma</a>
</dt>
<dt>
<a href="netvista.allocating_and_freeing_scatter_gather_lists">Allocating and Freeing Scatter/Gather Lists</a>
</dt>
<dt>
<a href="netvista.scatter_gather_dma2">Miniport Driver Scatter/Gather DMA</a>
</dt>
<dt>
<a href="netvista.ndis_scatter_gather_dma">NDIS Scatter/Gather DMA</a>
</dt>
<dt>
<a href="netvista.registering_and_deregistering_dma_channels">Registering and Deregistering DMA Channels</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMDeregisterScatterGatherDma function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
