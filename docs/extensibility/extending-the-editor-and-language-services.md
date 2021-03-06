---
title: 擴充編輯器和語言服務 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4113a033d4e1a2595f4a980405e1b39d57d60958
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-editor-and-language-services"></a>擴充編輯器和語言服務
您可以加入您自己的編輯器 （例如 IntelliSense) 的語言服務功能，並擴充 Visual Studio 程式碼編輯器的大部分功能。  您可以擴充的完整清單，請參閱[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)。  
  
 您可以使用 Managed Extensibility Framework (MEF)，以擴充大部分的編輯器功能。 例如，如果您想要擴充的編輯器功能的語法著色，您可以撰寫 MEF*元件組件*，定義您要的不同色彩及要如何處理它們的分類。 此編輯器也支援多個相同功能的延伸。  
  
 編輯器展示層以 Windows Presentation Framework (WPF)。 WPF 圖形文件庫提供彈性的文字格式，並提供視覺效果，例如圖形和動畫。  
  
 Visual Studio SDK 提供配接器稱為*填充碼*以支援較早版本所撰寫的 Vspackage。 不過，如果您有現有的 VSPackage，建議其更新為新的技術，以取得更佳的效能和可靠性。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[開始使用語言服務及編輯器擴充功能](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|說明如何建立編輯器 中的擴充功能。|  
|[深入探索編輯器](../extensibility/inside-the-editor.md)|描述編輯器的一般結構，並列出其某些特性。|  
|[編輯器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|說明如何使用編輯器 中的 Managed Extensibility Framework (MEF)。|  
|[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)|列出編輯器 中的擴充點。 擴充點代表可擴充的編輯器功能。|  
|[逐步解說︰建立檢視裝飾、命令和設定 (分欄輔助線)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|逐步解說，並說明建置可協助您保持程式碼的特定顯示寬度 gudie 繪製資料行檢視裝飾。  也會顯示讀取和寫入設定，以及宣告和實作，您可以從命令視窗叫用的命令。|  
|[編輯器匯入](../extensibility/editor-imports.md)|列出擴充功能可以匯入的服務。|  
|[改寫舊版程式碼編輯器](../extensibility/adapting-legacy-code-to-the-editor.md)|說明不同的方式來調整 (預先 Visual Studio 2010) 來擴充編輯器的舊版程式碼。|  
|[移轉舊版語言服務](../extensibility/internals/migrating-a-legacy-language-service.md)|說明如何移轉基礎的 VSPackage 語言服務。|  
|[逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|示範如何將內容類型連結至檔案的副檔名。|  
|[逐步解說：建立邊界字符](../extensibility/walkthrough-creating-a-margin-glyph.md)|示範如何將圖示新增邊界。|  
|[逐步解說︰反白顯示文字](../extensibility/walkthrough-highlighting-text.md)|示範如何使用*標記*來反白顯示文字。|  
|[逐步解說︰大綱](../extensibility/walkthrough-outlining.md)|示範如何加入針對特定種類的大括號大綱。|  
|[逐步解說︰顯示對稱的括號](../extensibility/walkthrough-displaying-matching-braces.md)|示範如何以反白顯示對稱的括號。|  
|[逐步解說︰顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|示範如何顯示描述項目，例如屬性、 方法和事件的程式碼的 QuickInfo 快顯。|  
|[逐步解說︰顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)|示範如何顯示快顯，讓簽章中參數的類型與數量的相關資訊。|  
|[逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)|示範如何實作陳述式完成。|  
|[逐步解說︰實作程式碼片段](../extensibility/walkthrough-implementing-code-snippets.md)|示範如何實作程式碼片段擴充。|  
|[逐步解說︰顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|示範如何顯示燈泡，如程式碼的建議。|  
|[逐步解說︰搭配編輯器擴充功能使用 Shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|示範如何將功能表命令，在 VSPackage 中的與 MEF 元件產生關聯。|  
|[逐步解說︰搭配編輯器擴充功能使用快速鍵](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|示範如何在 VSPackage 將功能表快速鍵關聯為 MEF 元件。|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|提供 Managed Extensibility Framework (MEF) 的相關資訊。|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|提供 Windows Presentation Foundation (WPF) 的相關資訊。|  
  
## <a name="reference"></a>參考資料  
 在 Visual Studio 編輯器包含下列命名空間。  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>