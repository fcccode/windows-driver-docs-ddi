---
UID: NF.wdm.IoCreateSynchronizationEvent
title: IoCreateSynchronizationEvent function
author: windows-driver-content
description: The IoCreateSynchronizationEvent routine creates or opens a named synchronization event for use in serialization of access to hardware between two otherwise unrelated drivers.
old-location: kernel\iocreatesynchronizationevent.htm
old-project: kernel
ms.assetid: ce068ad0-3826-4f5d-a41c-2c3a40200f30
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: IoCreateSynchronizationEvent
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdm.h
req.include-header: Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoCreateSynchronizationEvent
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IrqlIoPassive4, PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
req.product: Windows 10 or later.
---

# IoCreateSynchronizationEvent function



## -description
The <b>IoCreateSynchronizationEvent</b> routine creates or opens a named synchronization event for use in serialization of access to hardware between two otherwise unrelated drivers.



## -syntax

````
PKEVENT IoCreateSynchronizationEvent(
  _In_  PUNICODE_STRING EventName,
  _Out_ PHANDLE         EventHandle
);
````


## -parameters

### -param EventName [in]

Pointer to a buffer containing a null-terminated Unicode string that names the event.


### -param EventHandle [out]

Pointer to a location in which to return a handle for the event object. In Windows Server 2003 and later versions of Windows, the returned handle is a <a href="wdkgloss.k#wdkgloss.kernel_handle#wdkgloss.kernel_handle"><i>kernel handle</i></a>. 


## -returns
<b>IoCreateSynchronizationEvent</b> returns a pointer to the created or opened event object or <b>NULL</b> if the event object could not be created or opened. 


## -remarks
The event object is created if it does not already exist. <b>IoCreateSynchronizationEvent</b> sets the state of a new synchronization event to Signaled. If the event object already exists, it is simply opened. The pair of drivers that use a synchronization event call <a href="kernel.kewaitforsingleobject">KeWaitForSingleObject</a> with the PKEVENT pointer returned by this routine.

When a synchronization event is set to the Signaled state, a single thread of execution that was waiting for the event is released, and the event is automatically reset to the Not-Signaled state.

To release the event, a driver calls <a href="kernel.zwclose">ZwClose</a> with the event handle.

Sharing event objects between user mode and kernel mode requires care. There are two main methods for sharing event objects: 

The user-mode application creates the event object and passes a handle to the object to the driver by sending an IOCTL to the driver. The driver must handle the IOCTL in the context of the process that created the event object and must validate the handle by calling <a href="kernel.obreferenceobjectbyhandle">ObReferenceObjectByHandle</a>. This method is the recommended method for sharing event objects between user and kernel modes.

The driver creates a named event object in the \\BaseNamedObjects object directory. You can open a kernel-mode event named \\BaseNamedObjects\<i>Xxx</i> in user mode under the name <i>Xxx</i>. Note that security settings can prevent an application from opening the event. For more information, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=718194">OpenEvent Fails in a Non-Administrator Account</a> KB article. The \\BaseNamedObjects object directory is not created until the Microsoft Win32 subsystem initializes, so drivers that are loaded at boot time cannot create event objects in the \\BaseNamedObjects directory in their <a href="..\wdm\nc-wdm-driver_initialize.md">DriverEntry</a> routines

For more information about events, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544323">Event Objects</a>. 


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
Available starting with Windows 2000.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Ntddk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
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
<a href="devtest.wdm_irqliopassive4">IrqlIoPassive4</a>, <a href="devtest.wdm_powerirpddis">PowerIrpDDis</a>, <a href="devtest.storport_hwstorportprohibitedddis">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.iocreatenotificationevent">IoCreateNotificationEvent</a>
</dt>
<dt>
<a href="kernel.kewaitforsingleobject">KeWaitForSingleObject</a>
</dt>
<dt>
<a href="kernel.rtlinitunicodestring">RtlInitUnicodeString</a>
</dt>
<dt>
<a href="kernel.zwclose">ZwClose</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoCreateSynchronizationEvent routine%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
