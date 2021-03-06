---
title: 字串視覺化檢視 中檢視字串 |Microsoft 文件
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3a0575b02422bf83dd560d3eae5724b0a50d3f3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>在 Visual Studio 中的字串視覺化檢視中檢視字串
您所偵錯時，您可以開啟檢視字串太長，無法在資料提示或偵錯工具視窗中檢視之字串視覺化檢視。 在許多案例中，視覺化檢視可以協助您識別格式不正確的字串。

標準的內建字串視覺化檢視包含純文字、 XML、 HTML 和 JSON。 幾個其他類型設定，例如偵錯工具中顯示 WPF 物件類似 windows**自動變數**視窗中，您也可以開啟視覺化檢視。

## <a name="open-a-string-visualizer"></a>開啟字串視覺化檢視

若要檢視的純文字、 XML、 HTML 或 JSON 字串，請按一下放大鏡圖示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")游標變數，其中包含字串值。 您必須先暫停偵錯工具若要查看的放大鏡圖示。

![開啟字串視覺化檢視](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>檢視字串資料

**運算式**字串視覺化檢視 中的欄位會顯示目前的變數或運算式停留在上偵錯工具。

**值**欄位顯示的字串值。 文字視覺化檢視會顯示純文字。

空白**值**指出特定的視覺化檢視無法辨識字串類型。 例如，XML 視覺化檢視會顯示空白**值**適用於簡單的文字字串 （使用任何 XML 標記） 或 JSON 格式化字串。 如果您要在視覺化檢視中檢視無法辨識的字串，請使用文字視覺化檢視。

### <a name="view-json-string-data"></a>檢視 JSON 字串資料

格式正確的 JSON 字串看起來如下圖所 JSON 視覺化檢視中。 JSON 格式不正確可能會顯示錯誤圖示 （或如果無法辨識的空白）。

![JSON 字串視覺化檢視](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 字串視覺化檢視")

### <a name="view-xml-string-data"></a>檢視 XML 字串資料

格式正確的 XML 字串看起來像下圖中 XML 視覺化檢視。 XML 格式不正確可能會顯示不含 XML 標記 （或如果無法辨識的空白）。

![XML 字串視覺化檢視](../debugger/media/dbg-string-visualizers-xml.png "XML 字串視覺化檢視")

### <a name="view-html-string-data"></a>檢視 HTML 字串資料

格式正確的 HTML 字串會出現類似的檢視，您會看到是否轉譯字串的瀏覽器，如圖所示。 格式不正確的 HTML 可能會顯示為純文字。

![HTML 字串視覺化檢視](../debugger/media/dbg-string-visualizers-html.png "HTML 字串視覺化檢視")

## <a name="see-also"></a>另請參閱  
 [建立自訂視覺化檢視 （C#、 Visual Basic）](../debugger/create-custom-visualizers-of-data.md)