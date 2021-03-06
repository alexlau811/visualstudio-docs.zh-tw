---
title: 工作流程設計工具-如何： 建立活動設計工具程式庫
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d05ddb48e88627f4b7ab4112c164b5129ddba910
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-activity-designer-library"></a>HOW TO：建立活動設計工具程式庫
自訂活動設計工具可讓您建立標準或自訂活動的使用者介面。 您可以控制使用者介面的複雜性，並且能為活動建立多個設計工具。 這個案例可讓您建立專為多個對象量身訂做的設計工具。

## <a name="to-create-an-activity-designer-library"></a>若要建立活動設計工具程式庫

1.  啟動 Visual Studio 2010。

2.  上**檔案**功能表上，指向**新增**，然後選取**專案**開啟**新專案** 對話方塊。

3.  在**專案類型**窗格中，選取**工作流程**從其中**Visual C#** 或**Visual Basic**根據您慣用的群組語言。

4.  在**範本**窗格中，選取**活動設計工具程式庫**。

5.  在**名稱**方塊中，輸入您的專案讓您輕鬆識別的描述性名稱。

6.  在**位置**方塊中，輸入您要儲存您的專案，或按一下的目錄**瀏覽**來巡覽找到它。

7.  在**方案**方塊、 輸入的描述性名稱，您的方案，然後按一下 **確定**。

    > [!NOTE]
    > 如果您想要新增至現有的方案工作流程主控台應用程式，在 Visual Studio 2010 中開啟該方案，以滑鼠右鍵按一下方案中**方案總管 中**，然後選取**新增**，然後**新專案**開啟**新專案** 對話方塊。 依照本程序上面的說明繼續進行。

8.  專案範本是以 XAML 建立活動設計工具定義，以及使用原始程式碼建立程式碼後置實作檔案。 Windows 工作流程設計工具開啟，並顯示活動設計工具的畫布。

9. 拖放到 Windows Presentation Foundation (WPF) 控制項從**工具箱**至設計介面，以在您的自訂活動設計工具中使用它們。  如需如何實作自訂活動設計工具的範例，請參閱[How to： 建立自訂活動設計工具](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)。

    > [!WARNING]
    > 自訂活動設計工具可以用於自訂活動，也與預設.NET Framework 4activities。

## <a name="see-also"></a>另請參閱

- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)