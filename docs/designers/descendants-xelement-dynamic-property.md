---
title: Descendants (XElement 動態屬性)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c1b0aa0c55c0da2a6f9af58f5d54ff607a409ce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (XElement 動態屬性)

取得用於擷取目前項目 (符合指定的擴充名稱) 之所有子代項目的索引子 (Indexer)。

## <a name="syntax"></a>語法

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

`IEnumerable<XElement> Item(String expandedName)` 型別的索引子。 這個索引子會採用指定之子代項目的擴充名稱，並傳回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中相符的子項目。

## <a name="remarks"></a>備註

這個屬性等同於 <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XContainer> 方法。

傳回集合中的項目順序為 XML 來源文件的順序。

這個屬性會使用延後執行。

## <a name="see-also"></a>另請參閱

- [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)
- [項目](../designers/elements-xelement-dynamic-property.md)