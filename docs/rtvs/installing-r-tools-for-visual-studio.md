---
title: 安裝 R 工具
description: 如何在 Visual Studio 2017 和 Visual Studio 2015 中，包括離線安裝。
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 26f0618397ef1ccfdd23983afdde28eccb59ef29
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>如何安裝 Visual Studio R 工具

本文內容：

- [支援的 Visual Studio 版本](#supported-versions-of-visual-studio)
- [在 Visual Studio 2017 中安裝 RTVS](#installing-rtvs-in-visual-studio-2017)
- [在 Visual Studio 2015 中安裝 RTVS](#installing-rtvs-in-visual-studio-2015)
- [離線安裝](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> 安裝 R 工具之後，您可能需要如[選項](options-for-r-tools-in-visual-studio.md)主題所述，設定 Visual Studio 以取得最佳化資料科學家版面配置。

## <a name="supported-versions-of-visual-studio"></a>支援的 Visual Studio 版本

在 Windows 上，Community (免費)、Professional 和 Enterprise 版本的 [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 和 [Visual Studio 2015 Update 3 (或更高版本)](http://go.microsoft.com/fwlink/?LinkId=691129) (直接下載) 支援 Visual Studio R 工具 (RTVS)。

Visual Studio for Mac 目前不支援 RTVS。

如果您只有產品隨附的 Visual Studio Shell (例如 Visual Studio Test Professional 和 SQL Server Management Studio)，將不會安裝 RTVS。 Visual Studio Shell 缺少 RTVS 的必要元件。

## <a name="installing-rtvs-in-visual-studio-2017"></a>在 Visual Studio 2017 中安裝 RTVS

1. 執行 Visual Studio 安裝程式，並選取 [修改] 選項 (如需詳細資料，請參閱[修改 Visual Studio](../install/modify-visual-studio.md))。 如果您還沒有安裝 Visual Studio，請參閱[安裝 Visual Studio](../install/install-visual-studio.md)。 在 Windows 7 上，請確定您的安裝程式已更新為顯示 Visual Studio 2017 15.2 版、組建 26430.12 或更新版本。

1. 選取 [資料科學與分析應用程式] 工作負載：

    ![VS2017 中的資料科學與分析應用程式工作負載](media/installation-data-science-workload.png)

1. 在相同的工作負載名稱下方，於右側設定任何其他選項。 這個工作負載預設會包括 F# 和 Python 支援。 針對 R，最低需求是 [R 語言支援]、[R 開發工具的執行階段支援] 和 [Microsoft R Client]。

RTVS 會安裝到：`%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`，其中 `<version>` 一般是 `2017`，而 `<edition>` 是 `Community`、`Professional` 或 `Enterprise`。

## <a name="installing-rtvs-in-visual-studio-2015"></a>在 Visual Studio 2015 中安裝 RTVS

使用 Visual Studio 2015，您需要個別安裝 R 解譯器和 R 工具。

### <a name="install-an-r-interpreter"></a>安裝 R 解譯器

RTVS 需要下列一或多個來源中 R 版本 3.2.1 或更高版本的 64 位元安裝︰

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open 和 CRAN R 都允許多個並行版本。 不過，Microsoft R Client 僅支援一個版本，並且一律會使用您已安裝的最新版本。

### <a name="install-the-r-tools"></a>安裝 R 工具

從 [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current) 下載目前 RTVS for Visual Studio 2015。 RTVS 會檢查適合的 Visual Studio 版本，並協助您安裝 R 解譯器 (若尚未安裝)。

> [!Note]
> 獨立 RTVS 安裝程式只能與 Visual Studio 2015 搭配運作；與 Visual Studio 2017 搭配運作時，透過如前所述的[資料科學與分析應用程式工作負載](#installing-rtvs-in-visual-studio-2017)來安裝 R 支援。

RTVS for Visual Studio 2015 會安裝在：`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Visual Studio and RTVS 的離線安裝

離線安裝適用於未連線到網際網路的電腦︰

1. 遵循指示來建立 Visual Studio 版本的離線安裝程式：

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. 如果是 Visual Studio 2015，請從 [https://aka.ms/rtvs-current-zip ](https://aka.ms/rtvs-current-zip) 和 [https://aka.ms/rtvs-remote-zip ](https://aka.ms/rtvs-remote-zip)下載離線 RTVS 安裝程式。

1. 從離線安裝程式安裝 Visual Studio 和 RTVS。

## <a name="see-also"></a>另請參閱

- [開始使用 R](getting-started-with-r.md)
- [R 工具範例專案](getting-started-samples.md)
- [取得協助](getting-started-help.md)
- [選項設定](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (先前稱為 R Server)](/machine-learning-server/)