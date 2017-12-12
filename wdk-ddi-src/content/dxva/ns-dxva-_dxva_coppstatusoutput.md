---
UID: NS.DXVA._DXVA_COPPSTATUSOUTPUT
title: _DXVA_COPPStatusOutput
author: windows-driver-content
description: The DXVA_COPPStatusOutput structure describes the status returned from a query on a protected video session that is associated with a DirectX VA COPP device.
old-location: display\dxva_coppstatusoutput.htm
old-project: display
ms.assetid: 71d16b59-3e5c-4a2a-9217-5e0f7a2d4478
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: _DXVA_COPPStatusOutput, *LPDXVA_COPPStatusOutput, DXVA_COPPStatusOutput
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: dxva.h
req.include-header: Dxva.h
req.target-type: Windows
req.target-min-winverclnt: This structure applies only to Windows Server 2003 with SP1 and later, and Windows XP with SP2 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXVA_COPPStatusOutput
req.alt-loc: dxva.h
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

# _DXVA_COPPStatusOutput structure



## -description
The DXVA_COPPStatusOutput structure describes the status returned from a query on a protected video session that is associated with a DirectX VA COPP device.



## -syntax

````
typedef struct _DXVA_COPPStatusOutput {
  GUID  macKDI;
  ULONG cbSizeData;
  UCHAR COPPStatus[4076];
} DXVA_COPPStatusOutput, *LPDXVA_COPPStatusOutput;
````


## -struct-fields

### -field macKDI

Specifies a message authentication code (MAC) GUID for the status at <b>COPPStatus</b>. The application that requested the status can use the MAC to verify that the transmission of the status was secure (that is, it was not tampered with in transit from the driver). 


### -field cbSizeData

Specifies the size, in bytes, of the status data at <b>COPPStatus</b>.


### -field COPPStatus

Specifies an array that contains the status data. The display driver should return status data in one of the following ways, depending on the input value that was specified in the <b>guidStatusRequestID</b> member of the <a href="display.dxva_coppstatusinput">DXVA_COPPStatusInput</a> structure: 

<table>
<tr>
<th>Input value</th>
<th>Output status data</th>
</tr>
<tr>
<td>
DXVA_COPPQueryDisplayData

</td>
<td>
Pointer to a <a href="display.dxva_coppstatusdisplaydata">DXVA_COPPStatusDisplayData</a> structure

</td>
</tr>
<tr>
<td>


### -field DXVA_COPPQueryProtectionType, 
### -field DXVA_COPPQueryConnectorType, 
### -field DXVA_COPPQueryLocalProtectionLevel, 
### -field DXVA_COPPQueryGlobalProtectionLevel or 
### -field DXVA_COPPQueryBusData



</td>
<td>
Pointer to a <a href="display.dxva_coppstatusdata">DXVA_COPPStatusData</a> structure

</td>
</tr>
<tr>
<td>
DXVA_COPPQueryHDCPKeyData

</td>
<td>
Pointer to a <a href="display.dxva_coppstatushdcpkeydata">DXVA_COPPStatusHDCPKeyData</a> structure

</td>
</tr>
<tr>
<td>
DXVA_COPPQuerySignaling

</td>
<td>
Pointer to a <a href="display.dxva_coppstatussignalingcmddata">DXVA_COPPStatusSignalingCmdData</a> structure

</td>
</tr>
</table>
 


## -remarks
Status requests are passed in the <i>pInput</i> parameter of the <a href="display.coppquerystatus">COPPQueryStatus</a> function. The <a href="display.dxva_coppstatusinput">DXVA_COPPStatusInput</a> structure describes a request for status. Status information is returned through the <i>pOutput</i> parameter of <i>COPPQueryStatus</i>. 


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
This structure applies only to Windows Server 2003 with SP1 and later, and Windows XP with SP2 and later.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Dxva.h (include Dxva.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="display.coppquerystatus">COPPQueryStatus</a>
</dt>
<dt>
<a href="display.dxva_coppsetprotectionlevelcmddata">DXVA_COPPSetProtectionLevelCmdData</a>
</dt>
<dt>
<a href="display.dxva_coppstatusdata">DXVA_COPPStatusData</a>
</dt>
<dt>
<a href="display.dxva_coppstatusdisplaydata">DXVA_COPPStatusDisplayData</a>
</dt>
<dt>
<a href="display.dxva_coppstatushdcpkeydata">DXVA_COPPStatusHDCPKeyData</a>
</dt>
<dt>
<a href="display.dxva_coppstatusinput">DXVA_COPPStatusInput</a>
</dt>
<dt>
<a href="display.dxva_coppstatussignalingcmddata">DXVA_COPPStatusSignalingCmdData</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXVA_COPPStatusOutput structure%20 RELEASE:%20(12/8/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
