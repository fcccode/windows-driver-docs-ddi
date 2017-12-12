---
UID: NF.irb.AtaPortReadRegisterUchar
title: AtaPortReadRegisterUchar function
author: windows-driver-content
description: The AtaPortReadRegisterUchar routine reads an unsigned byte value from the HBA.Note  The ATA port driver and ATA miniport driver models may be altered or unavailable in the future.
old-location: storage\ataportreadregisteruchar.htm
old-project: storage
ms.assetid: 1baa8d01-b889-4f2b-ad9e-f35078f7b3d8
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: AtaPortReadRegisterUchar
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: irb.h
req.include-header: Ata.h, Irb.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: AtaPortReadRegisterUchar
req.alt-loc: ataport.lib,ataport.dll,pciidex.lib,pciidex.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ataport.lib; Pciidex.lib
req.dll: 
req.irql: 
---

# AtaPortReadRegisterUchar function



## -description
The <b>AtaPortReadRegisterUchar</b> routine reads an unsigned byte value from the HBA.



## -syntax

````
UCHAR AtaPortReadRegisterUchar(
  _In_ PUCHAR Register
);
````


## -parameters

### -param Register [in]

A pointer to the register to read. The address value that is assigned to this parameter must be within the range of mapped I/O space addresses that are obtained by a call to <a href="storage.ataportgetdevicebase">AtaPortGetDeviceBase</a>.


## -returns
<b>AtaPortReadRegisterUchar</b> returns a UCHAR value from the HBA's register. 


## -remarks


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
<dt>Irb.h (include Ata.h or Irb.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Ataport.lib; </dt>
<dt>Pciidex.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.ataportgetdevicebase">AtaPortGetDeviceBase</a>
</dt>
<dt>
<a href="storage.ataportreadregisterulong">AtaPortReadRegisterUlong</a>
</dt>
<dt>
<a href="storage.ataportreadregisterushort">AtaPortReadRegisterUshort</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20AtaPortReadRegisterUchar routine%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
