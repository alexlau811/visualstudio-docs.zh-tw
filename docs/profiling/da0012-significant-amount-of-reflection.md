---
title: DA0012：大量的反映 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd6f293633bb64b06f5374a21fbc9382d58b0bc0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012：大量的反射
|||  
|-|-|  
|規則 ID|DA0012|  
|分類|.NET Framework 使用方式|  
|分析方法|取樣|  
|訊息|您可能過度使用反映。 這是很消耗資源的作業。|  
|規則型別|警告|  
  
## <a name="cause"></a>原因  
 對 System.Reflection 方法 (例如 InvokeMember 和 GetMember) 或 Type 方法 (例如 MemberInvoke) 的呼叫大部分是分析資料。 可能的話，請考慮將這些方法取代為相依組件方法的早期繫結。  
  
## <a name="rule-description"></a>規則描述  
 反映是 .NET Framework 一個彈性的工具，可用來將應用程式晚期繫結到相依的執行階段組件，或者用來建立並在執行階段期間動態執行新型別。 不過，如果在緊密迴圈中經常使用或呼叫這些技術則會降低效能。  
  
 如需詳細資訊，請參閱 MSDN 上 Microsoft Patterns and Practices 文件庫中＜改進 .NET 應用程式效能和延展性＞(英文) 的＜第 5 章 - 改進 Managed 程式碼的效能＞(英文) 中的[反映和晚期繫結 (英文)](http://go.microsoft.com/fwlink/?LinkId=177826)一節。  
  
## <a name="how-to-investigate-a-warning"></a>如何調查警告  
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至分析資料的[函式詳細資料檢視](../profiling/function-details-view.md)。 檢查 System.Type 或 System.Reflection 方法的呼叫函式，找出最常使用 .NET Reflection API 的程式區段。 請避免使用會傳回中繼資料的方法。 當應用程式的效能很重要時，可能需要避免使用晚期繫結和避免在執行階段動態建立型別。