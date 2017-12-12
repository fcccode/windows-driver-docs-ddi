---
UID: NF.ndis.NdisAllocateNetBufferAndNetBufferList
title: NdisAllocateNetBufferAndNetBufferList function
author: windows-driver-content
description: Call the NdisAllocateNetBufferAndNetBufferList function to allocate and initialize a NET_BUFFER_LIST structure that is initialized with a preallocated NET_BUFFER structure.
old-location: netvista\ndisallocatenetbufferandnetbufferlist.htm
old-project: netvista
ms.assetid: b872eff3-2d0a-4f01-874d-e00e09195801
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: NdisAllocateNetBufferAndNetBufferList
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
req.alt-api: NdisAllocateNetBufferAndNetBufferList
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_NetBuffer_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
---

# NdisAllocateNetBufferAndNetBufferList function



## -description
Call the 
  <b>NdisAllocateNetBufferAndNetBufferList</b> function to allocate and initialize a 
  <a href="netvista.net_buffer_list">NET_BUFFER_LIST</a> structure that is initialized
  with a preallocated 
  <a href="netvista.net_buffer">NET_BUFFER</a> structure.



## -syntax

````
PNET_BUFFER_LIST NdisAllocateNetBufferAndNetBufferList(
  _In_     NDIS_HANDLE PoolHandle,
  _In_     USHORT      ContextSize,
  _In_     USHORT      ContextBackFill,
  _In_opt_ PMDL        MdlChain,
  _In_     ULONG       DataOffset,
  _In_     SIZE_T      DataLength
);
````


## -parameters

### -param PoolHandle [in]

A NET_BUFFER_LIST structure pool handle that was previously returned from the 
     <a href="netvista.ndisallocatenetbufferlistpool">
     NdisAllocateNetBufferListPool</a> function. The 
     <b>fAllocateNetBuffer</b> member of the 
     <a href="netvista.net_buffer_list_pool_parameters">NET_BUFFER_LIST_POOL_PARAMETERS</a> structure that the caller passed to 
     <b>NdisAllocateNetBufferListPool</b> must have been set to <b>TRUE</b> and the 
     <b>DataSize</b> member set to zero.


### -param ContextSize [in]

The amount of 
     <i>used data space</i> in the 
     <a href="netvista.net_buffer_list_context">NET_BUFFER_LIST_CONTEXT</a> structure
     to reserve for the caller. The 
     <i>ContextSize</i> must be a multiple of the value defined by MEMORY_ALLOCATION_ALIGNMENT.


### -param ContextBackFill [in]

The amount of 
     <i>unused data space</i> (backfill space) that the caller requires. NDIS adds this value to the 
     <i>ContextSize</i> and allocates additional space. The 
     <i>ContextBackFill</i> must be a multiple of the value defined by MEMORY_ALLOCATION_ALIGNMENT.


### -param MdlChain [in, optional]

A pointer to an MDL chain that NDIS uses to initialize the preallocated NET_BUFFER structure. 
     <i>MdlChain</i> can be <b>NULL</b>.


### -param DataOffset [in]

The initial offset, in bytes, from the start of the buffer to the start of the 
     <i>used data space</i> in the MDL chain. Data space ahead of this offset is 
     <i>unused data space</i>. Therefore, this value also represents the initial amount of available backfill
     space in the MDL chain. If 
     <i>MdlChain</i> is <b>NULL</b>, 
     <i>DataOffset</i> must be 0.


### -param DataLength [in]

The length, in bytes, of the 
     <i>used data space</i> in the MDL chain. If 
     <i>MdlChain</i> is <b>NULL</b>, 
     <i>DataLength</i> must be 0.


## -returns
<b>NdisAllocateNetBufferAndNetBufferList</b> returns a pointer to the allocated NET_BUFFER_LIST
     structure. The NET_BUFFER_LIST structure includes a NET_BUFFER structure. If the allocation was
     unsuccessful, this pointer is <b>NULL</b>.


## -remarks
The structures that the 
    <b>NdisAllocateNetBufferAndNetBufferList</b> function allocates must come from a pool that includes 
    <a href="netvista.net_buffer_list">NET_BUFFER_LIST</a> structures that are paired
    with preallocated 
    <a href="netvista.net_buffer">NET_BUFFER</a> structures. To create such a pool, you
    must call the 
    <a href="netvista.ndisallocatenetbufferlistpool">
    NdisAllocateNetBufferListPool</a> function with the 
    <b>fAllocateNetBuffer</b> member of the 
    <a href="netvista.net_buffer_list_pool_parameters">NET_BUFFER_LIST_POOL_PARAMETERS</a> structure set to <b>TRUE</b>, and the 
    <b>DataSize</b> member set to zero.

Call the 
    <a href="netvista.ndisfreenetbufferlist">NdisFreeNetBufferList</a> function to
    free a <a href="netvista.net_buffer_list">NET_BUFFER_LIST</a> structure.

The preallocated <a href="netvista.net_buffer">NET_BUFFER</a> can be reused by reinitializing it with another MDL chain when it owns
    <b>NET_BUFFER</b>, but the 
    <i>DataOffset</i>, 
    <i>DataLength</i>, 
    <i>CurrentMdl</i>, and 
    <i>CurrentMdlOffset</i> fields in the <b>NET_BUFFER</b> must be consistent with the new MDL chain.

For example, if the original MDL chain contains <i>X</i>
<i>DataLength</i> and <i>Y</i>
<i>DataOffset</i>, and 
    <i>CurrentMdl</i> starts with the second MDL (<i>M</i>) in the original MDL chain, 
    <i>CurrentMdlOffset</i> is <i>Z</i>. The 
    <i>MdlChain</i> field in <a href="netvista.net_buffer_data">NET_BUFFER_DATA</a> then needs to point to a new MDL chain that contains <i>X'</i>
<i>DataLength</i> and <i>Y'</i>
<i>DataOffset</i>. If 
    <i>CurrentMdl</i> starts with the third MDL (<i>M'</i>) in the new MDL chain, 
    <i>CurrentMdlOffset</i> is <i>Z'</i>, and the following macros need to be used to set fields in <a href="netvista.net_buffer">NET_BUFFER</a>:


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
&lt;= DISPATCH_LEVEL

</td>
</tr>
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.ndis_irql_netbuffer_function">Irql_NetBuffer_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="netvista.ndisallocatenetbufferlistpool">
   NdisAllocateNetBufferListPool</a>
</dt>
<dt>
<a href="netvista.ndisfreenetbufferlist">NdisFreeNetBufferList</a>
</dt>
<dt>
<a href="netvista.net_buffer">NET_BUFFER</a>
</dt>
<dt>
<a href="netvista.net_buffer_list">NET_BUFFER_LIST</a>
</dt>
<dt>
<a href="netvista.net_buffer_list_context">NET_BUFFER_LIST_CONTEXT</a>
</dt>
<dt>
<a href="netvista.net_buffer_list_pool_parameters">NET_BUFFER_LIST_POOL_PARAMETERS</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisAllocateNetBufferAndNetBufferList function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
