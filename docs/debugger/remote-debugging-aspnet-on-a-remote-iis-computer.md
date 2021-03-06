---
title: 遠端偵錯遠端 IIS 電腦上的 ASP.NET Core |Microsoft 文件
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 607f4bb2bcce3d8895a4a07df8d70c866e7a6aab
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746926"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>在 Visual Studio 2017 遠端 IIS 電腦上的遠端偵錯 ASP.NET Core
偵錯已部署至 IIS 的 ASP.NET 應用程式，安裝和部署您的應用程式的所在的電腦上執行遠端工具，然後附加至執行的應用程式從 Visual Studio。

![遠端偵錯工具元件](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

本指南說明如何安裝和設定 Visual Studio 2017 ASP.NET Core、 將它部署到 IIS，並附加從 Visual Studio 遠端偵錯工具。 若要遠端偵錯 ASP.NET 4.5.2，請參閱[IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 您也可以部署和使用 Azure 在 IIS 上偵錯。 Azure 應用程式服務，您可以輕鬆地部署和偵錯的 IIS 和遠端偵錯工具，並使用預先設定的執行個體上[快照偵錯工具](../debugger/debug-live-azure-applications.md)或[附加偵錯工具從 伺服器總管](../debugger/remote-debugging-azure.md)。

這些伺服器設定過這些程序：
* Windows Server 2012 R2 和 IIS 8
* Windows Server 2016 和 IIS 10

## <a name="requirements"></a>需求

不支援透過 proxy 連線的兩部電腦之間的偵錯。 透過高延遲或低頻寬連線，例如撥號網際網路，或透過網際網路偵錯跨國家/地區不建議使用和可能會失敗或實在。 如需需求的完整清單，請參閱[需求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="app-already-running-in-iis"></a>已在 IIS 中執行的應用程式嗎？

這篇文章包含基本的 Windows server 上的 IIS 組態設定及部署 Visual Studio 應用程式的步驟。 這些步驟是以確定伺服器具有必要安裝，應用程式可以正確地執行，而且您準備好要遠端偵錯元件。

* 如果您的應用程式執行於 IIS，而且您只想要下載遠端偵錯工具並啟動偵錯，請移至[下載並安裝 Windows Server 上的遠端工具](#BKMK_msvsmon)。

* 如果您想要取得說明，請確認您的應用程式已設定，部署，並在 IIS 中正確執行，以便您可以偵錯，請遵循本主題中的所有步驟。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>在 Visual Studio 2017 電腦上建立 ASP.NET Core 應用程式 

1. 建立新的 ASP.NET Core 應用程式。 (**檔案 > 新增 > 專案**，然後選取**Visual C# > 網路 > ASP.NET Core Web 應用程式**)。

    在**ASP.NET Core**範本區段中，選取**Web 應用程式**。

2. 請確定**ASP.NET Core 2.0**已選取，**啟用 Docker 支援**是**不**選取且**驗證**設為**不驗證**。

3. 將專案命名**MyASPApp**按一下 **[確定]** 來建立新的方案。

4. 開啟 About.cshtml.cs 檔案，並在設定的中斷點`OnGet`方法 (在較舊的範本，開啟 HomeController.cs 改為和設定中斷點`About()`方法)。

## <a name="bkmk_configureIIS"></a> 安裝及設定 Windows Server 上的 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer （它預設會啟用） 啟用增強式安全性設定，您可能需要將某些網域新增為信任的網站，您可以下載某些網頁伺服器元件。 新增信任的網站，請前往**網際網路選項 > 安全性 > 受信任的網站 > 網站**。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，可能會收到要求授與權限來載入各種網站指令碼和資源。 其中一些資源並非必要，但若要簡化程序中，按一下**新增**出現提示時。

## <a name="install-aspnet-core-on-windows-server"></a>Windows 伺服器上安裝 ASP.NET Core

1. 安裝[.NET 核心 Windows Server 裝載](https://aka.ms/dotnetcore-2-windowshosting)主機系統上的套件組合。 配套在安裝.NET 核心執行階段、.NET 核心程式庫和 ASP.NET 核心模組。 深入了解的詳細指示，請參閱[發行至 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

    > [!NOTE]
    > 如果系統沒有網際網路連線，取得並安裝 *[Microsoft Visual c + + 2015年可轉散發](https://www.microsoft.com/download/details.aspx?id=53840)* 之前安裝的.NET 核心 Windows Server 主控的組合。

3. 重新啟動系統 (或執行**net stop was /y**後面**net 啟動 w3svc**挑選變更到系統路徑的命令提示字元)。

## <a name="choose-a-deployment-option"></a>選擇 部署選項

如果您需要協助部署到 IIS 應用程式，請考慮這些選項：

* 部署在 IIS 中建立的發行設定檔並匯入 Visual Studio 中的設定。 在某些情況下，這是一個快速方式來部署您的應用程式。 當您建立的發行設定檔案時，權限會自動設定 IIS 中。

* 部署發行至本機資料夾，並且將輸出的慣用方法複製到 IIS 上的已備妥應用程式資料夾。

## <a name="optional-deploy-using-a-publish-settings-file"></a>（選擇性）使用發行設定檔部署

您可以使用這個選項建立的發行設定檔，並匯入 Visual Studio。

> [!NOTE]
> 這種部署方法會使用 Web Deploy。 如果您想要設定 Web Deploy 以手動方式在 Visual Studio 中而非匯入設定，您可以安裝而不是 Web 部署 3.6 Web 部署 3.6 主控伺服器。 不過，如果您設定 Web Deploy 以手動方式，您必須確定應用程式資料夾的伺服器上已設定正確的值和權限 (請參閱[設定 ASP.NET 網站](#BKMK_deploy_asp_net))。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>安裝及設定 Web Deploy 來裝載 Windows Server 上的伺服器

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立的發行設定檔案

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>匯入 Visual Studio 中的發行設定和部署

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功後，它應該會自動啟動。 如果從 Visual Studio 應用程式未啟動，請在 IIS 中啟動應用程式。 您需要確定應用程式集區欄位的 ASP.NET Core **DefaultAppPool**設**沒有 Managed 程式碼**。

1. 在**設定**對話方塊中，按一下 偵錯啟用**下一步**，選擇**偵錯**組態，然後選擇 **移除其他檔案，在目的地**下**檔案發行**選項。

    > [!NOTE]
    > 如果您選擇發行組態，則停用偵錯*web.config*檔案，當您發行時。

1. 按一下**儲存**然後重新發行應用程式。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>（選擇性）部署發行至本機資料夾

您可以使用此選項來部署應用程式，如果您想要將應用程式複製到 IIS 使用 Powershell、 RoboCopy，或您想要手動複製這些檔案。

### <a name="BKMK_deploy_asp_net"></a> 設定 Windows Server 電腦上的 ASP.NET 網站

1. 開啟 Windows 檔案總管，並建立新的資料夾， **C:\Publish**將稍後部署 ASP.NET 專案。

2. 如果它尚未開啟，開啟**網際網路資訊服務 (IIS) 管理員**。 (在伺服器管理員 的左窗格中選取**IIS**。 以滑鼠右鍵按一下伺服器，然後選取**網際網路資訊服務 (IIS) 管理員**。)

3. 在下**連線**在左窗格中，移至**網站**。

4. 選取**Default Web Site**，選擇**基本設定**，並設定**實體路徑**至**C:\Publish**。

4. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

5. 設定**別名**欄位設為**MyASPApp**，接受預設的應用程式集區 (**DefaultAppPool**)，並設定**實體路徑**至**C:\Publish**。

6. 在下**連線**，選取**應用程式集區**。 開啟**DefaultAppPool**並將應用程式集區欄位設定為**沒有 Managed 程式碼**。

7. 以滑鼠右鍵按一下新的網站在 IIS 管理員中，選擇 **編輯權限**，並確定該 IUSR、 IIS_IUSRS 或設定 web 應用程式存取權是以讀取和執行權限的授權的使用者的使用者。

    如果您沒有看到其中一個使用者具有存取權，進行步驟來新增 IUSR 具有讀取和執行權限的使用者身分。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>發佈和部署應用程式發行至本機資料夾從 Visual Studio

您可以發佈和部署應用程式使用的檔案系統或其他工具。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> 下載並安裝 Windows Server 上的遠端工具

在此教學課程中，我們會使用 Visual Studio 2017。

如果您無法開啟遠端偵錯工具下載頁面，請參閱[解除封鎖檔案下載](../debugger/remote-debugging.md#unblock_msvsmon)的說明。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 在某些情況下，它可以是最有效率的檔案共用從執行遠端偵錯工具。 如需詳細資訊，請參閱[從檔案共用執行遠端偵錯工具](../debugger/remote-debugging.md#fileshare_msvsmon)。
  
## <a name="BKMK_setup"></a> 設定 Windows Server 上的遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要新增其他的使用者權限變更驗證模式或遠端偵錯工具連接埠號碼，請參閱[設定遠端偵錯工具](../debugger/remote-debugging.md#configure_msvsmon)。

如需以服務方式執行遠端偵錯資訊，請參閱[以服務方式執行遠端偵錯工具](../debugger/remote-debugging.md#bkmk_configureService)。

## <a name="BKMK_attach"></a> 從 Visual Studio 電腦連接至 ASP.NET 應用程式

1. Visual Studio 電腦上，開啟您嘗試偵錯方案 (**MyASPApp**遵循這篇文章中的所有步驟)。
2. 在 Visual Studio 中，按一下 **偵錯 > 附加至處理序**（Ctrl + Alt + P）。

    > [!TIP]
    > 您可以在 Visual Studio 2017，重新附加您先前附加至使用相同的程序**偵錯 > 重新附加至處理序...**（shift + Alt + P）。 

3. [限定詞] 欄位設定為**\<遠端電腦名稱 >: 4022**。
4. 按一下**重新整理**。
    您應該會看到有些處理程序會出現在 [可使用的處理序]  視窗。

    如果您沒有看到任何處理程序，請嘗試使用的 IP 位址，而不 （連接埠是必要的） 遠端電腦名稱。 您可以使用`ipconfig`取得 IPv4 位址的命令列。

    如果您想要使用**尋找** 按鈕，您可能需要[開啟 UDP 連接埠 3702](#bkmk_openports)在伺服器上。

5. 核取 [顯示所有使用者的處理序]  。
6. 輸入以快速找出處理序名稱的第一個字母**dotnet.exe** （適用於 ASP.NET Core)。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. 按一下 [附加] 。

8. 開啟遠端電腦的網站。 在瀏覽器，移至**http://\<遠端電腦名稱 >**。
    
    您應該會看到 ASP.NET 網頁。

9. 在執行的 ASP.NET 應用程式，按一下連結以**有關**頁面。

    應該在 Visual Studio 中叫用中斷點。

## <a name="bkmk_openports"></a> 疑難排解： 開啟 Windows Server 上的必要連接埠

大部分的安裝中安裝 ASP.NET 和遠端偵錯工具所開啟必要的連接埠。 不過，您可能需要確認連接埠已開啟。

> [!NOTE]
> 在 Azure VM 中，您必須開啟連接埠通過[網路安全性群組](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)。 

必要的連接埠：

- 80-所需的 IIS
- 4022-遠端偵錯所需從 Visual Studio 2017 (請參閱[遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)如需詳細資訊。
- 8172-（選擇性） 所需的 Web Deploy 來部署應用程式，從 Visual Studio。
- UDP 3702-（選擇性） 探索連接埠可以可讓您**尋找**按鈕時附加至 Visual Studio 中的遠端偵錯工具。

1. 若要開啟 Windows Server 上的連接埠，請開啟**啟動**功能表中，搜尋**具有進階安全性的 Windows 防火牆**。

2. 然後選擇 **輸入規則 > 新的規則 > 通訊埠**，然後按一下 **下一步**。 (如 UDP 3702 選擇**輸出規則**改用。)

3. 在下**特定本機連接埠**，輸入連接埠號碼，按一下**下一步**。

4. 按一下**允許連線**，按一下 **下一步**。

5. 選取一或多個網路類型，以啟用連接埠並按一下**下一步**。

    您選取的類型必須包括遠端電腦連線的網路。
6. 新增名稱 (例如， **IIS**， **Web Deploy**，或**msvsmon**) 的 輸入規則，然後按一下**完成**。

    您應該會看到您在 [輸入規則] 或 [輸出規則] 清單中的新規則。

    如果您想需設定 Windows 防火牆的詳細資訊，請參閱[設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 建立其他必要的連接埠的其他規則。
