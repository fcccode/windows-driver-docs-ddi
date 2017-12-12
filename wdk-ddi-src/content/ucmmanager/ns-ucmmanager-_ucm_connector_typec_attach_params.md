---
UID: NS.UCMMANAGER._UCM_CONNECTOR_TYPEC_ATTACH_PARAMS
title: _UCM_CONNECTOR_TYPEC_ATTACH_PARAMS
author: windows-driver-content
description: Describes the partner that is currently attached to the connector.
old-location: buses\ucm_connector_typec_attach_params.htm
old-project: usbref
ms.assetid: D1D4B9D8-0BBF-4592-9EC8-ED294D6D0C90
ms.author: windowsdriverdev
ms.date: 12/6/2017
ms.keywords: _UCM_CONNECTOR_TYPEC_ATTACH_PARAMS, *PUCM_CONNECTOR_TYPEC_ATTACH_PARAMS, UCM_CONNECTOR_TYPEC_ATTACH_PARAMS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: ucmmanager.h
req.include-header: Ucmcx.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 1.15
req.umdf-ver: 2.15
req.alt-api: UCM_CONNECTOR_TYPEC_ATTACH_PARAMS
req.alt-loc: Ucmmanager.h
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
req.product: Windows 10 or later.
---

# _UCM_CONNECTOR_TYPEC_ATTACH_PARAMS structure



## -description
Describes the partner that is currently attached to the connector.



## -syntax

````
typedef struct _UCM_CONNECTOR_TYPEC_ATTACH_PARAMS {
  ULONG              Size;
  UCM_TYPEC_PARTNER  PortPartnerType;
  UCM_TYPEC_CURRENT  CurrentAdvertisement;
  UCM_CHARGING_STATE ChargingState;
} UCM_CONNECTOR_TYPEC_ATTACH_PARAMS, *PUCM_CONNECTOR_TYPEC_ATTACH_PARAMS;
````


## -struct-fields

### -field Size

Size of the <b>UCM_CONNECTOR_TYPEC_ATTACH_PARAMS</b> structure. 


### -field PortPartnerType

The type of partner attached to the connector, indicated by a <a href="buses.ucm_type_c_port_state">UCM_TYPEC_PARTNER</a> value.


### -field CurrentAdvertisement

Power sourcing capabilities of: the partner port when <b>PortPartnerType</b> is <b>UcmTypeCPortStateDfp</b>; the local port when <b>PortPartnerType</b> is not <b>UcmTypeCPortStateDfp</b>. 


### -field ChargingState

Optional. Charging state of the port indicated by one of the <a href="buses.ucm_charging_state">UCM_CHARGING_STATE</a>-typed flags. 


## -remarks
Initialize this structure by calling <a href="buses.ucm_connector_typec_attach_params_init">UCM_CONNECTOR_TYPEC_ATTACH_PARAMS_INIT</a>. An initialized <b>UCM_CONNECTOR_TYPEC_ATTACH_PARAMS</b> structure is an input parameter value to <a href="buses.ucmconnectortypecattach">UcmConnectorTypeCAttach</a> that is used by the client driver to notify UcmCx about the Attached state of the port.


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
Minimum KMDF version

</th>
<td width="70%">
1.15

</td>
</tr>
<tr>
<th width="30%">
Minimum UMDF version

</th>
<td width="70%">
2.15

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ucmmanager.h (include Ucmcx.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="buses.ucmconnectortypecattach">UcmConnectorTypeCAttach</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20UCM_CONNECTOR_TYPEC_ATTACH_PARAMS structure%20 RELEASE:%20(12/6/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
