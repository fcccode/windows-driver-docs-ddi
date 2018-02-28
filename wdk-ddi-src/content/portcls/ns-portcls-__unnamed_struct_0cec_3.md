---
UID: NS:portcls.__unnamed_struct_0cec_3
title: PCPROPERTY_ITEM
author: windows-driver-content
description: The PCPROPERTY_ITEM structure describes a property that is supported by a particular filter, pin, or node.
old-location: audio\pcproperty_item.htm
old-project: audio
ms.assetid: aec5b9df-22cc-4ef8-8d09-103124ab357c
ms.author: windowsdriverdev
ms.date: 2/20/2018
ms.keywords: portcls/PCPROPERTY_ITEM, PPCPROPERTY_ITEM structure pointer [Audio Devices], PPCPROPERTY_ITEM, audio.pcproperty_item, *PPCPROPERTY_ITEM, PCPROPERTY_ITEM structure [Audio Devices], PCPROPERTY_ITEM, audpc-struct_6d95504b-3ecc-47dc-b98f-b6ebfa40d749.xml, portcls/PPCPROPERTY_ITEM
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: portcls.h
req.include-header: Portcls.h
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
req.irql: PASSIVE_LEVEL
topictype:
-	APIRef
-	kbSyntax
apitype:
-	HeaderDef
apilocation:
-	portcls.h
apiname:
-	PCPROPERTY_ITEM
product: Windows
targetos: Windows
req.typenames: PCPROPERTY_ITEM, *PPCPROPERTY_ITEM
---

# *PPCPROPERTY_ITEM structure
The <b>PCPROPERTY_ITEM</b> structure describes a property that is supported by a particular filter, pin, or node.

## Syntax
````
typedef struct {
  const GUID            *Set;
  ULONG                 Id;
  ULONG                 Flags;
  PCPFNPROPERTY_HANDLER Handler;
} PCPROPERTY_ITEM, *PPCPROPERTY_ITEM;
````

## Members


## Remarks
The <b>PCPROPERTY_ITEM</b> structure specifies a particular property item in an automation table. The <a href="..\portcls\ns-portcls-__unnamed_struct_0cec_6.md">PCAUTOMATION_TABLE</a> structure points to an array of <b>PCPROPERTY_ITEM</b> structures.

When calling the <b>Handler</b> routine, the caller passes in a single call parameter, which is a pointer to a <a href="..\portcls\ns-portcls-_pcproperty_request.md">PCPROPERTY_REQUEST</a> structure. This structure is allocated by the caller, and the caller frees it under either of the following conditions:

<ol>
<li>
If the <b>Handler</b> routine returns any status code other than STATUS_PENDING, the caller frees the structure. In this case, the miniport driver should not attempt to access the structure after the <b>Handler</b> routine returns.

</li>
<li>
The <b>Handler</b> routine can also return STATUS_PENDING, in which case the miniport driver is obliged to call <a href="..\portcls\nf-portcls-pccompletependingpropertyrequest.md">PcCompletePendingPropertyRequest</a> at a later time to complete the pending property request. The <b>PcCompletePendingPropertyRequest</b> function frees the structure. After calling <b>PcCompletePendingPropertyRequest</b>, the miniport driver should not attempt to access the structure.

</li>
</ol>
If the miniport driver attempts to access the structure after it has been freed, this action is likely to cause a bug check or to corrupt another driver's memory.

For more information about serialization and raw serialization of a property set, see <a href="https://msdn.microsoft.com/a385929e-1934-4d88-aaf9-ff1ddbfd30f7">KS Properties</a>.

## Requirements
| &nbsp; | &nbsp; |
| ---- |:---- |
| **Header** | portcls.h (include Portcls.h) |

## See Also

<a href="..\portcls\nf-portcls-pccompletependingpropertyrequest.md">PcCompletePendingPropertyRequest</a>



<a href="..\portcls\ns-portcls-_pcproperty_request.md">PCPROPERTY_REQUEST</a>



 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PCPROPERTY_ITEM structure%20 RELEASE:%20(2/20/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>