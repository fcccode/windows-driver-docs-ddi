---
UID: NF.ntifs.RtlGetSaclSecurityDescriptor
title: RtlGetSaclSecurityDescriptor function
author: windows-driver-content
description: The RtlGetSaclSecurityDescriptor routine returns a pointer to the system ACL (SACL) for a security descriptor.
old-location: ifsk\rtlgetsaclsecuritydescriptor.htm
old-project: ifsk
ms.assetid: 5dd4b15a-63e1-4b80-a156-bc44aeeafb0e
ms.author: windowsdriverdev
ms.date: 11/30/2017
ms.keywords: RtlGetSaclSecurityDescriptor
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Microsoft Windows Server 2003 SP1 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlGetSaclSecurityDescriptor
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
req.irql: <= APC_LEVEL
---

# RtlGetSaclSecurityDescriptor function



## -description
The <b>RtlGetSaclSecurityDescriptor</b> routine returns a pointer to the system ACL (SACL) for a security descriptor.



## -syntax

````
NTSTATUS RtlGetSaclSecurityDescriptor(
  _In_  PSECURITY_DESCRIPTOR SecurityDescriptor,
  _Out_ PBOOLEAN             SaclPresent,
  _Out_ PACL                 *Sacl,
  _Out_ PBOOLEAN             SaclDefaulted
);
````


## -parameters

### -param SecurityDescriptor [in]

Pointer to the <a href="kernel.security_descriptor">SECURITY_DESCRIPTOR</a> whose SACL is to be returned.


### -param SaclPresent [out]

Pointer to a Boolean variable that indicates the presence of a SACL in the specified security descriptor. If this variable receives <b>TRUE</b>, the security descriptor contains a SACL, and the remaining output parameters receive valid values. If this variable receives <b>FALSE</b>, the security descriptor does not contain a SACL, and the remaining output parameters do not receive valid values.


### -param Sacl [out]

Pointer to a variable that receives the address of the SACL for the security descriptor. If the security descriptor does not have a SACL, this variable does not receive a value. If the security descriptor has a <b>NULL</b> SACL, this variable receives <b>NULL</b>. 


### -param SaclDefaulted [out]

Pointer to a Boolean variable that receives the value of the SE_SACL_DEFAULTED flag in the security descriptor's SECURITY_DESCRIPTOR_CONTROL structure if a SACL exists for the security descriptor. 


## -returns
<b>RtlGetSaclSecurityDescriptor</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value such as the following:
<dl>
<dt><b>STATUS_UNKNOWN_REVISION</b></dt>
</dl>The security descriptor's revision level is unknown or is not supported. This is an error code.

 


## -remarks
For more information about security and access control, see the documentation for these topics in the Microsoft Windows SDK. 


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
This routine is available on Microsoft Windows Server 2003 SP1 and later.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h)</dt>
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
&lt;= APC_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.acl">ACL</a>
</dt>
<dt>
<a href="kernel.rtlcreatesecuritydescriptor">RtlCreateSecurityDescriptor</a>
</dt>
<dt>
<a href="ifsk.rtlgetdaclsecuritydescriptor">RtlGetDaclSecurityDescriptor</a>
</dt>
<dt>
<a href="kernel.rtllengthsecuritydescriptor">RtlLengthSecurityDescriptor</a>
</dt>
<dt>
<a href="kernel.rtlsetdaclsecuritydescriptor">RtlSetDaclSecurityDescriptor</a>
</dt>
<dt>
<a href="kernel.rtlvalidsecuritydescriptor">RtlValidSecurityDescriptor</a>
</dt>
<dt>
<a href="ifsk.security_descriptor">SECURITY_DESCRIPTOR</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlGetSaclSecurityDescriptor routine%20 RELEASE:%20(11/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
