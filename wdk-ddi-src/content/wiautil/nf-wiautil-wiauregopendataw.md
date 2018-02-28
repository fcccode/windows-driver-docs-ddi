---
UID: NF:wiautil.wiauRegOpenDataW
title: wiauRegOpenDataW function
author: windows-driver-content
description: The wiauRegOpenData function opens the DeviceData registry key.
old-location: image\wiauregopendata.htm
old-project: image
ms.assetid: f289dfa8-26e4-426b-8058-8c2464e47e2a
ms.author: windowsdriverdev
ms.date: 2/23/2018
ms.keywords: image.wiauregopendata, wiauFncs_1718e270-b13c-4325-bb4a-a872becaa8bb.xml, wiauRegOpenData, wiauRegOpenData function [Imaging Devices], wiauRegOpenDataA, wiauRegOpenDataW, wiautil/wiauRegOpenData
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wiautil.h
req.include-header: Wiautil.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows XP and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.exe
req.dll: 
req.irql: 
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	wiautil.h
api_name:
-	wiauRegOpenData
product: Windows
targetos: Windows
req.typenames: SKIP_AMOUNT
req.product: Windows 10 or later.
---


# wiauRegOpenDataW function
The <b>wiauRegOpenData</b> function opens the <b>DeviceData</b> registry key.

## Syntax

````
HRESULT _stdcall wiauRegOpenData(
  _In_    HKEY hkeyAncestor,
  _Inout_ HKEY *phkeyDeviceData
);
````

## Parameters

`hkeyAncestor`

Specifies the key handle of the parent. This parameter should be set to the value used in the call to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543824">IStiUSD::Initialize</a> method.

`phkeyDeviceData`

Pointer to a memory location that receives the opened key handle.


## Return Value

On success, the function returns S_OK. If the function fails, it returns a standard COM error.

## Remarks

Call this function only in the STI <a href="https://msdn.microsoft.com/library/windows/hardware/ff543824">IStiUSD::Initialize</a> method. Call <b>RegCloseKey</b> (described in the Microsoft Windows SDK documentation) when you are finished with the registry.

## Requirements
| &nbsp; | &nbsp; |
| ---- |:---- |
| **Windows version** | Available in Windows XP and later.  |
| **Target Platform** | Desktop |
| **Header** | wiautil.h (include Wiautil.h) |
| **Library** | NtosKrnl.exe |

## See Also

<a href="https://msdn.microsoft.com/library/windows/hardware/ff543824">IStiUSD::Initialize</a>



 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [image\image]:%20wiauRegOpenData function%20 RELEASE:%20(2/23/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>