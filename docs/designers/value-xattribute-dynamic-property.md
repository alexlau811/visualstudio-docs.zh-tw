---
title: Value (XAttribute 動態屬性)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19808b10c64b469d3d9191fa2e4fc282d7696c5f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="value-xattribute-dynamic-property"></a>Value (XAttribute 動態屬性)

取得或設定 XML 屬性的值。

## <a name="syntax"></a>語法

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

包含此屬性之值的 <xref:System.String>。

## <a name="exceptions"></a>例外狀況

|例外狀況類型|條件|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|設定時，`value` 為 `null`。|

## <a name="remarks"></a>備註

此屬性相當於 <xref:System.Xml.Linq.XAttribute.Value%2A> 類別的 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> 屬性，但此動態屬性也支援變更通知。

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [XAttribute 類別動態屬性](../designers/xattribute-class-dynamic-properties.md)
- [屬性](../designers/attribute-xelement-dynamic-property.md)