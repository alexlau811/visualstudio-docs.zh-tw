---
title: 使用 PyLint 對 Python 程式碼進行 Lint 檢查
description: 如何在 Visual Studio 中使用 PyLint 來檢查 Python 程式碼中的問題。
ms.date: 07/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 4e47de7be6587f0e8c967ba458a65906c80f2e5b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="using-pylint-to-check-python-code"></a>使用 PyLint 檢查 Python 程式碼

[PyLint](https://www.pylint.org/) 是一種廣泛使用的工具，可檢查 Python 程式碼中的錯誤，有助於撰寫良好的 Python 程式碼模式，因此 Visual Studio 已針對 Python 專案整合這項工具。

只要在 [方案總管] 中以滑鼠右鍵按一下 Python 專案，並選取 [Python] > [執行 PyLint]：

![操作功能表上 Python 專案的 PyLint 命令](media/code-pylint-command.png)

使用這個命令會提示您將 PyLint 安裝到使用中的環境，如果還沒有 PyLint 的話。

PyLint 警告和錯誤會出現在 [錯誤清單] 視窗中︰

![PyLint 錯誤清單](media/code-pylint-error-list.png)

按兩下錯誤會帶您直接前往產生問題的原始程式碼。

> [!Tip]
> 如需所有 PyLint 輸出訊息的詳細清單，請參閱 [PyLint 功能參考 (英文)](https://pylint.readthedocs.io/en/latest/technical_reference/features.html)。

## <a name="setting-pylint-command-line-options"></a>設定 PyLint 命令列選項

PyLint 文件的 [command-line options](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) (命令列選項) 一節描述如何透過 `.pylintrc` 設定檔控制 PyLint 的行為。 視您想要套用這些設定的範圍而定，這類檔案可以放在 Visual Studio Python 專案的根目錄或其他位置 (如需詳細資料，請參閱[命令列選項](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options))。

例如，若要在專案的 `.pylintrc` 檔案中隱藏上圖顯示的「遺失 docstring」警告，請執行下列步驟︰

1. 在命令列中，巡覽至您的專案根目錄 (其包含您的 `.pyproj` 檔案)，然後執行下列命令來產生已加註解的設定檔︰

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. 在 Visual Studio [方案總管] 中，以滑鼠右鍵按一下您的專案，選取 [加入] > [結束項目...]，瀏覽並選取新的 `.pylintrc` 檔案，然後選取 [加入]。

1. 開啟檔案進行編輯，它包含您可以使用的各種設定。 若要停用警告，請找出 `[MESSAGES CONTROL]` 區段，然後找出該區段的 `disable` 設定。 您會看到一長串的特定訊息，可以在其中附加您想要的任何警告。 在此範例中，請附加 `,missing-docstring` (包括其中的逗號)。

1. 儲存 `.pylintrc` 檔案，再次執行 PyLint，您會發現警告現在已經隱藏。

> [!Tip]
> 若要使用網路共用中的 `.pylintrc` 檔案，請利用使用 UNC 路徑或對應磁碟機代號之網路共用上的檔案名稱值來建立名為 `PYLINTRC` 的環境變數。 例如，`PYLINTRC=\\myshare\python\.pylintrc`。
