---
UID: NC.dot11wdi.NDIS_WDI_TX_DEQUEUE_IND
title: NDIS_WDI_TX_DEQUEUE_IND
author: windows-driver-content
description: The NdisWdiTxDequeueIndication callback function is called in the context of a MiniportWdiTxDataSend or MiniportWdiTxTalSend by the IHV miniport to dequeue frames from WDI to the IHV miniport.
old-location: netvista\ndiswditxdequeueindication.htm
old-project: netvista
ms.assetid: ACCB45DA-1233-4276-A0F5-466E50D9377B
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _SYNTH_STATS, *PSYNTH_STATS, SYNTH_STATS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: dot11wdi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisWdiTxDequeueIndication
req.alt-loc: dot11wdi.h
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

# NDIS_WDI_TX_DEQUEUE_IND callback



## -description
The 
  NdisWdiTxDequeueIndication callback function is called in the context of a <a href="..\dot11wdi\nc-dot11wdi-miniport_wdi_tx_data_send.md">MiniportWdiTxDataSend</a> or <a href="..\dot11wdi\nc-dot11wdi-miniport_wdi_tx_tal_send.md">MiniportWdiTxTalSend</a> by the IHV miniport to dequeue frames from WDI to the IHV miniport.

This is a callback inside <a href="netvista.ndis_wdi_data_api">NDIS_WDI_DATA_API</a>.



## -prototype

````
NDIS_WDI_TX_DEQUEUE_IND NdisWdiTxDequeueIndication;

VOID NdisWdiTxDequeueIndication(
  _In_  NDIS_HANDLE      NdisMiniportDataPathHandle,
  _In_  UINT32           Quantum,
  _In_  UINT8            MaxNumFrames,
  _In_  UINT16           Credit,
  _Out_ PNET_BUFFER_LIST *ppNBL
)
{ ... }
````


## -parameters

### -param NdisMiniportDataPathHandle [in]

The NdisMiniportDataPathHandle passed to the IHV miniport in <a href="..\dot11wdi\nc-dot11wdi-miniport_wdi_tal_txrx_initialize.md">MiniportWdiTalTxRxInitialize</a>.


### -param Quantum [in]

The quantum. For more information, see the <i>Host - target TX transfer scheduling</i> section in <a href="netvista.wdi_tx_path">WDI TX path</a>.


### -param MaxNumFrames [in]

Maximum frame count.


### -param Credit [in]

Credit value. For more information, see <i>The target-credit scheme and the pause/resume mechanism</i> section in <a href="netvista.wdi_tx_path">WDI TX path</a>.


### -param ppNBL [out]

Pointer to a pointer to a <a href="netvista.net_buffer_list">NET_BUFFER_LIST</a> chain dequeued by WDI.


## -returns
This callback function does not return a value.


## -remarks
A subset of the parameters may not be applicable to a device. For instance, the maximum frame count may not apply to a store and forward device (message-based bus interface).

The following parameters are ignored by TxMgr under these circumstances.

The TAL should provide accurate parameters whenever possible to guarantee fairness and avoid overwhelming TIL/target resources.  

If the TAL does not have enough credit to dequeue a maximum cost frame, it should issue an <a href="..\dot11wdi\nc-dot11wdi-ndis_wdi_tx_send_pause_ind.md">NdisWdiTxSendPauseIndication</a> instead of an <i>NdisWdiTxDequeueIndication</i>.

The TxMgr may return a list of <a href="netvista.net_buffer_list">NET_BUFFER_LIST</a> that exceed the limit of the number of frames, frame cost, or quantum. This only happens if the frames are being requeued/replayed after being send completed with status of Postponed and with identical sequence number, which indicates they were originally transmitted as part of a single A-MSDU.


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
Header

</th>
<td width="70%">
<dl>
<dt>Dot11wdi.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="netvista.ndis_wdi_data_api">NDIS_WDI_DATA_API</a>
</dt>
<dt>
<a href="..\dot11wdi\nc-dot11wdi-ndis_wdi_tx_dequeue_ind.md">NdisWdiTxDequeueIndication</a>
</dt>
<dt>
<a href="..\dot11wdi\nc-dot11wdi-ndis_wdi_tx_send_pause_ind.md">NdisWdiTxSendPauseIndication</a>
</dt>
<dt>
<a href="netvista.net_buffer_list">NET_BUFFER_LIST</a>
</dt>
<dt>
<a href="netvista.wdi_tx_path">WDI TX path</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_WDI_TX_DEQUEUE_IND callback function%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
