---
title: CA2227：集合屬性應該為唯讀
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: aa1d8644049f78eccfda7402360bdbc930b61601
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227：集合屬性應該為唯讀

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|分類|Microsoft.Usage|
|中斷變更|中斷|

## <a name="cause"></a>原因

外部可見的可寫入的屬性是型別可實作<xref:System.Collections.ICollection?displayProperty=fullName>。 陣列、 索引子 （屬性名稱為 'Item'） 和權限集合，則會忽略這個規則。

## <a name="rule-description"></a>規則描述

可寫入的集合屬性允許使用者以完全不同的集合取代該集合。 唯讀屬性會停止從取代過程，集合，但是仍然允許設定個別成員。 如果目標是取代集合，慣用的設計模式是包含方法，從集合移除的所有項目和重新擴展集合的方法。 請參閱<xref:System.Collections.ArrayList.Clear%2A>和<xref:System.Collections.ArrayList.AddRange%2A>方法<xref:System.Collections.ArrayList?displayProperty=fullName>類別，如需此模式的範例。

二進位與 XML 序列化支援是集合的唯讀屬性。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>類別有特定實作的型別需求<xref:System.Collections.ICollection>和<xref:System.Collections.IEnumerable?displayProperty=fullName>才能序列化。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將屬性設為唯讀。 如果設計需要的話，將方法加入至清除並重新填入集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例會示範具有可寫入的集合屬性的型別，並且說明如何直接取代集合。 此外，取代唯讀集合的屬性使用的慣用的方式`Clear`和`AddRange`方法會顯示。

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>相關的規則

[CA1819：屬性不應該傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)