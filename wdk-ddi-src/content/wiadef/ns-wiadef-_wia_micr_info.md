---
UID: NS:wiadef._WIA_MICR_INFO
title: "_WIA_MICR_INFO"
author: windows-driver-content
description: The WIA_MICR_INFO structure stores information for one decoded MICR code.
old-location: image\wia_micr_info.htm
old-project: image
ms.assetid: E91F5D6F-40F9-4CE2-8C51-4CA7FB27F2C3
ms.author: windowsdriverdev
ms.date: 2/27/2018
ms.keywords: WIA_MICR_INFO, WIA_MICR_INFO structure [Imaging Devices], _WIA_MICR_INFO, image.wia_micr_info, wiadef/WIA_MICR_INFO
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wiadef.h
req.include-header: Wiadef.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: WDTFSystemAction.idl
req.max-support: 
req.namespace: Microsoft.WDTF
req.assembly: WDTFSystemAction.Interop.dll
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
-	wiadef.h
api_name:
-	WIA_MICR_INFO
product:
- Windows
targetos: Windows
req.typenames: WIA_MICR_INFO
req.product: Windows 10 or later.
---

# _WIA_MICR_INFO structure


## -description


The <b>WIA_MICR_INFO</b> structure stores information for one decoded MICR code.


## -struct-fields




### -field Size

The total size of this structure, in bytes.


### -field Page

The page number where the MICR code was detected. A zero-based index referring to the current scan job.


### -field Length

Length of the MICR text, in characters, excluding the length of the NULL terminator.


### -field Text

Placeholder for a NULL terminated character string containing the MICR text.

