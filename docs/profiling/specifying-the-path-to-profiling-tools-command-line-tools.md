---
title: 指定分析工具命令列工具的路徑 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e25d5052cbc70e4a45040f8ebadb8cb36daa053
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>指定程式碼剖析工具命令列工具的路徑
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼分析工具命令列工具的路徑不會加入 PATH 環境變數中。 在 32 位元電腦上，這些工具會在一個目錄中。 在 64 位元電腦上，程式碼分析工具有 32 位元和 64 位元兩種版本。  
  
## <a name="32-bit-computers"></a>32 位元電腦  
 在 32 位元電腦上，預設的分析工具目錄是*磁碟機*\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools。  
  
## <a name="64-bit-computers"></a>64 位元電腦  
 在 64 位元電腦上，則會根據已進行程式碼剖析之應用程式的目標平台指定路徑。  
  
-   若是 32 位元應用程式，預設程式碼剖析工具目錄是：  
  
     *磁碟機*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   若是 64 位元應用程式，預設程式碼剖析工具目錄是：  
  
     *磁碟機*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64