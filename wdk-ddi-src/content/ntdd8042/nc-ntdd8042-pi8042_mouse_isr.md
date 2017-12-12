---
UID: NC.ntdd8042.PI8042_MOUSE_ISR
title: PI8042_MOUSE_ISR
author: windows-driver-content
description: A PI8042_MOUSE_ISR-typed callback routine customizes the operation of the I8042prt mouse ISR.
old-location: hid\pi8042_mouse_isr.htm
old-project: hid
ms.assetid: 7c8a0dc8-49ec-476f-b183-1baa419e831d
ms.author: windowsdriverdev
ms.date: 12/6/2017
ms.keywords: _MSFC_VirtualFibrePortAttributes, MSFC_VirtualFibrePortAttributes, *PMSFC_VirtualFibrePortAttributes
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: ntdd8042.h
req.include-header: Ntdd8042.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MouseIsr
req.alt-loc: ntdd8042.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section.
---

# PI8042_MOUSE_ISR callback



## -description
A PI8042_MOUSE_ISR-typed callback routine customizes the operation of the I8042prt mouse ISR.



## -prototype

````
PI8042_MOUSE_ISR MouseIsr;

BOOLEAN MouseIsr(
  _In_    PVOID                 IsrContext,
  _In_    PMOUSE_INPUT_DATA     CurrentInput,
  _In_    POUTPUT_PACKET        CurrentOutput,
  _In_    UCHAR                 StatusByte,
  _In_    PUCHAR                Byte,
  _Inout_ PBOOLEAN              ContinueProcessing,
  _In_    PMOUSE_STATE          MouseState,
  _In_    PMOUSE_RESET_SUBSTATE ResetSubState
)
{ ... }
````


## -parameters

### -param IsrContext [in]

Pointer to the filter device object of the driver that supplies this callback.


### -param CurrentInput [in]

Pointer to the input <a href="hid.mouse_input_data">MOUSE_INPUT_DATA</a> structure being constructed by the ISR.


### -param CurrentOutput [in]

Pointer to an <a href="hid.output_packet">OUTPUT_PACKET</a> structure, which specifies an array of bytes being written to the hardware device.


### -param StatusByte [in]

Specifies a status byte that is read from I/O port 60 when the interrupt occurs.


### -param Byte [in]

Specifies a data byte that is read from I/O port 64 when the interrupt occurs.


### -param ContinueProcessing [in, out]

Specifies, if <b>TRUE</b>, that processing in the I8042prt mouse ISR will continue after this callback completes. Otherwise, processing does not continue.


### -param MouseState [in]

Pointer to a <a href="hid.mouse_state">MOUSE_STATE</a> enumeration value, which identifies the state of mouse input.


### -param ResetSubState [in]

Pointer to MOUSE_RESET_SUBSTATE enumeration value, which identifies the mouse reset substate. See the Remarks section.


## -returns
A PI8042_MOUSE_ISR callback returns <b>TRUE</b> if the I8042prt mouse ISR should continue; otherwise it returns <b>FALSE</b>.


## -remarks
A PI8042_MOUSE_ISR callback is not needed if the default operation of the I8042prt mouse ISR is sufficient.

An upper-level keyboard filter driver can provide a mouse ISR callback. After the I8042prt mouse ISR validates the interrupt, it calls the mouse ISR callback.

To reset a mouse, I8042prt goes through a sequence of operational substates, each one of which is identified by a MOUSE_RESET_SUBSTATE enumeration value. For more information about how I8042prt resets a mouse and the corresponding mouse reset substates, see the documentation of MOUSE_RESET_SUBSTATE in ntdd8042.h.

A PI8042_MOUSE_ISR callback runs in kernel mode at the IRQL of the I8042prt mouse ISR.


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
Header

</th>
<td width="70%">
<dl>
<dt>Ntdd8042.h (include Ntdd8042.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
See Remarks section.

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/34d0a7e9-4a1e-43ba-a643-800ebaadc360">MouFilter_IsrHook</a>
</dt>
<dt>
<a href="hid.mouse_input_data">MOUSE_INPUT_DATA</a>
</dt>
<dt>
<a href="hid.mouse_state">MOUSE_STATE</a>
</dt>
<dt>
<a href="hid.output_packet">OUTPUT_PACKET</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20PI8042_MOUSE_ISR callback function%20 RELEASE:%20(12/6/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
