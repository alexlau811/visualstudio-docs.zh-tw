---
title: 如何：收集 Windows 事件追蹤 (ETW) 資料 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f75d16a252862d301ca1dcc85bd3ccd0696aff16
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>如何：收集 Windows 事件追蹤 (ETW) 資料

Windows 事件追蹤 (ETW) 是高效率的核心層級追蹤功能，可讓程式碼剖析工具記錄核心或應用程式定義的事件。 從事件提供者收集的資料，只能透過 /**Summary:ETW** option of the [VSPerfReport](../profiling/vsperfreport.md)命令列工具檢視。 您可使用此報告來判斷應用程式中發生效能問題的癥結。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="to-enable-event-trace-providers"></a>啟用事件追蹤提供者

1. 在 [效能總管] 中，以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性] 。

2. 在 [屬性頁] 中，按一下 [Windows 事件]  屬性。

3. 在 [選取要從中收集資料的事件追蹤提供者] 清單中，選取要用來對應用程式進行程式碼剖析的事件提供者。

## <a name="see-also"></a>另請參閱

[設定效能工作階段](../profiling/configuring-performance-sessions.md)