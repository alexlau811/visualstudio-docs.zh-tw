---
title: 工作流程設計工具-如何： 使用工作流程設計工具偵測 XAML
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: eac6294861080614cbdd46e6ac1cc9a05d7124ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>HOW TO：使用工作流程設計工具偵測 XAML

工作流程是根據 XAML 所定義的。 工作流程的 UI 呈現方式，乃是建立在定義該工作流程的 XAML 樹狀上。 偵錯經驗很類似偵錯 Windows 工作流程設計工具中的工作流程。 比方說，XAML 偵錯，時 [區域變數]、 [監看式] 和 [執行緒] 視窗的運作方式相同偵錯工作流程設計工具中所顯示的一樣。 此外，在 XAML 偵錯期間的呼叫堆疊檢視，也是工作流程執行流程的逐行階層架構檢視。

> [!NOTE]
> 如果為工作流程的 XAML 與活動位於同一個組件中，則不會包含類別名稱中的組件部分。 沒有類別 (活動) 名稱的這個部分，就不能在執行階段載入 XAML。 不建議在與主要專案的同一個命名空間中定義活動，否則，XAML 在設計工具中編輯之後必須手動編輯。

## <a name="to-debug-workflow-xaml"></a>若要進行工作流程 XAML 偵錯

1.  Visual Studio 中開啟的工作流程或活動專案。

2.  活動或您想要偵錯中所述的活動上設定中斷點[How to： 在工作流程中設定的中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)。

3.  以滑鼠右鍵按一下包含您的工作流程定義和選取的.xaml 檔案**檢視程式碼**。 在設計檢視中設定中斷點的活動之後，您會看到該活動 XAML 項目宣告的同一行上顯示中斷點。

4.  叫用偵錯工具中所述[How to： 叫用工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)。

5.  當程式碼執行到您的其中一個中斷點時，該中斷點關聯的 XAML 項目會出現醒目顯示。 若要移動到下一個中斷點，請使用**F10**或**F11**索引鍵。

## <a name="see-also"></a>另請參閱

- [如何：在工作流程中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [如何：叫用工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)