---
title: 模組檢視 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb86cc9809bcb620033820b8c422313305d95d53
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="modules-view"></a>模組檢視
模組檢視會列出分析資料的模組。 每個模組都是階層式樹狀結構的根節點。 模組的已分析函式列在模組節點之下。 如果使用取樣方法收集分析資料，則行資訊會列在函式節點下，而指令指標資料則列在行節點下。  
  
 請展開或摺疊模組名稱來顯示或關閉模組效能資料的檢視。  
  
 若要新增或移除資料行，請以滑鼠右鍵按一下報表視窗，然後選取 [新增/移除資料行]。 您可以按一下資料行名稱來排序資料。 如需詳細資訊，請參閱[如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)。  
  
 [模組] 檢視中可用的資料行取決於用來收集資料的分析方法 (取樣或檢測)，以及是否在分析回合中收集 .NET 記憶體資料。  
  
## <a name="see-also"></a>請參閱  
 [模組檢視](../profiling/modules-view-sampling-data.md)   
 [模組檢視](../profiling/modules-view-instrumentation-data.md)   
 [模組檢視 - 檢測](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [模組檢視 - 取樣](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [模組檢視](../profiling/modules-view-contention-data.md)