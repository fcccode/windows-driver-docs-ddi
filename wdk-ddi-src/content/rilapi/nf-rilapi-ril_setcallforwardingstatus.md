---
UID: NF:rilapi.RIL_SetCallForwardingStatus
title: RIL_SetCallForwardingStatus function
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\ril_setcallforwardingstatus.htm
old-project: netvista
ms.assetid: c73e3b75-e11d-44b8-9a4a-c98ccfe1c820
ms.author: windowsdriverdev
ms.date: 3/26/2018
ms.keywords: RIL_SetCallForwardingStatus, RIL_SetCallForwardingStatus method [Network Drivers Starting with Windows Vista], netvista.ril_setcallforwardingstatus, rilapi/RIL_SetCallForwardingStatus
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: rilapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
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
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	rilapi.h
api_name:
-	RIL_SetCallForwardingStatus
product:
- Windows
targetos: Windows
req.typenames: PTP_VENDOR_DATA_OUT, *PPTP_VENDOR_DATA_OUT
req.product: Windows 10 or later.
---

# RIL_SetCallForwardingStatus function


## -description


This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. 

            


## -parameters




### -param hRil


### -param lpContext


### -param dwExecutor


### -param dwReason


### -param fAllClasses


### -param dwInfoClasses


### -param dwStatus


## -returns



If this method succeeds, it returns <b xmlns:loc="http://microsoft.com/wdcml/l10n">S_OK</b>. Otherwise, it returns an <b xmlns:loc="http://microsoft.com/wdcml/l10n">HRESULT</b> error code.



