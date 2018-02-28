---
UID: NC:wdm.GET_DMA_ADAPTER
title: GET_DMA_ADAPTER
author: windows-driver-content
description: The GetDmaAdapter routine returns a DMA_ADAPTER structure for the target device.
old-location: kernel\getdmaadapter.htm
old-project: kernel
ms.assetid: 0F703E88-2650-4451-9F5A-05FBCF33C131
ms.author: windowsdriverdev
ms.date: 2/24/2018
ms.keywords: GET_DMA_ADAPTER, GetDmaAdapter, GetDmaAdapter routine [Kernel-Mode Driver Architecture], drvr_interface_5c7fd89d-0b6c-45e7-8559-8666f43beb9a.xml, kernel.busgetdmaadapter, kernel.getdmaadapter, ntddk/GetDmaAdapter
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: wdm.h
req.include-header: Ntddk.h, Wdm.h
req.target-type: Desktop
req.target-min-winverclnt: Available starting with  Windows 2000.
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
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	Ntddk.h
api_name:
-	GetDmaAdapter
product: Windows
targetos: Windows
req.typenames: WDI_TYPE_PMK_NAME, *PWDI_TYPE_PMK_NAME
req.product: Windows 10 or later.
---


# GET_DMA_ADAPTER callback function
The <i>GetDmaAdapter</i> routine returns a <a href="..\wdm\ns-wdm-_dma_adapter.md">DMA_ADAPTER</a> structure for the target device.

## Syntax

```
GET_DMA_ADAPTER GetDmaAdapter;

_DMA_ADAPTER * GetDmaAdapter(
  PVOID Context,
  _DEVICE_DESCRIPTION * DeviceDescriptor,
  PULONG NumberOfMapRegisters
)
{...}
```

## Parameters

`Context`

A pointer to interface-specific context information. The caller passes the value that is passed as the <b>Context</b> member of the <a href="..\wdm\ns-wdm-_bus_interface_standard.md">BUS_INTERFACE_STANDARD</a> structure for the interface.

`DeviceDescriptor`

A pointer to a <a href="..\wdm\ns-wdm-_device_description.md">DEVICE_DESCRIPTION</a> structure that describes the attributes of the physical device.

`NumberOfMapRegisters`

A pointer to, on output, the maximum number of map registers that the driver can allocate for any DMA transfer operation. The caller must allocate a <b>LONG</b> variable to receive this data.


## Return Value

The <i>GetDmaAdapter</i> routine returns a pointer to a <a href="..\wdm\ns-wdm-_dma_adapter.md">DMA_ADAPTER</a> structure when successful. If an adapter structure cannot be allocated, the routine returns <b>NULL</b>.

## Remarks

If the driver is executing at IRQL = PASSIVE_LEVEL, it should obtain a device's DMA adapter object by calling the <a href="..\wdm\nf-wdm-iogetdmaadapter.md">IoGetDmaAdapter</a> function. <b>IoGetDmaAdapter</b> detects whether the bus driver supports the <a href="..\wdm\ns-wdm-_bus_interface_standard.md">BUS_INTERFACE_STANDARD</a> interface; if it does, <b>IoGetDmaAdapter</b> calls the routine pointed to by the <i>GetDmaAdapter</i> member of this interface to obtain the adapter object. Otherwise, <b>IoGetDmaAdapter</b> calls an equivalent legacy routine.

However, if a driver must obtain an adapter object while running at IRQL ≥ DISPATCH_LEVEL, it cannot do so with the <a href="..\wdm\nf-wdm-iogetdmaadapter.md">IoGetDmaAdapter</a> function. In such a case, the driver must query for the <a href="..\wdm\ns-wdm-_bus_interface_standard.md">BUS_INTERFACE_STANDARD</a> interface while still at IRQL = PASSIVE_LEVEL by issuing an <a href="https://msdn.microsoft.com/library/windows/hardware/ff551687">IRP_MN_QUERY_INTERFACE</a> request.

## Requirements
| &nbsp; | &nbsp; |
| ---- |:---- |
| **Windows version** | Available starting with  Windows 2000.  |
| **Target Platform** | Desktop |
| **Header** | wdm.h (include Ntddk.h, Wdm.h) |
| **IRQL** | PASSIVE_LEVEL |

## See Also

<a href="..\wdm\ns-wdm-_device_description.md">DEVICE_DESCRIPTION</a>



<a href="..\wdm\ns-wdm-_dma_adapter.md">DMA_ADAPTER</a>



<a href="..\wdm\ns-wdm-_bus_interface_standard.md">BUS_INTERFACE_STANDARD</a>



<a href="..\wdm\nf-wdm-iogetdmaadapter.md">IoGetDmaAdapter</a>



 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20GET_DMA_ADAPTER routine%20 RELEASE:%20(2/24/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>