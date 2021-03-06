---
title: 遠端偵錯 IIS 與 Azure 上的 ASP.NET Core |Microsoft 文件
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: a4e03f9a369959a5736d7030a1dac885771d7984
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746763"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>在 Visual Studio 2017 在 Azure 中的 IIS 上的遠端偵錯 ASP.NET Core

本指南說明如何安裝和設定 Visual Studio 2017 ASP.NET Core 應用程式、 將它部署到 IIS 使用 Azure，並附加從 Visual Studio 遠端偵錯工具。

在 Azure 上的遠端偵錯的建議的方式取決於您的案例：

* 若要偵錯 ASP.NET Core Azure App Service 上，請參閱[使用快照集偵錯工具的偵錯 Azure 應用程式](../debugger/debug-live-azure-applications.md)。 這是建議的方法。
* 若要偵錯 ASP.NET Core 上使用較傳統的偵錯功能的 Azure 應用程式服務，請遵循本主題中的步驟 (請參閱節[遠端偵錯 Azure App Service 上](#remote_debug_azure_app_service))。

    在此案例中，您必須將您的應用程式從 Visual Studio Azure 部署，但您不需要手動安裝或設定 IIS 或遠端偵錯工具 （這些元件與虛線表示），如下圖所示。

    ![遠端偵錯工具元件](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* 若要偵錯在 Azure VM 上的 IIS，請遵循本主題中的步驟 (請參閱節[Azure VM 上的遠端偵錯](#remote_debug_azure_vm))。 這可讓您使用自訂的 IIS 設定，但更複雜的安裝和部署步驟。

    為 Azure VM，您必須將您的應用程式從 Visual Studio Azure 部署，您也需要手動安裝 IIS 角色和遠端偵錯工具，如下圖所示。

    ![遠端偵錯工具元件](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* 若要偵錯在 Azure Service Fabric ASP.NET Core 時，請參閱[遠端 Service Fabric 應用程式進行偵錯](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)。

> [!WARNING]
> 請務必刪除您已完成的步驟，在本教學課程時，您建立的 Azure 資源。 這樣一來，您可以避免產生不必要的費用。


### <a name="requirements"></a>需求

不支援透過 proxy 連線的兩部電腦之間的偵錯。 透過高延遲或低頻寬連線，例如撥號網際網路，或透過網際網路偵錯跨國家/地區不建議使用和可能會失敗或實在。 如需需求的完整清單，請參閱[需求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>在 Visual Studio 2017 電腦上建立 ASP.NET Core 應用程式 

1. 建立新的 ASP.NET Core 應用程式。 (選擇**檔案 > 新增 > 專案**，然後選取**Visual C# > 網路 > ASP.NET Core Web 應用程式**)。

    在**ASP.NET Core**範本區段中，選取**Web 應用程式**。

2. 請確定**ASP.NET Core 2.0**已選取，**啟用 Docker 支援**是**不**選取且**驗證**設為**不驗證**。

3. 將專案命名**MyASPApp**按一下 **[確定]** 來建立新的方案。

4. 開啟 About.cshtml.cs 檔案，並在設定的中斷點`OnGet`方法 (在較舊的範本，開啟 HomeController.cs 改為和設定中斷點`About()`方法)。

## <a name="remote_debug_azure_app_service"></a> Azure App Service 上的遠端偵錯 ASP.NET Core

從 Visual Studio 中，您可以快速發行及偵錯應用程式完整佈建的 IIS 執行個體。 不過，預先設定的 IIS 設定，而且您不能加以自訂。 如需詳細指示，請參閱[ASP.NET Core web 應用程式部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 (如果您需要自訂 IIS 的功能，請試著偵錯在[Azure VM](#BKMK_azure_vm)。) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>若要部署應用程式，然後使用 [伺服器總管] 的遠端偵錯

1. 在 Visual Studio 中，以滑鼠右鍵按一下專案節點，然後選擇 **發行**。

    如果您先前設定的任何發行設定檔，**發行** 窗格隨即出現。 按一下**新設定檔**。

1. 選擇**Azure App Service**從**發行**對話方塊中，選取**新建**，並遵循提示來發佈。

    如需詳細指示，請參閱[ASP.NET Core web 應用程式部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

    ![發佈至 Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 開啟**伺服器總管**(**檢視** > **伺服器總管**)，以滑鼠右鍵按一下應用程式服務執行個體，然後選擇 **附加偵錯工具**.

1. 在執行的 ASP.NET 應用程式，按一下連結以**有關**頁面。

    應該在 Visual Studio 中叫用中斷點。

    就這麼容易！ 本主題中步驟的其餘部分適用於 Azure VM 上的遠端偵錯。

## <a name="remote_debug_azure_vm"></a> Azure VM 上的遠端偵錯 ASP.NET Core

您可以建立伺服器的 Azure VM 的 Windows，再安裝及設定 IIS 和其他必要的軟體元件。 這會花費的時間比部署到 Azure 應用程式服務，並且需要您在本教學課程執行其餘的步驟。

首先，請依照下列所述的所有步驟[安裝和執行的 IIS](/azure/virtual-machines/windows/quick-create-portal)。

當您開啟通訊埠 80 的網路安全性群組中時，也請開啟連接埠 4022 遠端偵錯工具。 這樣一來，您不需要開啟它。

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Azure VM 上已執行於 IIS 應用程式嗎？

這篇文章包含基本的 Windows server 上的 IIS 組態設定及部署 Visual Studio 應用程式的步驟。 這些步驟是以確定伺服器已安裝的應用程式可以正常運作，並在您準備好要遠端偵錯的必要的元件。

* 如果您的應用程式執行於 IIS，而且您只想要下載遠端偵錯工具並啟動偵錯，請移至[下載並安裝 Windows Server 上的遠端工具](#BKMK_msvsmon)。

* 如果您想要取得說明，請確認您的應用程式已設定，部署，並在 IIS 中正確執行，以便您可以偵錯，請遵循本主題中的所有步驟。

### <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer （它預設會啟用） 啟用增強式安全性設定，您可能需要將某些網域新增為信任的網站，您可以下載某些網頁伺服器元件。 新增信任的網站，請前往**網際網路選項 > 安全性 > 受信任的網站 > 網站**。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，可能會收到要求授與權限來載入各種網站指令碼和資源。 其中一些資源並非必要，但若要簡化程序中，按一下**新增**出現提示時。

### <a name="install-aspnet-core-on-windows-server"></a>Windows 伺服器上安裝 ASP.NET Core

1. 安裝[.NET 核心 Windows Server 裝載](https://aka.ms/dotnetcore-2-windowshosting)主機系統上的套件組合。 組合將會安裝.NET 核心執行階段、.NET 核心程式庫和 ASP.NET 核心模組。 深入了解的詳細指示，請參閱[發行至 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

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

如果您要匯入發行設定，您可以略過本節。

1. 開啟 [Internet Information Services (IIS) 管理員]  並移至 [網站] 。

2. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

3. 設定**別名**欄位設為**MyASPApp**和應用程式集區欄位設**沒有 Managed 程式碼**。 設定**實體路徑**至**C:\Publish** （稍後部署目標的 ASP.NET 專案）。

4. 在 IIS 管理員中選取站台之後，選擇 **編輯權限**，並確定該 IUSR、 IIS_IUSRS 或設定為應用程式集區授權的使用者具有讀取和執行權限的使用者。

    如果您沒有看到其中一個使用者具有存取權，進行步驟來新增 IUSR 具有讀取和執行權限的使用者身分。

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>（選擇性）發佈和部署應用程式發行至本機資料夾從 Visual Studio

如果您不使用 Web Deploy，您必須發行和部署檔案系統或其他工具所使用的應用程式。 您可以開始使用檔案系統中，建立封裝，然後以手動方式部署封裝或使用 PowerShell、 RoboCopy 或 XCopy 等其他工具。 在本節中，我們假設如果您不使用 Web Deploy，您要以手動方式複製封裝。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> 下載並安裝 Windows Server 上的遠端工具

在此教學課程中，我們會使用 Visual Studio 2017。

如果您無法開啟遠端偵錯工具下載頁面，請參閱[解除封鎖檔案下載](../debugger/remote-debugging.md#unblock_msvsmon)的說明。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> 設定 Windows Server 上的遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要新增其他的使用者權限變更驗證模式或遠端偵錯工具連接埠號碼，請參閱[設定遠端偵錯工具](../debugger/remote-debugging.md#configure_msvsmon)。

### <a name="BKMK_attach"></a> 從 Visual Studio 電腦連接至 ASP.NET 應用程式

1. Visual Studio 電腦上，開啟您嘗試偵錯方案 (**MyASPApp**如果您要遵照這篇文章中的步驟)。
2. 在 Visual Studio 中，按一下 **偵錯 > 附加至處理序**（Ctrl + Alt + P）。

    > [!TIP]
    > 在 Visual Studio 2017，您可以重新連接至您先前附加至使用相同的程序**偵錯 > 重新附加至處理序...**(Shift + Alt + P)。 

3. [限定詞] 欄位設定為**\<遠端電腦名稱 >: 4022**。
4. 按一下**重新整理**。
    您應該會看到有些處理程序會出現在 [可使用的處理序]  視窗。

    如果您沒有看到任何處理程序，請嘗試使用的 IP 位址，而不 （連接埠是必要的） 遠端電腦名稱。 您可以使用`ipconfig`取得 IPv4 位址的命令列。

    如果您想要使用**尋找** 按鈕，您可能需要[開啟 UDP 連接埠 3702](#bkmk_openports)在伺服器上。

5. 核取 [顯示所有使用者的處理序]  。

6. 輸入以快速找出處理序名稱的第一個字母*dotnet.exe* （適用於 ASP.NET Core)。
   
   ASP.NET Core 應用程式中，先前的程序名稱是*dnx.exe*。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. 按一下 [附加] 。

8. 開啟遠端電腦的網站。 在瀏覽器，移至**http://\<遠端電腦名稱 >**。
    
    您應該會看到 ASP.NET 網頁。
9. 在執行的 ASP.NET 應用程式，按一下連結以**有關**頁面。

    應該在 Visual Studio 中叫用中斷點。

### <a name="bkmk_openports"></a> 疑難排解： 開啟 Windows Server 上的必要連接埠

大部分的安裝中安裝 ASP.NET 和遠端偵錯工具所開啟必要的連接埠。 不過，如果您正在疑難排解部署問題，而應用程式裝載在防火牆後面，您可能需要確認正確的通訊埠已開啟。

在 Azure VM 中，您必須開啟連接埠通過[網路安全性群組](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)。 

必要的連接埠：

- 80-所需的 IIS
- 4022-遠端偵錯所需從 Visual Studio 2017 (請參閱[遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)如需詳細資訊)。
- UDP 3702-（選擇性） 探索連接埠可以可讓您**尋找**按鈕時附加至 Visual Studio 中的遠端偵錯工具。

此外，應該已經開啟這些連接埠，由 ASP.NET 安裝：
- 8172-（選擇性） 所需的 Web Deploy 來部署應用程式，從 Visual Studio

