---
title: PF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 523140a4ffdc8e1eae07e3ae7dcffee5709067a2
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
---
# <a name="pf"></a>PF
VSPerfCmd.exe 的 **PF** 選項會將取樣的分析事件設定為分頁錯誤，並且選擇性地變更取樣間隔的分頁錯誤數目，預設值為 10。  
  
> [!NOTE]
>  **PF** 不能在 64 位元系統上使用。  
  
**PF** 只能用於也包含 [啟動] 或 [連結] 選項的命令列。  
  
 預設會將取樣事件設定為未暫止處理器時脈週期，並將取樣間隔設定為 10,000,000。 [計時器]、[PF]、[Sys] 和 [計數器] 選項可讓您設定取樣事件和取樣間隔。 **GC** 選項會在每個配置和記憶體回收事件發生時，收集 .NET 記憶體資料。 您只能在命令列上指定上述其中一個選項。  
  
 取樣事件和取樣間隔只能在包含 [啟動] 或 [附加] 選項的第一個命令列中設定。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>參數  
 `Events`  
 指定取樣間隔中分頁錯誤事件數目的整數值。 如果未指定 `Events`，間隔會設定為 10。  
  
## <a name="required-options"></a>必要選項  
 **PF** 只能在包含下列其中一個選項的命令列上指定。  
  
 **Launch：** `AppName`  
 啟動分析工具及 AppName 指定的應用程式。  
  
 **Attach:** `PID`  
 將分析工具附加至 AppName 指定的處理序。  
  
## <a name="invalid-options"></a>無效的選項  
 下列選項無法在與 **PF** 相同的命令列上指定。  
  
 **Timer**[**:**`Cycles`]  
 將取樣事件設定為處理器時脈週期，並且選擇性地將取樣間隔設定為 `Cycles`。 預設的計時器間隔為 10,000,000。  
  
 **Sys**[**:**`Events`]  
 將取樣事件設定為從已分析應用程式呼叫作業系統核心 (syscalls)，並選擇性地將取樣間隔設定為 `Events`。 預設的 Sys 間隔為 10。  
  
 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]  
 將取樣事件設定為 `Name` 所指定的 CPU 效能計數器，並將取樣間隔設定為 `Reload`。  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 收集 .NET 記憶體資料。 根據預設 (**配置**)，系統會在每個記憶體配置事件發生時收集資料。 指定 **Lifetime** 參數時，也會在每個記憶體回收事件發生時收集資料。  
  
## <a name="example"></a>範例  
 此範例示範如何將分析取樣事件設定為分頁錯誤，並將取樣間隔設定為 20 個分頁錯誤。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)