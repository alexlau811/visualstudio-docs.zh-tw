---
title: 快速監看式命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce3c95591809b847141dde07b2a770d9b4597a5f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="quick-watch-command"></a>快速監看式命令
可顯示[快速監看式](../../debugger/watch-and-quickwatch-windows.md)視窗的 [運算式] 欄位中所選取或指定的文字。 您可以使用此對話方塊來計算偵錯工具辨識的變數或運算式目前的值，或暫存器的內容。 此外，您可以變更任何非 const 變數的值或任何暫存器的內容。

## <a name="syntax"></a>語法

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>引數
 `text`

 選擇性。 要新增至 [快速監看式] 對話方塊的文字。

## <a name="remarks"></a>備註
 如果省略 `text`，則會將游標處目前選取的文字或字組新增至監看式視窗。

## <a name="example"></a>範例

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>請參閱

- [在 Visual Studio 中使用監看式及快速監看式視窗在變數設定監看式](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)