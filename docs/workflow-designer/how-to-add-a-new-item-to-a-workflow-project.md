---
title: 工作流程設計工具-如何： 將新的項目加入至工作流程專案
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0aa2be7fd8ecccbd8de0aa54c2693dd6b02c7e10
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>HOW TO：將新的項目加入至工作流程專案

建立工作流程專案之後，您可以將工作流程活動、 設計工具和其他熟悉的 Visual Studio 項目加入至您的專案。

下表列出您可以加入至工作流程專案的 Windows Workflow Foundation (WF) 項目。

|名稱|描述|
|----------|-----------------|
|活動|要由其他活動組成的活動。 選取這個項目是將相同的 XAML 檔案加入專案，當選取時，您會取得**活動程式庫**新的專案範本。 如需此程序的相關詳細資訊，請參閱[How to： 建立活動程式庫](../workflow-designer/how-to-create-an-activity-library.md)。|
|活動設計工具|可自訂活動之設計階段經驗的設計工具。 選取這個項目是將相同的檔案加入專案，當選取時，您會取得**活動設計工具程式庫**新的專案範本。 如需此程序的相關詳細資訊，請參閱[How to： 建立活動設計工具程式庫](../workflow-designer/how-to-create-an-activity-designer-library.md)。|
|程式碼活動|包含寫入至程式碼之執行邏輯的活動。 已為您產生包含 <xref:System.Activities.CodeActivity.Execute%2A> 方法之覆寫的原始程式碼檔。|
|WCF 工作流程服務|使用工作流程活動建置的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 服務。 選取這個項目是將相同的檔案加入專案，當選取時，您會取得**WCF 工作流程服務應用程式**新的專案範本。 如需有關這個程序的詳細資訊，請參閱[How to： 建立 WCF 工作流程服務應用程式](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md)。|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案

1.  在**專案**功能表上，按一下 **加入新項目...**.

     **加入新項目**對話方塊隨即開啟。

2.  在**已安裝的範本**窗格中，選取**工作流程**群組。

3.  選取四個項目的其中一個。 上表列出可用的選擇。

4.  輸入適當的名稱中的項目**名稱**方塊 對話方塊的底部。

5.  按一下**新增**將項目加入至目前的工作流程專案。

## <a name="see-also"></a>另請參閱

- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)