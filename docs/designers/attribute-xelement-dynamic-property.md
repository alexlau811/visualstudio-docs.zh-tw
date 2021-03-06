---
title: Attribute (XElement 動態屬性)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ac173785804ce2ed2874b9628c68d3ab78be6e1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (XElement 動態屬性)

取得用於擷取對應於指定擴充名稱之屬性執行個體的索引子 (Indexer)。

## <a name="syntax"></a>語法

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

`XAttribute Item(String expandedName)` 型別的索引子。 如果沒有具有指定之名稱的屬性，這個索引子會採用指定之屬性的擴充名稱，並傳回對應的 <xref:System.Xml.Linq.XAttribute> 或 `null`。

## <a name="remarks"></a>備註

這個屬性等同於 <xref:System.Xml.Linq.XElement.Attribute%2A> 類別的 <xref:System.Xml.Linq.XElement?displayProperty=fullName> 方法。

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)
- [值](../designers/value-xattribute-dynamic-property.md)