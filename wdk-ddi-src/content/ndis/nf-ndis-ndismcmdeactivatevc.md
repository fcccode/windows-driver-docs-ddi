---
UID: NF.ndis.NdisMCmDeactivateVc
title: NdisMCmDeactivateVc function
author: windows-driver-content
description: NdisMCmDeactivateVc notifies NDIS that there will be no further transfers on a particular active VC.
old-location: netvista\ndismcmdeactivatevc.htm
old-project: netvista
ms.assetid: e18f6326-621e-4bed-aa82-b326f3b1422d
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: NdisMCmDeactivateVc
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see    NdisMCmDeactivateVc (NDIS   5.1)) in Windows Vista. Supported for NDIS 5.1 drivers (see    NdisMCmDeactivateVc (NDIS   5.1)) in Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisMCmDeactivateVc
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_MCM_Function
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

# NdisMCmDeactivateVc function



## -description
<b>NdisMCmDeactivateVc</b> notifies NDIS that there will be no further transfers on a particular active
  VC.



## -syntax

````
NDIS_STATUS NdisMCmDeactivateVc(
  _In_ NDIS_HANDLE NdisVcHandle
);
````


## -parameters

### -param NdisVcHandle [in]

Specifies the handle identifying the VC. This handle was supplied by NDIS to the MCM driver either
     when it called 
     <a href="netvista.ndismcmcreatevc">NdisMCmCreateVc</a> for an incoming call or
     when its 
     <a href="..\ndis\nc-ndis-protocol_co_create_vc.md">ProtocolCoCreateVc</a> function set up
     the VC for a client-initiated outgoing call.


## -returns
<b>NdisMCmDeactivateVc</b> can return one of the following:
<dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl>NDIS marked the VC as inactive.
<dl>
<dt><b>NDIS_STATUS_NOT_ACCEPTED</b></dt>
</dl>The VC is already deactivated, so this call is redundant.

 


## -remarks
An MCM driver calls 
    <b>NdisMCmDeactivateVc</b> as an essential step in closing a call, usually after the packet exchange with
    network components that tears down the connection.

A successful call to 
    <b>NdisMCmDeactivateVc</b> allows the MCM driver to discard the current call parameters for transfers on
    the VC, possibly reinitializing them to miniport driver-determined default values. However, if the VC is
    reactivated subsequently for another call, the client will supply new call parameters to the miniport
    driver.

The 
    <i>NdisVcHandle</i> passed to 
    <b>NdisMCmDeactivateVc</b> remains valid after VC deactivation is completed. The deactivation of any VC
    allows its creator to reinitialize the VC for reuse or to destroy it:

Following VC deactivation and the closing of the call, a client can reuse a VC that it originally
      created to make another call with 
      <a href="netvista.ndisclmakecall">NdisClMakeCall</a>, or it can call 
      <a href="netvista.ndiscodeletevc">NdisCoDeleteVc</a>, thereby causing a call
      to the MCM driver's 
      <a href="..\ndis\nc-ndis-protocol_co_delete_vc.md">ProtocolCoDeleteVc</a> function.

Following VC deactivation and the closing of the call, an MCM driver can reuse a VC that it
      originally created to indicate another incoming call to the same client with 
      <a href="netvista.ndismcmdispatchincomingcall">
      NdisMCmDispatchIncomingCall</a>, or it can call 
      <a href="netvista.ndismcmdeletevc">NdisMCmDeleteVc</a>.

The driver writer determines whether an MCM driver has an (internal) 
    <i>MiniportCoDeactivateVc</i> function that the driver calls in the context of tearing down connections
    for outgoing and incoming calls.

Only connection-oriented miniport drivers that provide integrated call-management support can call 
    <b>NdisMCmDeactivateVc</b>. Stand-alone call managers, which register themselves with NDIS as protocol
    drivers, call 
    <b>NdisCmDeactivateVc</b> instead.


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
Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/83192574-5734-40ec-b388-b686568bc800">NdisMCmDeactivateVc (NDIS
   5.1)</a>) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisMCmDeactivateVc (NDIS
   5.1)</b>) in Windows XP.

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
<a href="devtest.ndis_irql_mcm_function">Irql_MCM_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\ndis\nc-ndis-miniport_co_deactivate_vc.md">MiniportCoDeactivateVc</a>
</dt>
<dt>
<a href="netvista.ndisclclosecall">NdisClCloseCall</a>
</dt>
<dt>
<a href="netvista.ndisclmakecall">NdisClMakeCall</a>
</dt>
<dt>
<a href="netvista.ndiscmdeactivatevc">NdisCmDeactivateVc</a>
</dt>
<dt>
<a href="netvista.ndismcmactivatevc">NdisMCmActivateVc</a>
</dt>
<dt>
<a href="netvista.ndismcmdeletevc">NdisMCmDeleteVc</a>
</dt>
<dt>
<a href="netvista.ndismcmdispatchincomingcall">NdisMCmDispatchIncomingCall</a>
</dt>
<dt>
<a href="..\ndis\nc-ndis-protocol_cm_close_call.md">ProtocolCmCloseCall</a>
</dt>
<dt>
<a href="..\ndis\nc-ndis-protocol_co_delete_vc.md">ProtocolCoDeleteVc</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMCmDeactivateVc function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
