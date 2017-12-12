---
UID: NF.ntifs._FSRTL_ADVANCED_FCB_HEADER.FsRtlNotifyCleanupAll~r1
title: FsRtlNotifyCleanupAll function
author: windows-driver-content
description: The FsRtlNotifyCleanupAll routine removes all members of the specified notification list.
old-location: ifsk\fsrtlnotifycleanupall.htm
old-project: ifsk
ms.assetid: 850728bd-6758-4c21-9bfd-10a0f3d006d6
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: FsRtlNotifyCleanupAll
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntifs.h
req.include-header: FltKernel.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Vista and later version of the Windows operating system.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FsRtlNotifyCleanupAll
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <=APC_LEVEL
---

# FsRtlNotifyCleanupAll function



## -description
The <b>FsRtlNotifyCleanupAll</b> routine removes all members of the specified notification list. 



## -syntax

````
VOID FsRtlNotifyCleanupAll(
  _In_ PNOTIFY_SYNC NotifySync,
  _In_ PLIST_ENTRY  NotifyList
);
````


## -parameters

### -param NotifySync [in]

A pointer to the opaque synchronization object for <i>NotifyList</i>. 


### -param NotifyList [in]

A pointer to the head of the notify list to be cleaned up. Each element in the list is an opaque notify structure. 


## -returns
None


## -remarks
For each entry in the <i>NotifyList</i> list, <b>FsRtlNotifyCleanupAll</b> completes all pending IRPs. Then the routine removes the entry from the list and deallocates the entry.

Because a notify list is typically associated with a volume, the <b>FsRtlNotifyCleanupAll</b> routine can be used to complete all the IRP requests for the volume.


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
Available in Windows Vista and later version of the Windows operating system.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include FltKernel.h or Ntifs.h)</dt>
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
&lt;=APC_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.fsrtlnotifycleanup">FsRtlNotifyCleanup</a>
</dt>
<dt>
<a href="ifsk.fsrtlnotifyfilterchangedirectory">FsRtlNotifyFilterChangeDirectory</a>
</dt>
<dt>
<a href="ifsk.fsrtlnotifyfilterreportchange">FsRtlNotifyFilterReportChange</a>
</dt>
<dt>
<a href="ifsk.fsrtlnotifyfullchangedirectory">FsRtlNotifyFullChangeDirectory</a>
</dt>
<dt>
<a href="ifsk.fsrtlnotifyfullreportchange">FsRtlNotifyFullReportChange</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FsRtlNotifyCleanupAll routine%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
