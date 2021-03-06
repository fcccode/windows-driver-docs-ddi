---
UID: NS:wdm._OSVERSIONINFOW
title: "_OSVERSIONINFOW"
author: windows-driver-content
description: The RTL_OSVERSIONINFOW structure contains operating system version information.
old-location: kernel\rtl_osversioninfow.htm
old-project: kernel
ms.assetid: 04e50a2c-eb85-4fc8-9751-798397eddf95
ms.author: windowsdriverdev
ms.date: 3/28/2018
ms.keywords: "*LPOSVERSIONINFOW, *POSVERSIONINFOW, *PRTL_OSVERSIONINFOW, OSVERSIONINFO, OSVERSIONINFOW, PRTL_OSVERSIONINFOW, PRTL_OSVERSIONINFOW structure pointer [Kernel-Mode Driver Architecture], RTL_OSVERSIONINFOW, RTL_OSVERSIONINFOW structure [Kernel-Mode Driver Architecture], _OSVERSIONINFOW, kernel.rtl_osversioninfow, kstruct_d_61d86312-0550-4bce-81c8-bb29551cc586.xml, wdm/PRTL_OSVERSIONINFOW, wdm/RTL_OSVERSIONINFOW"
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wdm.h
req.include-header: Ntddk.h
req.target-type: Windows
req.target-min-winverclnt: 
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
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (see Remarks section)
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	wdm.h
api_name:
-	RTL_OSVERSIONINFOW
product:
- Windows
targetos: Windows
req.typenames: OSVERSIONINFOW, *POSVERSIONINFOW, *LPOSVERSIONINFOW, RTL_OSVERSIONINFOW, *PRTL_OSVERSIONINFOW
req.product: Windows 10 or later.
---

# _OSVERSIONINFOW structure


## -description


The <b>RTL_OSVERSIONINFOW</b> structure contains operating system version information. The information includes major and minor version numbers, a build number, a platform identifier, and descriptive text about the operating system. The <b>RTL_OSVERSIONINFOW</b> structure is used with <a href="https://msdn.microsoft.com/library/windows/hardware/ff561910">RtlGetVersion</a>. 


## -struct-fields




### -field dwOSVersionInfoSize

The size in bytes of an <b>RTL_OSVERSIONINFOW</b> structure. This member must be set before the structure is used with <a href="https://msdn.microsoft.com/library/windows/hardware/ff561910">RtlGetVersion</a>.


### -field dwMajorVersion

The major version number of the operating system. For example, for Windows 2000, the major version number is five. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563620">RTL_OSVERSIONINFOEXW</a>.


### -field dwMinorVersion

The minor version number of the operating system. For example, for Windows 2000 the minor version number is zero. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563620">RTL_OSVERSIONINFOEXW</a>. 


### -field dwBuildNumber

The build number of the operating system.


### -field dwPlatformId

The operating system platform. For Microsoft Win32 on NT-based operating systems, <b>RtlGetVersion</b> returns the value VER_PLATFORM_WIN32_NT.


### -field szCSDVersion

The service-pack version string. This member contains a null-terminated string, such as "Service Pack 3", which indicates the latest service pack installed on the system. If no service pack is installed, <b>RtlGetVersion</b> might not initialize this string. Initialize <i>szCSDVersion</i> to zero (empty string) before the call to <b>RtlGetVersion</b>.


## -remarks



For a list of the major and minor version numbers for the various versions of Windows, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563620">RTL_OSVERSIONINFOEXW</a>.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff563620">RTL_OSVERSIONINFOEXW</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff561910">RtlGetVersion</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff563026">RtlVerifyVersionInfo</a>
 

 

