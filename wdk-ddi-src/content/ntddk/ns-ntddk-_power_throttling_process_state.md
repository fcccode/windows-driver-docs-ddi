---
UID: NS.NTDDK._POWER_THROTTLING_PROCESS_STATE
title: _POWER_THROTTLING_PROCESS_STATE
author: windows-driver-content
description: Stores the throttling policies and how to apply them to a target process when that process is subject to power management.
old-location: kernel\power_throttling_process_state.htm
old-project: kernel
ms.assetid: f22be66a-1f1c-4999-a99e-9a8575313239
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: _POWER_THROTTLING_PROCESS_STATE, POWER_THROTTLING_PROCESS_STATE, *PPOWER_THROTTLING_PROCESS_STATE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: ntddk.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1709
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: POWER_THROTTLING_PROCESS_STATE
req.alt-loc: Ntddk.h
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

# _POWER_THROTTLING_PROCESS_STATE structure



## -description
Stores the throttling policies and how to apply them to a target process when that process is subject to power management.



## -syntax

````
typedef struct _POWER_THROTTLING_PROCESS_STATE {
  ULONG  Version;
  ULONG  ControlMask;
  ULONG  StateMask;
} POWER_THROTTLING_PROCESS_STATE, POWER_THROTTLING_PROCESS_STATE;
````


## -struct-fields

### -field Version

The version of this structure. Set to PROCESS_POWER_THROTTLING_CURRENT_VERSION.


### -field ControlMask

Flags that enable the caller to take control of the power throttling mechanism.

<ul>
<li>PROCESS_POWER_THROTTLING_EXECUTION_SPEED: Manages the execution speed of the process.</li>
</ul>

### -field StateMask

Flags that manage the power throttling mechanism on/off state.

<ul>
<li>PROCESS_POWER_THROTTLING_EXECUTION_SPEED: Manages the execution speed of the process.</li>
</ul>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 10, version 1709

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
Header

</th>
<td width="70%">
<dl>
<dt>Ntddk.h</dt>
</dl>
</td>
</tr>
</table>