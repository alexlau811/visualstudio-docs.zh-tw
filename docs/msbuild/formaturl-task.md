---
title: FormatUrl 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 353dd60697d1e77adced612dee79cea97e4c7ba8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="formaturl-task"></a>FormatUrl 工作
將 URL 轉換為正確的 URL 格式。  
  
## <a name="parameters"></a>參數  
 下表說明 `FormatUrl` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`InputUrl`|選擇性的 `String` 參數。<br /><br /> 指定要格式化的 URL。|  
|`OutputUrl`|選擇性的 `String` 輸出參數。<br /><br /> 指定已格式化 URL。|  
  
## <a name="remarks"></a>備註  
 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)