---
title: 在 Visual Studio 的專案和項目範本中新增名稱參數
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 26802b7b5293fd43eb1546290560c5300c360003
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-substitute-parameters-in-a-template"></a>如何：替代範本中的參數

從範本建立檔案時，範本參數可讓您取代類別名稱和命名空間等識別碼。 您可以將範本參數新增至現有的範本，或使用範本參數建立您自己的範本。

以格式 $<參數>$ 撰寫範本參數。 如需完整的範本參數清單，請參閱[範本參數](../ide/template-parameters.md)。

下節示範如何修改範本，以「安全的專案名稱」取代命名空間的名稱。

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>使用參數取代命名空間名稱

1. 在範本的一或多個程式碼檔案中，插入參數。 例如: 

    ```csharp
    namespace $safeprojectname$
    ```

1. 在範本的 *vstemplate* 檔案中，找出包含此檔案的 `ProjectItem` 元素。

1. 將 `ProjectItem` 項目的 `ReplaceParameters` 屬性設定為 `true`：

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>另請參閱

- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [範本參數](../ide/template-parameters.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem 項目 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)