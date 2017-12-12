---
UID: NF.wdm.PoFxSetDeviceIdleTimeout
title: PoFxSetDeviceIdleTimeout function
author: windows-driver-content
description: The PoFxSetDeviceIdleTimeout routine specifies the minimum time interval from when the last component of the device enters the idle condition to when the power management framework (PoFx) calls the driver's DevicePowerNotRequiredCallback routine.
old-location: kernel\pofxsetdeviceidletimeout.htm
old-project: kernel
ms.assetid: 8378D5F1-92AC-4C59-BA66-68246C011199
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: PoFxSetDeviceIdleTimeout
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdm.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PoFxSetDeviceIdleTimeout
req.alt-loc: Ntoskrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ntoskrnl.lib
req.dll: Ntoskrnl.exe
req.irql: <= DISPATCH_LEVEL
req.product: Windows 10 or later.
---

# PoFxSetDeviceIdleTimeout function



## -description
The <b>PoFxSetDeviceIdleTimeout</b> routine specifies the minimum time interval from when the last component of the device enters the idle condition to when the power management framework (PoFx) calls the driver's <a href="kernel.devicepowernotrequiredcallback">DevicePowerNotRequiredCallback</a> routine.



## -syntax

````
VOID PoFxSetDeviceIdleTimeout(
  _In_ POHANDLE  Handle,
  _In_ ULONGLONG IdleTimeout
);
````


## -parameters

### -param Handle [in]

A handle that represents the registration of the device with PoFx. The device driver previously received this handle from the <a href="kernel.pofxregisterdevice">PoFxRegisterDevice</a> routine.


### -param IdleTimeout [in]

The idle time-out interval in 100-nanosecond units. For more information, see Remarks.


## -returns
None.


## -remarks
This routine specifies a time-out interval for PoFx to apply to future calls to the driver's <a href="kernel.devicepowernotrequiredcallback">DevicePowerNotRequiredCallback</a> callback routine. By default, this time-out interval is zero, in which case PoFx might call the <i>DevicePowerNotRequiredCallback</i> routine just as soon as the device is ready to switch to a low-power Dx state. However, a driver might prefer to delay this transition and to keep the device in the D0 power state for some additional time-out interval. In this case, if the device becomes active before the end of the time-out interval, and is therefore required to stay in the D0 state, the pending <i>DevicePowerNotRequiredCallback</i> call is no longer required and is canceled by PoFx.

For example, to improve performance and reduce wear, a storage device driver might want to prevent a spinning drive from entering D3 and slowing down until the drive has been idle for a sufficiently long time. To simplify this driver's implementation of the <i>DevicePowerNotRequiredCallback</i> callback routine, the <b>PoFxSetDeviceIdleTimeout</b> routine enables the driver to automatically delay the D3 transition without requiring the driver to set up a timer.

The time-out interval starts when all components of the device complete their transitions to the idle condition. Typically, PoFx waits until the end of the time-out interval to call the <i>DevicePowerNotRequiredCallback</i> routine. However, if PoFx is preparing to enter a low-power system state, PoFx might end the time-out interval early. In any case, when PoFx calls the driver's <i>DevicePowerNotRequiredCallback</i> routine, the driver should switch to the low-power Dx state without further delay.

The device driver can call <b>PoFxSetDeviceIdleTimeout</b> each time a change in conditions requires a change in the idle time-out interval. After each call, the new idle time-out interval remains in effect until the driver calls <b>PoFxSetDeviceIdleTimeout</b> again to update it.


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
Available starting with Windows 8.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wdm.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Ntoskrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>Ntoskrnl.exe</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="kernel.devicepowernotrequiredcallback">DevicePowerNotRequiredCallback</a>
</dt>
<dt>
<a href="kernel.pofxregisterdevice">PoFxRegisterDevice</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20PoFxSetDeviceIdleTimeout routine%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
