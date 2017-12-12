---
UID: NS.61883._CIP_DATA_FORMAT_VER2
title: _CIP_DATA_FORMAT_VER2
author: windows-driver-content
description: This structure is a CIP data format which is used by CMP_CONNECT_VER2.
old-location: ieee\cip_data_format_ver2.htm
old-project: IEEE
ms.assetid: C78543F5-82CC-43CF-8769-1E721C17FF9C
ms.author: windowsdriverdev
ms.date: 11/29/2017
ms.keywords: _CIP_DATA_FORMAT_VER2, *PCIP_DATA_FORMAT_VER2, CIP_DATA_FORMAT_VER2
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: 61883.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CIP_DATA_FORMAT_VER2
req.alt-loc: 61883.h
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

# _CIP_DATA_FORMAT_VER2 structure



## -description
This structure is a CIP data format which is used by <a href="ieee.cmp_connect_ver2">CMP_CONNECT_VER2</a>.



## -syntax

````
typedef struct _CIP_DATA_FORMAT_VER2 {
  HANDLE     hConnect;
  PCIP_FRAME Frame;
} CIP_DATA_FORMAT_VER2, *PCIP_DATA_FORMAT_VER2;
````


## -struct-fields

### -field hConnect

A handle to a connection.


### -field Frame

Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff537045">CIP_FRAME</a> structure that contains information about a frame and a data buffer to be sent or filled.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>61883.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537008">AV_61883_REQUEST</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [IEEE\buses]:%20CIP_DATA_FORMAT_VER2 structure%20 RELEASE:%20(11/29/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
