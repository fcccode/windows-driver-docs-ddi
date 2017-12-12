---
UID: NF.sercx.SerCx2CustomTransmitTransactionCreate
title: SerCx2CustomTransmitTransactionCreate function
author: windows-driver-content
description: The SerCx2CustomTransmitTransactionCreate method creates a custom-transmit-transaction object, which version 2 of the serial framework extension (SerCx2) uses to perform custom-transmit transactions.
old-location: serports\sercx2customtransmittransactioncreate.htm
old-project: serports
ms.assetid: 1A308BD8-E28E-4618-99D0-55FBD6FA7CF4
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.keywords: SerCx2CustomTransmitTransactionCreate
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: sercx.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 8.1.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SerCx2CustomTransmitTransactionCreate
req.alt-loc: 2.0\Sercx.h
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
req.product: Windows 10 or later.
---

# SerCx2CustomTransmitTransactionCreate function



## -description
The <b>SerCx2CustomTransmitTransactionCreate</b> method creates a custom-transmit-transaction object, which version 2 of the serial framework extension (SerCx2) uses to perform custom-transmit transactions.



## -syntax

````
NTSTATUS SerCx2CustomTransmitTransactionCreate(
  [in]  SERCX2CUSTOMTRANSMIT                       CustomTransmit,
  [in]  PSERCX2_CUSTOM_TRANSMIT_TRANSACTION_CONFIG CustomTransmitTransactionConfig,
  [in]  PWDF_OBJECT_ATTRIBUTES                     Attributes,
  [out] SERCX2CUSTOMTRANSMITTRANSACTION            *CustomTransmitTransaction
);
````


## -parameters

### -param CustomTransmit [in]

A <a href="serports.sercx2customtransmit">SERCX2CUSTOMTRANSMIT</a> handle to a custom-transmit object. The serial controller driver previously called the <a href="serports.sercx2customtransmitcreate">SerCx2CustomTransmitCreate</a> method to create this object.


### -param CustomTransmitTransactionConfig [in]

A pointer to a <a href="serports.sercx2_custom_transmit_transaction_config">SERCX2_CUSTOM_TRANSMIT_TRANSACTION_CONFIG</a> structure. Before calling this method, the caller must call the <a href="serports.sercx2_custom_transmit_transaction_config_init">SERCX2_CUSTOM_TRANSMIT_TRANSACTION_CONFIG_INIT</a> function to initialize the structure. This structure contains pointers to a set of event callback routines that are implemented by the serial controller driver. SerCx2 calls these functions to do an I/O transaction that uses the custom data-transfer mechanism to write data to the serial controller to be transmitted.


### -param Attributes [in]

A pointer to a <a href="kmdf.wdf_object_attributes">WDF_OBJECT_ATTRIBUTES</a> structure that describes the attributes to assign to the new custom-transmit-transaction object. Before calling this method, the caller must call the <a href="kmdf.wdf_object_attributes_init">WDF_OBJECT_ATTRIBUTES_INIT</a> function to initialize the structure. This parameter is optional and can be specified as WDF_NO_OBJECT_ATTRIBUTES if the serial controller driver does not need to assign attributes to the object. For more information, see Remarks.


### -param CustomTransmitTransaction [out]

A pointer to a location to which this method writes a <a href="https://msdn.microsoft.com/library/windows/hardware/dn265257">SERCX2CUSTOMTRANSMITTRANSACTION</a> handle to the newly created custom-transmit-transaction object. SerCx2 and the serial controller driver use this handle in subsequent calls to refer to this object.


## -returns
This method returns STATUS_SUCCESS if the call is successful. Possible error return values include the following status codes.
<dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl>A custom-transmit-transaction object already exists from a previous <b>SerCx2CustomTransmitTransactionCreate</b> call.
<dl>
<dt><b>STATUS_INFO_LENGTH_MISMATCH</b></dt>
</dl>The <i>CustomTransmitTransactionConfig</i>-&gt;<b>Size</b> value does not equal <b>sizeof</b>(<b>SERCX2_CUSTOM_TRANSMIT_TRANSACTION_CONFIG</b>).
<dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl>A parameter value is not valid. The caller must supply a valid <a href="..\sercx\nc-sercx-evt_sercx2_custom_transmit_transaction_start.md">EvtSerCx2CustomTransmitTransactionStart</a> function pointer.
<dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl>Insufficient resources are available to create the custom-transmit-transaction object.

 


## -remarks
Your serial controller driver can call this method to create a custom-transmit-transaction object. SerCx2 uses this object to manage custom-transmit transactions, which are I/O transactions that use a custom data-transfer mechanism to write data to the serial controller to be transmitted.

As an option, a serial controller driver can use the <i>Attributes</i> parameter to create a context for the custom-transmit object, and to supply pointers to <a href="..\wdfobject\nc-wdfobject-evt_wdf_object_context_cleanup.md">EvtCleanupCallback</a> and <a href="..\wdfobject\nc-wdfobject-evt_wdf_object_context_destroy.md">EvtDestroyCallback</a> functions that are called to prepare the object for deletion. For more information, see <a href="kmdf.wdf_object_attributes">WDF_OBJECT_ATTRIBUTES</a>.

If the <i>Attributes</i> parameter points to a <a href="kmdf.wdf_object_attributes">WDF_OBJECT_ATTRIBUTES</a> structure, the caller must not overwrite the values that the <a href="kmdf.wdf_object_attributes_init">WDF_OBJECT_ATTRIBUTES_INIT</a> initialization function writes to the <b>ParentObject</b>, <b>ExecutionLevel</b>, and <b>SynchronizationScope</b> members of this structure.

If the specified combination of implemented callback functions is not valid, <b>SerCx2CustomTransmitTransactionCreate</b> fails and returns STATUS_INVALID_PARAMETER.

For more information about creating custom-transmit-transaction objects, see <a href="https://msdn.microsoft.com/library/windows/hardware/dn265257">SERCX2CUSTOMTRANSMITTRANSACTION</a>. For more information about custom-transmit transactions, see <a href="https://msdn.microsoft.com/E72E68BC-A60A-41BE-8606-92A608648042">SerCx2 Custom-Transmit Transactions</a>.


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
Available starting with Windows 8.1.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>2.0\Sercx.h</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="..\wdfobject\nc-wdfobject-evt_wdf_object_context_cleanup.md">EvtCleanupCallback</a>
</dt>
<dt>
<a href="..\wdfobject\nc-wdfobject-evt_wdf_object_context_destroy.md">EvtDestroyCallback</a>
</dt>
<dt>
<a href="..\sercx\nc-sercx-evt_sercx2_custom_transmit_transaction_start.md">EvtSerCx2CustomTransmitTransactionStart</a>
</dt>
<dt>
<a href="serports.sercx2customtransmit">SERCX2CUSTOMTRANSMIT</a>
</dt>
<dt>
<a href="serports.sercx2customtransmitcreate">SerCx2CustomTransmitCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn265257">SERCX2CUSTOMTRANSMITTRANSACTION</a>
</dt>
<dt>
<a href="serports.sercx2_custom_transmit_transaction_config">SERCX2_CUSTOM_TRANSMIT_TRANSACTION_CONFIG</a>
</dt>
<dt>
<a href="serports.sercx2_custom_transmit_transaction_config_init">SERCX2_CUSTOM_TRANSMIT_TRANSACTION_CONFIG_INIT</a>
</dt>
<dt>
<a href="kmdf.wdf_object_attributes">WDF_OBJECT_ATTRIBUTES</a>
</dt>
<dt>
<a href="kmdf.wdf_object_attributes_init">WDF_OBJECT_ATTRIBUTES_INIT</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [serports\serports]:%20SerCx2CustomTransmitTransactionCreate method%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
