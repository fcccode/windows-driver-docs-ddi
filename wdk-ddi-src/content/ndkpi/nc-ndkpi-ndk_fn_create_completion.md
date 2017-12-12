---
UID: NC.ndkpi.NDK_FN_CREATE_COMPLETION
title: NDK_FN_CREATE_COMPLETION
author: windows-driver-content
description: The NdkCreateCompletion (NDK_FN_CREATE_COMPLETION) function completes the creation of an NDK object.
old-location: netvista\ndk_fn_create_completion.htm
old-project: netvista
ms.assetid: C7A2792C-FDAE-4525-A8B1-7F8F6BA8249A
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _NDIS_WWAN_VISIBLE_PROVIDERS, *PNDIS_WWAN_VISIBLE_PROVIDERS, NDIS_WWAN_VISIBLE_PROVIDERS
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
req.alt-api: NdkCreateCompletion
req.alt-loc: ndkpi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <=DISPATCH_LEVEL
---

# NDK_FN_CREATE_COMPLETION callback



## -description
The <i>NdkCreateCompletion</i> (<i>NDK_FN_CREATE_COMPLETION</i>) function completes the creation of an NDK object.



## -prototype

````
NDK_FN_CREATE_COMPLETION NdkCreateCompletion;

VOID NdkCreateCompletion(
  _In_opt_ PVOID             Context,
  _In_     NTSTATUS          Status,
  _In_     NDK_OBJECT_HEADER *pNdkObject
)
{ ... }
````


## -parameters

### -param Context [in, optional]

The context value passed to the NDK provider when a consumer calls an object creation function. The creation function  provides the context with the asynchronous create completion request <i>NdkCreateCompletion</i> (<i>NDK_FN_CREATE_COMPLETION</i>) function pointer.


### -param Status [in]

The asynchronous completion status for the create request. See the object creation functions (for example, <a href="..\ndkpi\nc-ndkpi-ndk_fn_create_cq.md">NDK_FN_CREATE_CQ</a>) for completion status codes that can be returned for each type of object.


### -param pNdkObject [in]

A pointer to an NDK object header (<a href="netvista.ndk_object_header">NDK_OBJECT_HEADER</a>).


## -returns
None


## -remarks
NDK objects are created with asynchronous functions. These asynchronous object creation functions take an <i>NDK_FN_CREATE_COMPLETION</i> function pointer as an input parameter. 

An NDK provider can return STATUS_PENDING from an asynchronous object creation function. In this case, the  NDK provider must call the create completion function to indicate that the object creation is complete. 

Any status other status code indicates inline completion. In this case, the provider must not call the create request completion function. If the create request function returns an NT_STATUS status code other than STATUS_PENDING, the created object must be returned in an output parameter with the create request function. 

For create requests that return STATUS_PENDING and later complete with STATUS_SUCCESS asynchronously, the created object must be returned by the create completion function with the <i>pNdkObject</i> parameter and the provider must not access the object output parameter of the create request function.


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
None supported

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
Version

</th>
<td width="70%">
Supported in NDIS 6.30 and later.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ndkpi.h (include Ndkpi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
&lt;=DISPATCH_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="netvista.ndk_object_header">NDK_OBJECT_HEADER</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_connector.md">NDK_FN_CREATE_CONNECTOR</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_cq.md">NDK_FN_CREATE_CQ</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_listener.md">NDK_FN_CREATE_LISTENER</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_mr.md">NDK_FN_CREATE_MR</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_mw.md">NDK_FN_CREATE_MW</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_pd.md">NDK_FN_CREATE_PD</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_qp.md">NDK_FN_CREATE_QP</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_qp_with_srq.md">NDK_FN_CREATE_QP_WITH_SRQ</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_shared_endpoint.md">NDK_FN_CREATE_SHARED_ENDPOINT</a>
</dt>
<dt>
<a href="..\ndkpi\nc-ndkpi-ndk_fn_create_srq.md">NDK_FN_CREATE_SRQ</a>
</dt>
<dt>
<a href="netvista.ndkpi_object_lifetime_requirements">NDKPI Object Lifetime Requirements</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDK_FN_CREATE_COMPLETION callback function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
