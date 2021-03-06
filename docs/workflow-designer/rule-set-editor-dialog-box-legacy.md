---
title: 工作流程設計工具中的規則集編輯器對話方塊 （舊版）
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77bb10e5237b33c60b0cd309c2d3c6c634182bc6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="rule-set-editor-dialog-box-legacy"></a>規則集編輯器對話方塊 (舊版)

本主題描述如何使用**規則集編輯器**在舊版的 Windows 工作流程設計工具 對話方塊。 當您需要以.NET Framework 3.5 版或 WinFX 為目標時，請使用舊版工作流程設計工具。

**規則集編輯器**對話方塊用來建立和修改[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)規則集可序列化為.rules 檔案。

> [!NOTE]
> 如果您想要開啟.rules 檔案**含編碼的 XML 編輯器**，您必須先關閉工作流程或活動相關聯的設計工具視窗。

如需有關如何存取資訊**規則集編輯器**對話方塊中，請參閱[How to： 建立 PolicyActivity 規則集 （舊版）](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)。

> [!WARNING]
> 舊版工作流程設計工具，用於以.NET Framework 3.5 版或 WinFX 目標的規則編輯器不支援多目標。

下表描述的使用者介面 (UI) 項目**規則集編輯器** 對話方塊。

|UI 項目|描述|
|----------------|-----------------|
|**新增規則**|將新的規則定義新增至規則集。|
|**刪除**|將選取的規則從規則集內刪除。|
|**鏈結**|指定規則集要使用哪種類型的向前鏈結。 可用的選項如下：<br /><br /> -   **完整鏈結**，其中指定要使用所有正向鏈結的機制： 隱含的方法屬性設定，並明確使用**更新**函式。<br />-   **循序**，指定不使用任何向前鏈結。<br />-   **僅明確更新**，指定只有上執行向前鏈結**更新**動作。<br /><br /> 如需向前鏈結的詳細資訊，請參閱[使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004)。|
|**名稱**|規則集清單資料行標題。 按一下會按照名稱排序規則清單。|
|**優先順序**|規則集清單資料行標題。 按一下會按照優先權排序規則清單。|
|**重新評估**|規則集清單資料行標題。 按一下會按照重新評估類型排序規則清單。|
|**規則預覽**|規則集清單資料行標題。 按一下會按照規則的條件和動作預覽排序規則清單。|
|**名稱：**|輸入規則名稱。|
|**優先順序：**|輸入規則的優先權。 預設優先權為 0。|
|**重新評估：**|指定規則要使用哪一種規則重新評估。 可用的選項如下：<br /><br /> -   **一律**，因而導致要視需要重新評估規則。<br />-   **永遠不會**，讓規則永不重新評估。 在此狀況下，規則只執行一次。|
|**使用中**|核取可讓規則成為作用中。|
|**條件：**|輸入規則條件的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**Then 動作：**|輸入 Then 動作的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**Else 動作：**|輸入 Else 動作的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**[確定]**|按一下將規則集儲存為 .rules 檔案。|

 如需規則集的詳細資訊，請參閱[使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004)。

## <a name="entering-condition-and-action-expressions"></a>輸入條件和動作運算式
 輸入條件和 Then 運算式，並在其各自的文字，以文字的動作中的方塊，否則**規則集編輯器** 對話方塊。 您可以輸入**這。** 若要參考欄位、 屬性和方法的工作流程中使用編輯器中，使用 IntelliSense 型的功能表。 或者您可以直接輸入工作流程成員名稱。 您可以輸入類別名稱，後面加上方法名稱，來呼叫參考型別上的靜態方法。

 您可以將邏輯運算子新增至條件中，如 AND、OR 和 NOT。 您也可以新增述詞 (Predicate)。 述詞是二元 (Binary) 運算子和兩個運算元。 支援的二元運算子有 = =、 >、 \<，> = 和 < =。 支援的運算元有常數值、算術函式和有範圍的 Public 成員。

 您可以指定的類型比較，而且您可以比較與**null**或空字串。 您可以對包含複雜型別之變數上的成員進行巢狀呼叫，例如，`this.Address.State == "WA"`。

 運算式支援以下運算子：

-   關係運算子：==、=、!=

-   比較運算子： <， \<=、 >、 > =

-   算術運算子：+、-、*、/、MOD

-   邏輯運算子:，& &、 OR、 &#124; &#124;、 NOT、 ！

-   位元運算子： &、&#124;

 運算式運算子的優先順序是按照 C# 運算子優先順序規則。

 如需條件的詳細資訊，請參閱[在工作流程中使用條件](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77)。

### <a name="halt-and-update-functions"></a>暫止和更新函式
 **Then 動作：**和**Else 動作：**運算式支援**暫止**和**更新**函式。 若要使用**暫止**函式中，輸入**暫止**到**Then 動作：**或**Else 動作：**文字方塊。 **暫止**動作會造成規則集立即停止執行，並且控制項會傳回至呼叫的程式碼。 您使用**更新**函式與向前鏈結。

 **更新**陳述式可以在編輯器中有兩種形式表示，則下列範例會示範這兩種形式：

```
Update(this.Address.State)
Update("this/Address/State")
```

 如需有關使用**更新**與向前鏈結，請參閱[使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004)。

## <a name="see-also"></a>另請參閱

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [選取規則集對話方塊 (舊版)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004)
- [在工作流程中使用條件](http://go.microsoft.com/fwlink?LinkID=65009)