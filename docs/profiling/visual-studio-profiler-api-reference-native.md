---
title: Visual Studio 分析工具 API 參考 (原生) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 53c8caa101b51a9d26d555787e710408cf315a0e
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="visual-studio-profiler-api-reference-native"></a>Visual Studio 分析工具 API 參考 (原生)
Visual Studio 分析工具 API 可讓您以程式設計方式控制收集的資料量，並在分析期間插入時間戳記和設定檔標記。 若要使用原生 API，您可以在您的專案中包含 VSPerf.h 標頭檔，並加入 VSPerf.lib。  
  
> [!NOTE]
>  根據預設，VSPerf.h 和 VSPerf.lib 位於名為 PerfSDK 的資料夾中。 例如，位於 \<磁碟機>:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\PerfSDK 目錄中。  
  
## <a name="in-this-section"></a>本節內容  
 [CommentMarkAtProfile](../profiling/commentmarkatprofile.md)  
  
 [CommentMarkProfile](../profiling/commentmarkprofile.md)  
  
 [MarkProfile](../profiling/markprofile.md)  
  
 [NameProfile](../profiling/nameprofile.md)  
  
 [ResumeProfile](../profiling/resumeprofile.md)  
  
 [StartProfile](../profiling/startprofile.md)  
  
 [StopProfile](../profiling/stopprofile.md)  
  
 [SuspendProfile](../profiling/suspendprofile.md)  
  
 [PROFILE_CURRENTID](../profiling/profile-currentid.md)  
  
## <a name="see-also"></a>另請參閱  
 [分析工具 API](../profiling/profiling-tools-apis.md)   
 [逐步解說：使用分析工具 API](../profiling/walkthrough-using-profiler-apis.md)
