---
title: 開發舊版語言服務 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cf384a22429c6314bf5e2fcbb66db7974d42c87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="developing-a-legacy-language-service"></a>開發舊版語言服務
這個區段會連結至主題可協助您建立舊版語言服務。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱[編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="in-this-section"></a>本節內容  
 [舊版語言服務模型](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 提供的最小的語言服務模型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心編輯器。 您可以使用這個模型做為指南，來建立您自己的語言服務。  
  
 [舊版語言服務介面](../../extensibility/internals/legacy-language-service-interfaces.md)  
 討論實作語言服務所需的物件，並提供可用來提供語法反白顯示、 方法的資料和其他功能的其他物件的清單。  
  
 [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 描述如何將語言服務才能攔截命令文字 檢視會處理的插入命令篩選器。  
  
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 提供有關如何使用註冊語言服務資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [語言服務支援偵錯](../../extensibility/internals/language-service-support-for-debugging.md)  
 描述如何語言服務可以提供功能來支援偵錯工具。  
  
 [檢查清單︰建立舊版語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 提供逐步指示，可建立和整合核心編輯器的語言服務。  
  
## <a name="related-sections"></a>相關章節  
 [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 討論如何實作語言服務中反白顯示語法。  
  
 [舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 討論陳述式完成時，語言服務用來協助完成語言關鍵字或項目，在開始輸入使用者的程序。  
  
 [在舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 描述如何提供多載函式和方法的方法提示。  
  
 [如何︰在舊版語言服務中提供隱藏文字的支援](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 說明隱藏的文字區域的目的，並提供指引來說明如何實作隱藏的文字區域。  
  
 [如何︰在舊版語言服務中提供展開大綱的支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 說明擴充您的語言支援的大綱支援的兩個選項*摺疊至定義*命令。