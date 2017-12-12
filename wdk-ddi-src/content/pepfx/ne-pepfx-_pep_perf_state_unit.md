---
UID: NE.pepfx._PEP_PERF_STATE_UNIT
title: _PEP_PERF_STATE_UNIT
author: windows-driver-content
description: The PEP_PERF_STATE_UNIT enumeration indicates the measurement units in which the performance state (P-state) of a component is specified.
old-location: kernel\pep_perf_state_unit.htm
old-project: kernel
ms.assetid: 5E5F049D-4306-4382-B3F7-06C1F5FFE93E
ms.author: windowsdriverdev
ms.date: 12/7/2017
ms.keywords: _PEP_PERF_STATE_UNIT, PEP_PERF_STATE_UNIT, *PPEP_PERF_STATE_UNIT
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: enum
req.header: pepfx.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Supported starting with Windows 10.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PEP_PERF_STATE_UNIT
req.alt-loc: pepfx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks.
---

# _PEP_PERF_STATE_UNIT enumeration



## -description
The <b>PEP_PERF_STATE_UNIT</b> enumeration indicates the measurement units in which the performance state (P-state) of a component is specified.



## -syntax

````
typedef enum _PEP_PERF_STATE_UNIT { 
  PepPerfStateUnitOther      = 0,
  PepPerfStateUnitFrequency,
  PepPerfStateUnitBandwidth,
  PepPerfStateUnitMax
} PEP_PERF_STATE_UNIT;
````


## -enum-fields

### -field PepPerfStateUnitOther

Some other type of measurement units not explicitly described by this enumeration.


### -field PepPerfStateUnitFrequency

Hertz (frequency units).


### -field PepPerfStateUnitBandwidth

Bits per second (bandwidth units).


### -field PepPerfStateUnitMax

Reserved for use by operating system.


## -remarks
The <b>Type</b> member of the <a href="kernel.pep_component_perf_set">PEP_COMPONENT_PERF_SET</a> structure is a <b>PEP_PERF_STATE_UNIT</b> enumeration value.


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Supported starting with Windows 10.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Pepfx.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.pep_component_perf_set">PEP_COMPONENT_PERF_SET</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20PEP_PERF_STATE_UNIT enumeration%20 RELEASE:%20(12/7/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
