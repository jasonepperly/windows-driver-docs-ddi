---
UID: NF:wiamdef.wiasCreatePropContext
title: wiasCreatePropContext function
author: windows-driver-content
description: The wiasCreatePropContext function allocates a property context to indicate which of an item's properties are being changed by the application.
old-location: image\wiascreatepropcontext.htm
old-project: image
ms.assetid: b820c19d-a12b-417b-a9a3-6a3d700009c0
ms.author: windowsdriverdev
ms.date: 1/17/2018
ms.keywords: wiasCreatePropContext
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wiamdef.h
req.include-header: Wiamdef.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Microsoft Windows Me and in Windows XP and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: wiasCreatePropContext
req.alt-loc: Wiaservc.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wiaservc.lib
req.dll: Wiaservc.dll
req.irql: 
req.typenames: *PDEVICEDIALOGDATA2, *LPDEVICEDIALOGDATA2, DEVICEDIALOGDATA2
req.product: Windows 10 or later.
---

# wiasCreatePropContext function



## -description
The <b>wiasCreatePropContext </b>function allocates a property context to indicate which of an item's properties are being changed by the application.



## -syntax

````
HRESULT _stdcall wiasCreatePropContext(
           ULONG                cPropSpec,
  _In_     PROPSPEC             *pPropSpec,
           ULONG                cProps,
  _In_opt_ PROPID               *pProps,
  _In_     WIA_PROPERTY_CONTEXT *pContext
);
````


## -parameters

### -param cPropSpec 

Specifies the total number of PROPSPEC structures in the <i>pPropSpec</i> array.


### -param pPropSpec [in]

Pointer to the first element of an array of PROPSPEC structures identifying which properties are changing.


### -param cProps 

Specifies the number of property identifiers stored in this context.


### -param pProps [in, optional]

Pointer to the first element of an array of property identifiers that indicate the properties to put into this property context.


### -param pContext [in]

Pointer to a <a href="..\wiamindr_lh\ns-wiamindr_lh-_wia_property_context.md">WIA_PROPERTY_CONTEXT</a> structure that contains a property context.


## -returns
On success, the function returns S_OK. If the function fails, it returns a standard COM error or one of the WIA_ERROR_XXX errors (described in the Microsoft Windows SDK documentation).


## -remarks
This function allocates a property context and fills in its values. This function is generally used in <a href="..\wiamdef\nf-wiamdef-wiasvalidateitemproperties.md">wiasValidateItemProperties</a> where the properties written by the application are validated.

Entries in the property context are identifiers for properties that either have dependents, or are themselves dependent on other properties. A context is used to mark which properties are being changed. When the property context is no longer needed, it should be freed by a call to <a href="..\wiamdef\nf-wiamdef-wiasfreepropcontext.md">wiasFreePropContext</a>.

The properties to which an application writes are specified by the <i>pPropSpec </i>array. The properties that were changed by the application, as well as any properties dependent on the changed properties, are specified by the <i>pProps</i> array. Only properties that have been changed by the application (and any dependent properties) can be specified in <i>pProps</i>. The PROPSPEC structure is defined in the Windows SDK documentation.

WIA_IPA_DATATYPE

WIA_IPA_DEPTH

WIA_IPS_XRES

WIA_IPS_XPOS

WIA_IPS_XEXTENT

WIA_IPA_PIXELS_PER_LINE

WIA_IPS_YRES

WIA_IPS_YPOS

WIA_IPS_YEXTENT

WIA_IPA_NUMBER_OF_LINES

WIA_IPS_CUR_INTENT

WIA_IPA_TYMED

WIA_IPA_FORMAT


## -see-also
<dl>
<dt>
<a href="..\wiamindr_lh\ns-wiamindr_lh-_wia_property_context.md">WIA_PROPERTY_CONTEXT</a>
</dt>
<dt>
<a href="..\wiamdef\nf-wiamdef-wiasvalidateitemproperties.md">wiasValidateItemProperties</a>
</dt>
<dt>
<a href="..\wiamdef\nf-wiamdef-wiasfreepropcontext.md">wiasFreePropContext</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [image\image]:%20wiasCreatePropContext function%20 RELEASE:%20(1/17/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>

