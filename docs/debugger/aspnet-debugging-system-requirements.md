---
title: ASP.NET 偵錯： 系統需求 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a0d591c9f68e5331b2047ee749fff148c8844937
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET 偵錯：系統需求
本主題描述 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 偵錯情節的軟體和安全性需求：  
  
-   本機偵錯： [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 Web 應用程式會在同一部電腦上執行。 這個情節有兩種版本：  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程序碼位於檔案系統上。  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程序碼位於 IIS 網站中。  
  
-   遠端偵錯： [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在用戶端電腦上執行，並對遠端伺服器電腦上執行的 Web 應用程式進行偵錯。  
  
## <a name="security-requirements"></a>安全性需求  
 若要進行遠端偵錯，本機和遠端電腦都必須在網域設定或工作群組設定中。  
  
 若要偵錯[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]工作者處理序 （裝載應用程式集區），您必須偵錯該處理序的權限。 根據預設，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]前 IIS 6.0 的應用程式執行身分**ASPNET**使用者。 在 IIS 6.0 和 IIS 7.0、 **NETWORK SERVICE**帳戶是預設值。 如果背景工作處理序是以 **ASPNET**或 **NETWORK SERVICE**身分執行，則您必須具有 Administrator 權限才能對它進行偵錯。

 > [!IMPORTANT]
 > 從 Windows Server 2008 R2 開始，我們建議使用[ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities)做為每個應用程式集區身分識別。
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序的名稱會隨偵錯情節和 IIS 的版本而有所不同。 如需詳細資訊，請參閱[如何：尋找 ASP.NET 處理序的名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)。  
  
 您可以編輯執行 IIS 的伺服器上的 machine.config 檔案，變更 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序執行的使用者帳戶。 若要執行這項操作，最好是使用 [Internet Information Services (IIS) 管理員] 。 如需詳細資訊，請參閱[如何： 執行背景工作處理序在使用者帳戶](../debugger/how-to-run-the-worker-process-under-a-user-account.md)。  
  
 如果您將 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序變更為以您自己的使用者帳戶執行，您就不需要是執行 IIS 之伺服器上的系統管理員。  
  
> [!CAUTION]
>  在您將 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序變更為以不同帳戶執行之前，請考慮以該帳戶執行 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序時，處理序遭到竊取的後果。 ASPNET 和 NETWORK SERVICE 使用者帳戶會以最低權限執行，因此可降低處理序遭竊取時可能造成的損害。 如果您必須將 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序變更為以具有較高權限的帳戶執行，可能造成的損害也會較大。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 ASP.NET 應用程式](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [如何：在使用者帳戶下執行背景工作處理序](../debugger/how-to-run-the-worker-process-under-a-user-account.md)