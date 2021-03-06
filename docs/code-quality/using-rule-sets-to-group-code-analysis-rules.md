---
title: 在 Visual Studio 中的程式碼分析規則集
ms.date: 04/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20e727fd331ebd98a74acbb63738e6921e5ad1a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>使用規則集分組程式碼分析規則

當您在 Visual Studio 中設定程式碼分析時，您可以從內建清單中選擇*規則集*。 規則集套用至專案，並是一群的程式碼分析規則，識別目標的問題以及該專案的特定條件。 比方說，您可以將套用的規則集是設計用來公開可用的 Api，掃描程式碼，或最小建議規則。 您也可以套用的規則集包含的所有規則。

您可以自訂規則集中加入或刪除規則，或變更規則的重要性顯示為警告或錯誤**錯誤清單**。 自訂的規則集可滿足特定的開發環境的需要。 當您自訂規則集時，規則集編輯器會提供搜尋和篩選工具，可協助您在程序中。

## <a name="rule-set-format"></a>規則集格式

中的 XML 格式中指定的規則集 *.ruleset*檔案。 包含識別碼的規則和*動作*，依分析器 ID 和檔案中的命名空間加以分組。

XML 內容 *.ruleset*檔案看起來類似這樣：

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> 更輕鬆地[編輯規則集](../code-quality/working-in-the-code-analysis-rule-set-editor.md)圖形**規則集編輯器**比以手動方式。

規則集的專案由指定`CodeAnalysisRuleSet`Visual Studio 專案檔中的屬性。 例如: 

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>另請參閱

- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)
