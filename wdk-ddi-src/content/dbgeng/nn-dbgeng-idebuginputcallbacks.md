---
UID: NN.dbgeng.IDebugInputCallbacks
title: IDebugInputCallbacks
author: windows-driver-content
description: IDebugInputCallbacks interface
old-location: debugger\idebuginputcallbacks.htm
old-project: debugger
ms.assetid: 2122d970-1d1c-4ef0-b8f7-92ef6e4f0731
ms.author: windowsdriverdev
ms.date: 12/8/2017
ms.keywords: DebugCreateEx
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: interface
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugInputCallbacks
req.alt-loc: dbgeng.h
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

# IDebugInputCallbacks interface



## -description

## -inheritance
The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IDebugInputCallbacks</b> interface inherits from the <a href="com.iunknown" xmlns:loc="http://microsoft.com/wdcml/l10n"><b>IUnknown</b></a> interface. <b>IDebugInputCallbacks</b> also has these types of members:

The <b>IDebugInputCallbacks</b> interface has these methods.

This method is called by the engine to indicate that it is no longer waiting for input.


This method is called by the engine to indicate that it is waiting for a line of input.


 


## -members
The <b>IDebugInputCallbacks</b> interface has these methods.
<table class="members" id="memberListMethods">
<tr>
<th align="left" width="37%">Method</th>
<th align="left" width="63%">Description</th>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="debugger.idebuginputcallbacks_endinput">EndInput</a>
</td>
<td align="left" width="63%">
This method is called by the engine to indicate that it is no longer waiting for input.


</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="debugger.idebuginputcallbacks_startinput">StartInput</a>
</td>
<td align="left" width="63%">
This method is called by the engine to indicate that it is waiting for a line of input.


</td>
</tr>
</table>This method is called by the engine to indicate that it is no longer waiting for input.


This method is called by the engine to indicate that it is waiting for a line of input.


 


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Dbgeng.h (include Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>