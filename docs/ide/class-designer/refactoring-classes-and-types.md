---
title: 重構類別和類型 (類別設計工具)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3104266e92bc05f82a4d97fb62fc20bc9e79c0eb
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="refactoring-classes-and-types-class-designer"></a>重構類別和類型 (類別設計工具)

當您重構程式碼時，可以變更其內部結構以及設計其物件的方式，而不是其外部行為，使其更容易了解、維護且更有效率。 使用類別設計工具和 [類別細節] 視窗可讓您在 Visual Studio 專案中重構 C# 、Visual Basic 或 C++ 程式碼時，減少必須執行的工作以及引入錯誤 (bug) 的機會。

> [!NOTE]
> 專案的檔案可能是唯讀的，因為專案是在原始程式碼控制之下且尚未簽出、參考的專案或是其檔案在磁碟上標示為唯讀。 當您在處於上述其中一種狀態的專案中工作時，依據專案的狀態，您會有各種儲存工作的方式可以使用。 這適用於重構程式碼，也適用於您以其他方式變更的程式碼，例如直接編輯。

## <a name="common-tasks"></a>一般工作

|工作|支援內容|
|----------|------------------------|
|**重構類別：** 您可以使用重構作業來將一個類別分割成部分類別，或是實作抽象基底類別。|-   [如何：將類別分割成部分類別](how-to-split-a-class-into-partial-classes.md)|
|**使用介面：** 在類別設計工具中，您可以將介面連接至替介面方法提供程式碼的類別，以在類別圖表上實作介面。|-   [如何：實作介面](how-to-implement-an-interface.md)|
|**重構類型、類型成員與參數：** 使用類別設計工具，即可重新命名類型、覆寫類型成員，或將其從某類型移至另一類型。 您也可以建立可為 Null 的類型。|-   [重新命名類型和類型成員](refactoring-classes-and-types.md#rename)<br />-   [將類型成員從一個類型移到另一個類型](refactoring-classes-and-types.md#move)<br />-   [如何：建立可為 Null 的類型](how-to-create-a-nullable-type.md)|

<a name="rename"></a>
### <a name="rename-types-and-type-members"></a>重新命名類型和類型成員

在類別設計工具中，您可以在類別圖表上或在 [屬性] 視窗中重新命名類型或類型的成員。 在 [類別細節] 視窗中，您可以變更成員的名稱，但不能變更類型的名稱。 重新命名類型或類型成員會傳播至舊名稱曾出現的所有視窗和程式碼位置。

#### <a name="to-rename-a-name-in-the-class-designer"></a>在類別設計工具中重新命名

1.  在類別圖上，選取類型或成員，然後按一下名稱。

     成員的名稱會變成可編輯。

2.  輸入類型或類型成員的新名稱

#### <a name="to-rename-a-name-in-the-class-details-window"></a>在 [類別細節] 視窗中重新命名

1.  若要顯示 [類別細節] 視窗，請用滑鼠右鍵按一下類型或類型成員，然後按一下 [類別細節] 。

     [類別細節] 視窗隨即出現。

2.  在 [名稱]  欄中，變更類型成員的名稱

3.  若要將焦點從儲存格移開，請按 **ENTER** 鍵，或是在儲存格以外的地方按一下。

    > [!NOTE]
    > 在 [類別細節] 視窗中，您可以變更成員的名稱，但不能變更類型的名稱。

#### <a name="to-rename-a-name-in-the-properties-window"></a>在 [屬性] 視窗中重新命名

1.  在類別圖表或 [類別細節] 視窗中，用滑鼠右鍵按一下類型或成員，然後按一下 [屬性] 。

     [屬性] 視窗隨即出現，並顯示類型或類型成員的屬性。

2.  在 [名稱]  屬性中，變更類型或類型成員的名稱。

     新的名稱會傳播至目前專案中曾出現舊名稱的所有視窗和程式碼位置。

<a name="move"></a>
### <a name="move-type-members-from-one-type-to-another"></a>將類型成員從一個類型移到另一個類型

您可以使用 [類別設計工具] ，將類型成員從一個類型移到另一個類型 (如果兩者都顯示在目前的類別圖表中)。

1.  在設計介面上顯示的類型中，用滑鼠右鍵按一下您要移動到另一個類型的成員，然後按一下 [剪下] 。

2.  用滑鼠右鍵按一下目的類型，然後按一下 [貼上] 。

     該屬性會從來源類型中移除，並出現在目的類型中。

## <a name="see-also"></a>另請參閱

- [檢視類型與關聯性](viewing-types-and-relationships.md)
- [設計類別和類型](designing-classes-and-types.md)