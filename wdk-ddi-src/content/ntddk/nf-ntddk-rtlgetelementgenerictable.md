---
UID: NF.ntddk.RtlGetElementGenericTable
title: RtlGetElementGenericTable function
author: windows-driver-content
description: The RtlGetElementGenericTable routine returns a pointer to the caller-supplied data for a particular generic table element.
old-location: ifsk\rtlgetelementgenerictable.htm
old-project: ifsk
ms.assetid: 85b5fce8-eac4-4cd8-9a24-22564aae915a
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: RtlGetElementGenericTable
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntddk.h
req.include-header: Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlGetElementGenericTable
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: Any level (See Remarks)
---

# RtlGetElementGenericTable function



## -description
The <b>RtlGetElementGenericTable</b> routine returns a pointer to the caller-supplied data for a particular generic table element. 



## -syntax

````
PVOID RtlGetElementGenericTable(
  _In_ PRTL_GENERIC_TABLE Table,
  _In_ ULONG              I
);
````


## -parameters

### -param Table [in]

Pointer to the generic table (<a href="ifsk.rtl_generic_table">RTL_GENERIC_TABLE</a>) from which the <i>I</i>th element is to be retrieved. The table must have been initialized by calling <b>RtlInitializeGenericTable</b>.


### -param I [in]

Index of the element selected. This value is zero-based, so the index of the last-inserted element currently in <i>Table</i> is always one less than the value returned by <b>RtlNumberGenericTableElements</b>. 


## -returns
<b>RtlGetElementGenericTable</b> returns a pointer to the caller-supplied data for the <i>I</i>th element in the generic table. It returns <b>NULL</b> if the given <i>I</i> is too large or if the generic table currently has no elements. 


## -remarks
<b>RtlGetElementGenericTable</b> returns the <i>I</i>th element inserted in the generic table. To retrieve the first element, set <i>I</i> to zero. To retrieve the last element, set <i>I</i> to (<b>RtlNumberGenericTableElements</b>(<i>Table</i>)-1). Note that if an element is deleted from the generic table, the indexes of all elements inserted after the deleted element are decremented. Thus an element's index might change over time. 

<b>RtlGetElementGenericTable</b> is more efficient than <b>RtlLookupElementGenericTable</b> if the caller can supply the index of a particular element for which the caller needs access to the associated data. However, calling <b>RtlGetElementGenericTable</b> repeatedly to test for such an element is less efficient than calling <b>RtlLookupElementGenericTable</b> to locate it. 

Callers of the Rtl..GenericTable routines are responsible for exclusively synchronizing access to the generic table. An exclusive fast mutex is the most efficient synchronization mechanism to use for this purpose. 

By default, the operating system uses splay trees to implement generic tables. Under some circumstances, operations on a splay tree will make the tree deep and narrow and might even turn it into a straight line. Very deep trees degrade the performance of searches. You can ensure a more balanced, shallower tree implementation of generic tables by using Adelson-Velsky/Landis (AVL) trees. If you want to configure the generic table routines to use AVL trees instead of splay trees in your driver, insert the following define statement in a common header file before including <i>Ntddk.h</i>:

#define RTL_USE_AVL_TABLES 0

If RTL_USE_AVL_TABLES is not defined, you must use the AVL form of the generic table routines. For example, use the <b>RtlGetElementGenericTableAvl</b> routine instead of <b>RtlGetElementGenericTable</b>. In the call to <b>RtlGetElementGenericTableAvl</b>, the caller must pass a <a href="ifsk.rtl_avl_table">RTL_AVL_TABLE</a> table structure rather than <a href="ifsk.rtl_generic_table">RTL_GENERIC_TABLE</a>.

Callers of <b>RtlGetElementGenericTable</b> must be running at IRQL &lt; DISPATCH_LEVEL if the caller-allocated memory for the generic table is pageable. 


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
Header

</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
Any level (See Remarks)

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.rtldeleteelementgenerictable">RtlDeleteElementGenericTable</a>
</dt>
<dt>
<a href="ifsk.rtlenumerategenerictablewithoutsplaying">RtlEnumerateGenericTableWithoutSplaying</a>
</dt>
<dt>
<a href="ifsk.rtlinitializegenerictable">RtlInitializeGenericTable</a>
</dt>
<dt>
<a href="ifsk.rtlinsertelementgenerictable">RtlInsertElementGenericTable</a>
</dt>
<dt>
<a href="ifsk.rtllookupelementgenerictable">RtlLookupElementGenericTable</a>
</dt>
<dt>
<a href="ifsk.rtlnumbergenerictableelements">RtlNumberGenericTableElements</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlGetElementGenericTable routine%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
