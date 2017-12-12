---
UID: NF.ndis.NdisGetCurrentProcessorCounts
title: NdisGetCurrentProcessorCounts function
author: windows-driver-content
description: The NdisGetCurrentProcessorCounts function returns counts for the current processor that a driver can use to determine CPU usage for a particular time interval.
old-location: netvista\ndisgetcurrentprocessorcounts.htm
old-project: netvista
ms.assetid: 43a75def-0288-4615-ac85-b5e340aa11e6
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: NdisGetCurrentProcessorCounts
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and later drivers in Windows Vista and later. Supported for NDIS 5.1 drivers (see       NdisGetCurrentProcessorCounts (NDIS 5.1)) in Windows XP and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisGetCurrentProcessorCounts
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Miscellaneous_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
---

# NdisGetCurrentProcessorCounts function



## -description
The
  <b>NdisGetCurrentProcessorCounts</b> function returns counts for the current processor that a driver can use
  to determine CPU usage for a particular time interval.



## -syntax

````
VOID NdisGetCurrentProcessorCounts(
  _Out_ PULONG pIdleCount,
  _Out_ PULONG pKernelAndUser,
  _Out_ PULONG pIndex
);
````


## -parameters

### -param pIdleCount [out]

A pointer to a caller-supplied variable in which this function returns the cumulative idle time
     for the processor since the system was booted.


### -param pKernelAndUser [out]

A pointer to a caller-supplied variable in which this function returns the cumulative processing
     time (kernel-mode time plus user-mode time) for the processor since the system was booted.


### -param pIndex [out]

A pointer to a caller-supplied variable in which this function returns a zero-based index that
     identifies the processor within the computer.


## -returns
None


## -remarks
<b>NdisGetCurrentProcessorCounts</b> returns idle and CPU-usage counts that the caller can use to
    determine CPU usage for the current processor. The CPU utilization value indicates how loaded the CPU was
    since the immediately preceding call to this function. If the CPU was heavily loaded, such a driver can
    change how it handles certain operations to improve driver performance.

A driver might call 
    <b>NdisGetCurrentProcessorCounts</b> periodically within a timer function. The driver can use the
    following calculation to determine the CPU usage for a multiple of the timer interval:

where:

CpuUsage is CPU usage as a percentage of the total interval time

Idle is the 
      <i>IdleCount</i> value returned by the most recent call to 
      <b>NdisGetCurrentProcessorCounts</b>

Idle[n] is an 
      <i>IdleCount</i> value returned by a previous call, stored as the nth element in an array

KernelandUser is the 
      <i>KernelAndUser</i> value returned by the most recent call to 
      <b>NdisGetCurrentProcessorCounts</b>

KernelandUser[n] is the KernelandUser value returned by a previous call, stored as the nth element
      in an array


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Supported for NDIS 6.0 and later drivers in Windows Vista and later. Supported for NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/54316bfa-4fdc-4db9-b4bf-2e0d5fcca313">
   NdisGetCurrentProcessorCounts (NDIS 5.1)</a>) in Windows XP and later.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
&lt;= DISPATCH_LEVEL

</td>
</tr>
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.ndis_irql_miscellaneous_function">Irql_Miscellaneous_Function</a>
</td>
</tr>
</table>