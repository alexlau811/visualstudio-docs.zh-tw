---
title: 部署 Office 方案
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58e485384f80b2f0fdfc46a91caf305754a87301
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-an-office-solution"></a>部署 Office 方案
  您可以使用 ClickOnce 或 Windows Installer 部署 Office 方案。 使用 ClickOnce 可減少部署和更新您的方案所需的步驟。 如果您使用 Windows Installer，就可以控制安裝方案的方式，以及使用者安裝您的方案時安裝程式顯示的頁面。  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
## <a name="deploy-a-solution-by-using-clickonce"></a>使用 ClickOnce 部署方案  
 當您使用 ClickOnce 部署方案時，會將方案發行至可供使用者安裝及執行的中央位置。 您可以更新方案，而不必將新的安裝程式散發給使用者。  這個部署選項比較簡單，不過，您無法對使用者顯示自訂設定頁面。 此外，方案必須在擁有多位使用者的所有電腦上安裝多次。 請參閱[使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## <a name="deploy-a-solution-by-using-windows-installer"></a>使用 Windows Installer 部署方案  
 當您使用 Windows Installer 部署方案時，會將安裝程式散發給使用者，而使用者會使用該程式安裝方案。 安裝程式可以同時為電腦的所有使用者安裝方案，而不只是目前使用者。 您還能夠透過在使用者安裝方案時顯示的選項掌控更多方面。 例如，您可以顯示授權合約或是讓使用者安裝方案的特定元件。 不過，如果您更新方案，就必須散發新的安裝程式。 請參閱[使用 Windows Installer 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。  
  
## <a name="see-also"></a>另請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [使用 Windows Installer 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [疑難排解 Office 方案部署](../vsto/troubleshooting-office-solution-deployment.md)  
  
  