---
title: 專案設計工具，參考頁 (Visual Basic)
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35534c0c6965dd7f7db01e2299ff71572b8de9e7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="references-page-project-designer-visual-basic"></a>專案設計工具，參考頁 (Visual Basic)
使用 [專案設計工具] 的 [參考] 頁面來管理專案中的參考、Web 參考，以及匯入的命名空間。 專案可以包含 COM 元件、XML Web 服務、.NET Framework 類別庫/組件或其他類別庫的參考。 如需使用參考的詳細資訊，請參閱[管理專案中的參考](../../ide/managing-references-in-a-project.md)。

 若要存取 [參考] 頁面，請在方案總管中選擇專案節點 (而不是 [方案] 節點)。 然後選擇功能表列上的 [專案]、[屬性]。 [專案設計工具] 出現時，請按一下 [參考] 索引標籤。

## <a name="uielement-list"></a>UIElement 清單
 下列選項可讓您選取或移除專案中的參考和匯入的命名空間。

 **未使用的參考**

 按一下此按鈕可存取 [未使用的參考] 對話方塊。

 [未使用的參考] 對話方塊可讓您移除專案中包含、但程式碼並未實際使用的參考。 此對話方塊包含格線，其中會列出專案中未使用之命名空間的 [參考名稱]、[路徑]，以及其他資訊。 在格線中，選取您想要從專案移除的命名空間參考，然後按一下 [移除]。

 **參考路徑**

 按一下此按鈕可存取 [參考路徑] 對話方塊。

> [!NOTE]
> 當專案系統找到組件參考時，系統會尋找下列位置以便解析參考，順序如下：

>
>  1.  專案資料夾。 當 [顯示所有檔案] 沒有作用時，方案總管即會顯示專案資料夾檔案。
> 2.  [參考路徑] 對話方塊中所指定的資料夾。
> 3.  [新增參考] 對話方塊中所示檔案的資料夾。
> 4.  專案的 obj 資料夾 (當您將 COM 參考新增至專案時，可能會將一或多個組件新增至專案的 obj 資料夾)。

 **參考**

 這份清單會顯示專案中的所有參考 (不論使用或未使用)。

 **[新增]**

 按一下此按鈕，即可將參考或 Web 參考新增至 [參考] 清單。

 選擇 [參考]，即可使用 [新增參考] 對話方塊，將參考新增至專案。

 選擇 [Web 參考]，即可使用 [新增 Web 參考] 對話方塊，將 Web 參考新增至專案。

 **移除**

 選取 [參考] 清單中的一或多個參考，然後按一下這個按鈕即可刪除。

 **更新 Web 參考**

 選取 [參考] 清單中的 Web 參考，然後按一下這個按鈕即可更新。

 **匯入的命名空間**

 您可以在此方塊中輸入自己的命名空間，然後按一下 [新增使用者匯入]，將其新增至匯入的命名空間清單。

 您可以為使用者匯入的命名空間建立別名。 若要執行此工作，請以「別名」=*命名空間*的格式輸入別名和命名空間。 如果您使用長的命名空間，例如 `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`，這就非常實用。

 **新增使用者匯入**

 按一下此按鈕，可將 [匯入的命名空間] 方塊中指定的命名空間新增至匯入的命名空間清單。 只有當指定的命名空間尚未在清單中時，此按鈕才有作用。

 **命名空間清單**

 此清單會顯示所有可用的命名空間。 您專案中所含命名空間的核取方塊會是選取狀態。

 **更新使用者匯入**

 在命名空間清單中，選取使用者指定的命名空間，並在 [匯入的命名空間] 方塊中，輸入您想要取代的新名稱，然後按一下這個按鈕，即可將其變更為新的命名空間。 只有當指定的命名空間是您使用 [新增使用者匯入] 按鈕新增至清單時，此按鈕才有作用。 您可以新增下列項目：

-   類別或命名空間，例如 <xref:System.Math?displayProperty=fullName>。

-   別名匯入，例如 `VB=Microsoft.VisualBasic`。

-   XML 命名空間，例如 `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`。

## <a name="see-also"></a>請參閱

- [管理專案中的參考](../../ide/managing-references-in-a-project.md)
- [如何：新增或移除匯入的命名空間 (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports 陳述式 (XML 命名空間)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
