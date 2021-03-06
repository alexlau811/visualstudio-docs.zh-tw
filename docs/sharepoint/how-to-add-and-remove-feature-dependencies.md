---
title: 如何： 加入和移除功能相依性 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a65963c43c5a4facd8a3ca7c0f8ab1ed1988342f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767786"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>如何： 加入和移除功能相依性
  您的 SharePoint 功能仍取決於其他功能的功能或資料。 在這些情況下，您可以將這些其他功能做為相依性標示為您的功能。 如此一來，可確保在 SharePoint 伺服器之前您功能已啟用,，就會啟動相依的功能。  
  
## <a name="adding-dependencies"></a>加入相依性  
 您可以在方案中加入其他功能，做為相依性。 如此一來，您可以確定所需的功能會安裝並啟動您的功能安裝之前。  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>若要加入的相依性的方案中的功能
  
1.  開啟功能設計工具中，展開**功能啟用相依性** 節點，然後選擇 **新增** 按鈕。  
  
2.  在**新增的功能啟用相依性**對話方塊方塊中，選擇**方案中的功能上新增相依性**選項按鈕，選擇您想要新增為相依性的功能標題，然後選擇**新增** 按鈕。  
  
     您可以加入多個功能選擇多個項目時選擇**Ctrl**索引鍵。  
  
## <a name="adding-custom-dependencies"></a>新增自訂的依存性  
 您可以加入 SharePoint 伺服器上的已部署的功能，做為相依性。 如此一來，SharePoint 啟用程序會檢查並確定您的功能安裝之前，會啟動所有相依的功能。  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>若要新增的功能識別碼的相依性
  
1.  開啟功能設計工具中，展開**功能啟用相依性** 節點，然後選擇 **新增** 按鈕。  
  
2.  在**新增的功能啟用相依性**對話方塊方塊中，選擇**新增自訂相依性**選項按鈕。  
  
3.  在**功能識別碼**文字中，輸入您想要將標示為啟用相依性，然後選擇 [功能 GUID**新增**] 按鈕。  
  
## <a name="editing-custom-dependencies"></a>編輯自訂相依性  
 您可以編輯您先前加入的自訂相依性。 不過，相依的功能會在您的方案可以只會移除，無法編輯。  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>若要變更的相依性的方案中的功能
  
1.  開啟功能設計工具，接著展開**功能啟用相依性**節點。  
  
2.  選擇您想要編輯，然後選擇功能名稱**編輯** 按鈕。  
  
3.  在**編輯的自訂功能啟用相依性**對話方塊中，變更標題、 功能識別碼或描述，然後選擇**送出** 按鈕。  
  
## <a name="removing-dependencies"></a>移除相依性  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>若要在方案中移除功能相依性
  
1.  在功能設計工具中，依序展開**功能啟用相依性** 節點，選擇您想要移除，然後選擇功能名稱**移除** 按鈕。  
  
## <a name="see-also"></a>另請參閱
 [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何： 自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：新增與移除 SharePoint 功能中的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
