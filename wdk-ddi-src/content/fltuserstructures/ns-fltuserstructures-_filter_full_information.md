---
UID: NS.FLTUSERSTRUCTURES._FILTER_FULL_INFORMATION
title: _FILTER_FULL_INFORMATION
author: windows-driver-content
description: The FILTER_FULL_INFORMATION structure contains full information for a minifilter driver.
old-location: ifsk\filter_full_information.htm
old-project: ifsk
ms.assetid: fb592350-76e2-4655-b6db-854fd48aa827
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: _FILTER_FULL_INFORMATION, *PFILTER_FULL_INFORMATION, FILTER_FULL_INFORMATION
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: fltuserstructures.h
req.include-header: FltUser.h, FltKernel.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FILTER_FULL_INFORMATION
req.alt-loc: fltuserstructures.h
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
---

# _FILTER_FULL_INFORMATION structure



## -description
The FILTER_FULL_INFORMATION structure contains full information for a minifilter driver. 



## -syntax

````
typedef struct _FILTER_FULL_INFORMATION {
  ULONG  NextEntryOffset;
  ULONG  FrameID;
  ULONG  NumberOfInstances;
  USHORT FilterNameLength;
  WCHAR  FilterNameBuffer[1];
} FILTER_FULL_INFORMATION, *PFILTER_FULL_INFORMATION;
````


## -struct-fields

### -field NextEntryOffset

Byte offset of the next FILTER_FULL_INFORMATION entry, if multiple entries are present in a buffer. This member is zero if no other entries follow this one. 


### -field FrameID

Zero-based index of the current frame. 


### -field NumberOfInstances

Number of instances that currently exist for this minifilter. 


### -field FilterNameLength

Length, in bytes, of the minifilter name. 


### -field FilterNameBuffer

Specifies the first character of the filter name string. This character is followed in memory by the remainder of the string. The length of the string is specified by the <b>FilterNameLength</b> member. The string is Unicode and is not NULL-terminated. 


## -remarks
The FILTER_FULL_INFORMATION structure is passed as a parameter to routines such as <a href="ifsk.filterfindfirst">FilterFindFirst</a>, <a href="ifsk.filterfindnext">FilterFindNext</a>, <a href="ifsk.filtergetinformation">FilterGetInformation</a>, <a href="ifsk.fltenumeratefilterinformation">FltEnumerateFilterInformation</a>, and <a href="ifsk.fltgetfilterinformation">FltGetFilterInformation</a>. 

This structure must be aligned on a LONGLONG (8-byte) boundary. If a buffer contains two or more of these structures, the <b>NextEntryOffset</b> value in each entry, except the last, falls on an 8-byte boundary.


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Fltuserstructures.h (include FltUser.h or FltKernel.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.filter_aggregate_basic_information">FILTER_AGGREGATE_BASIC_INFORMATION</a>
</dt>
<dt>
<a href="ifsk.filter_aggregate_standard_information">FILTER_AGGREGATE_STANDARD_INFORMATION</a>
</dt>
<dt>
<a href="ifsk.filterfindclose">FilterFindClose</a>
</dt>
<dt>
<a href="ifsk.filterfindfirst">FilterFindFirst</a>
</dt>
<dt>
<a href="ifsk.filterfindnext">FilterFindNext</a>
</dt>
<dt>
<a href="ifsk.filtergetinformation">FilterGetInformation</a>
</dt>
<dt>
<a href="ifsk.fltenumeratefilterinformation">FltEnumerateFilterInformation</a>
</dt>
<dt>
<a href="ifsk.fltgetfilterinformation">FltGetFilterInformation</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FILTER_FULL_INFORMATION structure%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
