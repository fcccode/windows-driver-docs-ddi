---
UID: NC:mrx.PMRX_FINALIZE_V_NET_ROOT_CALLDOWN
title: PMRX_FINALIZE_V_NET_ROOT_CALLDOWN
author: windows-driver-content
description: The MRxFinalizeVNetRoot routine is called by RDBSS to request that a network mini-redirector finalize a V_NET_ROOT structure.
old-location: ifsk\mrxfinalizevnetroot.htm
old-project: ifsk
ms.assetid: 13d0c903-57b6-4a57-977a-bf1bd651660f
ms.author: windowsdriverdev
ms.date: 3/29/2018
ms.keywords: MRxFinalizeVNetRoot, MRxFinalizeVNetRoot routine [Installable File System Drivers], PMRX_FINALIZE_V_NET_ROOT_CALLDOWN, ifsk.mrxfinalizevnetroot, mrx/MRxFinalizeVNetRoot, mrxref_a5cc53ee-2d11-4987-aeb4-fe9cc2cc9b3e.xml
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: mrx.h
req.include-header: Mrx.h
req.target-type: Desktop
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
req.irql: 
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	mrx.h
api_name:
-	MRxFinalizeVNetRoot
product:
- Windows
targetos: Windows
req.typenames: SetDSMCounters_IN, *PSetDSMCounters_IN
---

# PMRX_FINALIZE_V_NET_ROOT_CALLDOWN callback


## -description


The <i>MRxFinalizeVNetRoot</i> routine is called by <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/ifs/the-rdbss-driver-and-library">RDBSS</a> to request that a network mini-redirector finalize a V_NET_ROOT structure.


## -parameters




### -param VirtualNetRoot


### -param Force








#### - ForceDisconnect [in]

A pointer to a Boolean value that indicates if the disconnect is to be forced. RDBSS currently passes <b>FALSE</b> for this parameter in all cases.


#### - pVNetRoot [in, out]

A pointer to the V_NET_ROOT structure to finalize. 


## -returns



<i>MRxFinalizeVNetRoot</i> returns STATUS_SUCCESS on success. 




## -remarks



<i>MRxFinalizeVNetRoot</i> is called by RDBSS when it finalizes a NET_ROOT structure. 

After the <i>MRxFinalizeVNetRoot</i> returns, RDBSS uninitializes the V_NET_ROOT structure members, dereferences the NET_ROOT structure, and releases the memory for the V_NET_ROOT structure.

RDBSS ignores the return value from <i>MRxFinalizeVNetRoot</i>. 




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff549864">MRxCreateSrvCall</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff549869">MRxCreateVNetRoot</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff550649">MRxExtractNetRootName</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff550653">MRxFinalizeNetRoot</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff550750">MRxPreparseName</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff550824">MRxSrvCallWinnerNotify</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff554426">RxFinalizeSrvCall</a>
 

 

