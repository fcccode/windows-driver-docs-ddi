---
UID: NC:ndkpi.NDK_FN_QUERY_ADAPTER_INFO
title: NDK_FN_QUERY_ADAPTER_INFO
author: windows-driver-content
description: The NdkQueryAdapterInfo (NDK_FN_QUERY_ADAPTER_INFO) function retrieves information about limits and capabilities of an NDK adapter.
old-location: netvista\ndk_fn_query_adapter_info.htm
old-project: netvista
ms.assetid: A307584E-CBF6-4CEB-8A0F-D519DA7599D3
ms.author: windowsdriverdev
ms.date: 3/26/2018
ms.keywords: NDK_FN_QUERY_ADAPTER_INFO, NdkQueryAdapterInfo, NdkQueryAdapterInfo callback function [Network Drivers Starting with Windows Vista], ndkpi/NdkQueryAdapterInfo, netvista.ndk_fn_query_adapter_info
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: ndkpi.h
req.include-header: Ndkpi.h
req.target-type: Windows
req.target-min-winverclnt: None supported,Supported in NDIS 6.30 and later.
req.target-min-winversvr: Windows Server 2012
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
req.irql: PASSIVE_LEVEL
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	ndkpi.h
api_name:
-	NdkQueryAdapterInfo
product:
- Windows
targetos: Windows
req.typenames: NDIS_WWAN_VISIBLE_PROVIDERS, *PNDIS_WWAN_VISIBLE_PROVIDERS
---

# NDK_FN_QUERY_ADAPTER_INFO callback


## -description


The <i>NdkQueryAdapterInfo</i> (<i>NDK_FN_QUERY_ADAPTER_INFO</i>) function retrieves information about limits and capabilities of an  NDK adapter.


## -parameters




### -param *pNdkAdapter [in]

A pointer to an NDK adapter (<a href="https://msdn.microsoft.com/7EEFC371-5E6F-4507-BF7F-66A1954C7A1A">NDK_ADAPTER)</a> instance.


### -param *pInfo

A pointer to a buffer that contains an <a href="https://msdn.microsoft.com/library/windows/hardware/hh439851">NDK_ADAPTER_INFO</a> structure. If the request completes with STATUS_SUCCESS, the NDK provider  fills  the structure with adapter information. 


### -param *pBufferSize

On input, this parameter is a pointer to a variable that holds the size, in bytes, of the buffer that the  <i>pInfo</i> parameter  points to. On output, the variable receives the size, in bytes,  of the adapter information that was written into the buffer.



## -returns



The 
     <i>NdkQueryAdapterInfo</i> function returns one of the following NTSTATUS codes.

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl>
</td>
<td width="60%">
The 	request completed successfully.


</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_BUFFER_TOO_SMALL</b></dt>
</dl>
</td>
<td width="60%">

The value in the <i>*pBufferSize</i> parameter specified a buffer size that was too small to hold the adapter information. <i>*pBufferSize</i> is updated with the required size.


</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>Other status codes</b></dt>
</dl>
</td>
<td width="60%">
An error occurred. 

</td>
</tr>
</table>
 




## -remarks



<i>NdkQueryAdapterInfo</i> retrieves the adapter information in an  <a href="https://msdn.microsoft.com/library/windows/hardware/hh439851">NDK_ADAPTER_INFO</a> structure. The structure  contains information on various limits and capabilities of the adapter.

<i>NdkQueryAdapterInfo</i>  requires an IRQL equal to PASSIVE_LEVEL and  it blocks until the request is completed.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/hh439848">NDK_ADAPTER</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/hh439850">NDK_ADAPTER_DISPATCH</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/hh439851">NDK_ADAPTER_INFO</a>
 

 

