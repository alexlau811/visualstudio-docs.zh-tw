---
title: 設定目前處理序
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64561db59cc089d9539ab396cf4e869e92fe1117
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="set-current-process"></a>設定目前處理序
將指定的處理序設為偵錯工具中的使用中處理序。

## <a name="syntax"></a>語法

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>引數
 `index`

 必要。 處理序的索引。

## <a name="remarks"></a>備註
 進行偵錯時，您可以附加至多個處理序，但是無論在任何時間，偵錯工具一次只能有一個使用中處理序。 您可以使用 `SetCurrentProcess` 命令設定使用中處理序。

## <a name="example"></a>範例

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)