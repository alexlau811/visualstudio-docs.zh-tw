---
title: 逐步解說： 建立自訂動作專案項目包含項目範本，第 1 部分 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 02f3311b96d8f1287f2c2f2a81f9b37e51d4f7f6
ms.sourcegitcommit: cc88ccc6aacebe497899fab05d243a65053e194c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1"></a>逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分
  您可以藉由建立您自己的專案項目類型擴充 Visual Studio 中的 SharePoint 專案系統。 在本逐步解說，您將建立可加入至 SharePoint 專案，在 SharePoint 網站上建立的自訂動作專案項目。 自訂動作會將功能表項目**網站動作**功能表的 SharePoint 網站。  
  
 本逐步解說將示範下列工作：  
  
-   建立 Visual Studio 擴充功能，可定義新類型的自訂動作的 SharePoint 專案項目。 新的專案項目類型會實作自訂的數種功能：  
  
    -   做為起點的專案項目，例如 Visual Studio 中顯示自訂動作的設計工具相關的其他工作的捷徑功能表。  
  
    -   開發人員變更專案項目和包含它之專案的某些屬性時會執行的程式碼。  
  
    -   中的專案項目旁邊會出現自訂圖示**方案總管 中**。  
  
-   建立 Visual Studio 項目範本專案項目。  
  
-   建立 Visual Studio 擴充功能 (VSIX) 封裝來部署專案項目範本和延伸模組組件。  
  
-   偵錯和測試專案項目。  
  
 這是獨立的逐步解說。 完成此逐步解說之後，您可以將項目範本的精靈增強專案項目。 如需詳細資訊，請參閱[逐步解說： 建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
> [!NOTE]  
>  您可以下載範例，以從[Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) ，示範如何建立自訂活動，以便在工作流程。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說在開發電腦上：  
  
-   支援的 Microsoft Windows、 SharePoint 和 Visual Studio 版本。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說使用**VSIX 專案**SDK，以建立 VSIX 封裝，來部署專案項目中的範本。 如需詳細資訊，請參閱[擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念是有幫助，但並非必要，完成此逐步解說：  
  
-   在 SharePoint 中的自訂動作。 如需詳細資訊，請參閱[自訂動作](http://go.microsoft.com/fwlink/?LinkId=177800)。  
  
-   在 Visual Studio 中的項目範本。 如需詳細資訊，請參閱[建立專案和項目範本](/visualstudio/ide/creating-project-and-item-templates)。  
  
## <a name="creating-the-projects"></a>建立專案  
 若要完成此逐步解說，您需要建立三個專案：  
  
-   VSIX 專案。 此專案會建立 VSIX 封裝來部署 SharePoint 專案項目。  
  
-   專案的項目範本。 此專案會建立可將 SharePoint 專案項目新增至 SharePoint 專案項目範本。  
  
-   類別庫專案。 這個專案會實作定義行為的 SharePoint 專案項目 Visual Studio 擴充功能。  
  
 開始本逐步解說建立的專案。  
  
#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
3.  在清單頂端的**新專案**對話方塊方塊中，請確定 **.NET Framework 4.5**已選取。  
  
4.  在**新專案**對話方塊方塊中，展開  **Visual C#** 或**Visual Basic**節點，然後選擇 **擴充性**節點。  
  
    > [!NOTE]  
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。  
  
5.  選擇**VSIX 專案**範本。  
  
6.  在**名稱**方塊中，輸入**CustomActionProjectItem**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**CustomActionProjectItem**專案加入**方案總管 中**。  
  
#### <a name="to-create-the-item-template-project"></a>若要建立專案項目範本  
  
1.  在**方案總管] 中**，開啟 [解決方案] 節點的捷徑功能表，選擇**新增**，然後選擇 [**新專案**。  
  
2.  在清單頂端的**新專案**對話方塊方塊中，請確定 **.NET Framework 4.5**已選取。  
  
3.  在**新專案**對話方塊方塊中，展開  **Visual C#** 或**Visual Basic**節點，然後選擇 **擴充性**節點。  
  
4.  在專案範本清單中選擇**C# 項目範本**或**Visual Basic 項目範本**範本。  
  
5.  在**名稱**方塊中，輸入**ItemTemplate**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**ItemTemplate**專案加入方案。  
  
#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案  
  
1.  在**方案總管] 中**，開啟 [解決方案] 節點的捷徑功能表，選擇**新增**，然後選擇 [**新專案**。  
  
2.  在清單頂端的**新專案**對話方塊方塊中，請確定 **.NET Framework 4.5**已選取。  
  
3.  在**新專案**對話方塊方塊中，展開  **Visual C#** 或**Visual Basic**節點，並選擇**Windows**  節點，然後選擇  **類別庫**專案範本。  
  
4.  在**名稱**方塊中，輸入**ProjectItemDefinition**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**ProjectItemDefinition**專案加入方案，並開啟預設 Class1 的程式碼檔。  
  
5.  從專案刪除 Class1 的程式碼檔案。  
  
## <a name="configuring-the-extension-project"></a>設定擴充功能專案  
 撰寫程式碼以定義 SharePoint 專案項目類型之前，您必須將程式碼檔案和擴充功能專案中的組件參考加入。  
  
#### <a name="to-configure-the-project"></a>若要設定專案  
  
1.  在**方案總管] 中**，開啟捷徑功能表**ProjectItemDefinition**專案，選擇**新增**，然後選擇 [**新項目**。  
  
2.  在專案項目清單中，選擇 **程式碼檔案**。  
  
3.  在**名稱**方塊中，輸入名稱**CustomAction**與適當的檔案名稱副檔名，然後選擇 [**新增**] 按鈕。  
  
4.  在**方案總管 中**，開啟捷徑功能表**ProjectItemDefinition**專案，然後再選擇**加入參考**。  
  
5.  在**參考管理員-ProjectItemDefinition**對話方塊方塊中，選擇**組件**] 節點，然後選擇 [ **Framework**節點。  
  
6.  選取下列組件的每個核取方塊：  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  選擇**延伸** 節點，選取 Microsoft.VisualStudio.Sharepoint 組件旁邊的核取方塊，然後選擇**確定** 按鈕。  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>定義新的 SharePoint 專案項目類型  
 建立類別，實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>介面來定義新的專案項目類型的行為。 每當您想要定義新的專案項目類型時，請實作這個介面。  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>若要定義新的 SharePoint 專案項目類型  
  
1.  在 ProjectItemDefinition 專案中，開啟 CustomAction 程式碼檔案。  
  
2.  這個檔案中的程式碼取代為下列程式碼。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="creating-an-icon-for-the-project-item-in-solution-explorer"></a>正在建立 「 方案總管 中的專案項目圖示  
 當您建立自訂 SharePoint 專案項目時，您可以將影像 （圖示或點陣圖） 與專案項目。 中的專案項目旁邊會出現此影像**方案總管 中**。  
  
 在下列程序中，您可以建立專案項目圖示和延伸模組組件中內嵌的圖示。 這個圖示由參考<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>的`CustomActionProjectItemTypeProvider`您稍早建立的類別。  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>若要建立自訂專案項目圖示  
  
1.  在**方案總管] 中**，開啟捷徑功能表**ProjectItemDefinition**專案，選擇**新增**，然後選擇 [**新項目...**.  
  
2.  在專案項目清單中，選擇 **圖示檔**項目。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，您必須選擇**一般**節點以顯示**圖示檔**項目。  
  
3.  在**名稱**方塊中，輸入**CustomAction_SolutionExplorer.ico**，然後選擇 [**新增**] 按鈕。  
  
     在中，開啟 [新增] 圖示**影像編輯器**。  
  
4.  編輯 16 x 16 版本的圖示檔，使其具有設計，您可以辨識，並再儲存 圖示檔。  
  
5.  在**方案總管 中**，選擇**CustomAction_SolutionExplorer.ico**。  
  
6.  在**屬性**視窗中，選擇箭號旁**建置動作**屬性。  
  
7.  在出現的清單，選擇 **內嵌資源**。  
  
## <a name="checkpoint"></a>檢查點  
 此時在逐步解說中，所有的程式碼專案項目現在是在專案中。 建置專案，以確認編譯無誤。  
  
#### <a name="to-build-your-project"></a>建置您的專案  
  
1.  開啟快顯功能表**ProjectItemDefinition**專案，選擇**建置**。  
  
## <a name="creating-a-visual-studio-item-template"></a>建立 Visual Studio 項目範本  
 若要啟用其他開發人員使用您的專案項目，您必須建立專案範本或項目範本。 開發人員使用 Visual Studio 中這些範本，建立新的專案，或將項目加入至現有的專案建立您的專案項目執行個體。 這個逐步解說中，使用 ItemTemplate 專案來設定您的專案項目。  
  
#### <a name="to-create-the-item-template"></a>若要建立項目範本  
  
1.  從 ItemTemplate 專案刪除 Class1 的程式碼檔案。  
  
2.  在 ItemTemplate 專案中，開啟 ItemTemplate.vstemplate 檔案。  
  
3.  檔案的內容取代為下列 XML，然後儲存並關閉檔案。  
  
    > [!NOTE]  
    >  下列 XML 程式碼是 Visual C# 項目範本。 如果您要建立 Visual Basic 項目範本，以取代值`ProjectType`具有項目`VisualBasic`。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     此檔案會定義的內容和行為的項目範本。 這個檔案的內容的相關資訊，請參閱[Visual Studio 範本結構描述參考](/visualstudio/extensibility/visual-studio-template-schema-reference)。  
  
4.  在**方案總管] 中**，開啟捷徑功能表**ItemTemplate**專案，選擇**新增**，然後選擇 [**新項目**。  
  
5.  在**加入新項目**對話方塊方塊中，選擇**文字檔**範本。  
  
6.  在**名稱**方塊中，輸入**CustomAction.spdata**，然後選擇 [**新增**] 按鈕。  
  
7.  將下列 XML 程式碼加入至 CustomAction.spdata 檔案，然後儲存並關閉檔案。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     此檔案包含的專案項目所包含之檔案的相關資訊。 `Type`屬性`ProjectItem`元素必須設定為相同的字串傳遞至<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>專案項目定義上 (`CustomActionProjectItemTypeProvider`您稍早在本逐步解說中建立的類別)。 .Spdata 檔案的內容的相關資訊，請參閱[SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)。  
  
8.  在**方案總管] 中**，開啟捷徑功能表**ItemTemplate**專案，選擇**新增**，然後選擇 [**新項目**。  
  
9. 在**加入新項目**對話方塊方塊中，選擇**XML 檔案**範本。  
  
10. 在**名稱**方塊中，輸入**Elements.xml**，然後選擇 [**新增**] 按鈕。  
  
11. Elements.xml 檔案的內容取代為下列 XML，然後儲存並關閉檔案。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     此檔案會定義預設的自訂動作，可以建立功能表項目**網站動作**功能表的 SharePoint 網站。 當使用者選擇功能表項目時，在指定的 URL`UrlAction`開啟網頁瀏覽器中的項目。 如需詳細資訊的 XML 項目可用來定義自訂的動作，請參閱[自訂動作定義](http://go.microsoft.com/fwlink/?LinkId=177801)。  
  
12. 選擇性地開啟 ItemTemplate.ico 檔案並加以修改，使其具有可辨識的設計。 中的專案項目旁邊會顯示這個圖示**加入新項目** 對話方塊。  
  
13. 在**方案總管 中**，開啟捷徑功能表**ItemTemplate**專案，然後再選擇**卸載專案**。  
  
14. 開啟快顯功能表**ItemTemplate**同樣地，專案，然後選擇**編輯 ItemTemplate.csproj**或**編輯 ItemTemplate.vbproj**。  
  
15. 找出下列`VSTemplate`專案檔中的項目。  
  
    ```xml  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. 取代此項`VSTemplate`具有下列 XML，然後儲存和關閉檔案項目。  
  
    ```xml  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath`項目會指定其他資料夾中建置專案時，項目範本建立所在的路徑。 此處指定的資料夾確保項目範本會使用，只有當客戶**加入新項目**對話方塊方塊中，展開  **SharePoint**  節點，然後選擇  **2010年**節點。  
  
17. 在**方案總管 中**，開啟捷徑功能表**ItemTemplate**專案，然後再選擇**重新載入專案**。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item"></a>建立 VSIX 封裝，來部署專案項目  
 若要部署擴充功能，方案中使用 VSIX 專案建立 VSIX 封裝。 首先，設定 VSIX 封裝，藉由修改 source.extension.vsixmanifest 檔案中包含在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要設定，並建立 VSIX 封裝  
  
1.  在**方案總管] 中**，開啟捷徑功能表**source.extension.vsixmanifest** CustomActionProjectItem 專案中的檔案，然後選擇 [**開啟**。  
  
     Visual Studio 會在資訊清單編輯器中開啟檔案。 Source.extension.vsixmanifest 檔案是所有的 VSIX 套件需要 extension.vsixmanifest 檔案的基礎。 如需有關這個檔案的詳細資訊，請參閱[VSIX 擴充功能結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**產品名稱**方塊中，輸入**自訂動作專案項目**。  
  
3.  在**作者**方塊中，輸入**Contoso**。  
  
4.  在**描述**方塊中，輸入**SharePoint 專案項目代表自訂動作**。  
  
5.  在**資產**索引標籤上，選擇**新增** 按鈕。  
  
     **加入新資產** 對話方塊隨即出現。  
  
6.  在**類型**清單中，選擇**Microsoft.VisualStudio.ItemTemplate**。  
  
    > [!NOTE]  
    >  這個值會對應到`ItemTemplate`extension.vsixmanifest 檔案中的項目。 此項目可識別包含專案項目範本的 VSIX 套件中的子資料夾。 如需詳細資訊，請參閱[ItemTemplate 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0)。  
  
7.  在**來源**清單中，選擇**目前方案中的專案**。  
  
8.  在**專案**清單中，選擇**ItemTemplate**，然後選擇 [**確定**] 按鈕。  
  
9. 在**資產**索引標籤上，選擇**新增**按鈕一次。  
  
     **加入新資產** 對話方塊隨即出現。  
  
10. 在**類型**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個項目 VSIX 封裝中指定延伸模組組件的名稱。 如需詳細資訊，請參閱[MEFComponent 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
11. 在**來源**清單中，選擇**目前方案中的專案**。  
  
12. 在**專案**清單中，選擇**ProjectItemDefinition**。  
  
13. 選擇 [確定]  按鈕。  
  
14. 在功能表列上選擇 **建置**，**建置方案**，然後確認專案編譯無誤。  
  
15. 請確定 CustomActionProjectItem 專案建置輸出資料夾包含 CustomActionProjectItem.vsix 檔案。  
  
     根據預設，會將組建輸出資料夾...包含 CustomActionProjectItem 專案資料夾下的 \bin\Debug 資料夾。  
  
## <a name="testing-the-project-item"></a>測試專案項目  
 現在您已經準備好進行測試的專案項目。 首先，開始偵錯 CustomActionProjectItem 方案在 Visual Studio 的實驗執行個體。 然後，測試**自訂動作**Visual Studio 的實驗執行個體中的 SharePoint 專案中的專案項目。 最後，建置並執行 SharePoint 專案來驗證自訂動作如預期般運作。  
  
#### <a name="to-start-debugging-the-solution"></a>若要啟動偵錯方案  
  
1.  系統管理認證，以重新啟動 Visual Studio，然後開啟 CustomActionProjectItem 方案。  
  
2.  開啟 CustomAction 程式碼檔案，然後再將中斷點加入至程式碼中的第一行`InitializeType`方法。  
  
3.  選擇**F5**鍵開始偵錯。  
  
     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom 動作專案 Item\1.0 來安裝擴充功能，並啟動 Visual studio 的實驗執行個體。 您將這個執行個體的 Visual Studio 中測試的專案項目。  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>若要在 Visual Studio 中測試的專案項目  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**檔案**，**新增**，**專案**。  
  
2.  展開**Visual C#** 或**Visual Basic** （取決於支援的語言項目範本），依序展開**SharePoint**，然後選擇  **2010年**節點。  
  
3.  在專案範本清單中選擇**SharePoint 2010 專案**。  
  
4.  在**名稱**方塊中，輸入**CustomActionTest**，然後選擇 [**確定**] 按鈕。  
  
5.  在**SharePoint 自訂精靈**，輸入您想要用於偵錯，網站的 URL，然後選擇**完成** 按鈕。  
  
6.  在**方案總管] 中**，開啟專案節點的捷徑功能表，選擇**新增**，然後選擇 [**新項目**。  
  
7.  在**加入新項目**對話方塊方塊中，選擇**2010年**節點下的**SharePoint**節點。  
  
     確認**自訂動作**項目會出現在清單中的專案項目。  
  
8.  選擇**自訂動作**項目，然後再選擇**新增** 按鈕。  
  
     Visual Studio 會加入名為的項目**CustomAction1**至您的專案並 Elements.xml 檔案在編輯器中開啟。  
  
9. 確認 Visual Studio 的其他執行個體中的程式碼是您稍早在設定的中斷點上停止`InitializeType`方法。  
  
10. 選擇**F5**鍵繼續偵錯專案。  
  
11. 中的 Visual Studio 實驗執行個體中**方案總管 中**，開啟捷徑功能表**CustomAction1**  節點，然後選擇 **檢視自訂動作設計師**.  
  
12. 確認訊息方塊隨即出現，然後選擇 [**確定**] 按鈕。  
  
     您可以使用這個快顯功能表，以提供開發人員而言，例如顯示的自訂動作的設計工具的其他選項或命令。  
  
13. 在功能表列上選擇 **檢視**，**輸出**。  
  
     **輸出**視窗隨即開啟。  
  
14. 在**方案總管 中**，開啟捷徑功能表**CustomAction1**項目，然後再變更其名稱**MyCustomAction**。  
  
     在**輸出**視窗中，確認訊息出現。 此訊息會寫入由<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged>中所定義的事件處理常式`CustomActionProjectItemTypeProvider`類別。 您可以處理這個事件與其他專案項目事件，以實作自訂行為，當開發人員修改專案項目。  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>若要在 SharePoint 中測試自訂動作  
  
1.  在 Visual Studio 的實驗執行個體，開啟 子系的 Elements.xml 檔案**MyCustomAction**專案項目。  
  
2.  在 Elements.xml 檔案中，進行下列變更，並儲存檔案：  
  
    -   在`CustomAction`項目，設定`Id`GUID 或其他唯一的字串屬性，如下列範例所示：  
  
        ```xml  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   在`CustomAction`項目，設定`Title`屬性，如下列範例所示：  
  
        ```xml  
        Title="SharePoint Developer Center"  
        ```  
  
    -   在`CustomAction`項目，設定`Description`屬性，如下列範例所示：  
  
        ```xml  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   在`UrlAction`項目，設定`Url`屬性，如下列範例所示：  
  
        ```xml  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  選擇 F5 鍵。  
  
     封裝和部署到 SharePoint 網站中指定自訂動作**網站 URL**專案的屬性。 網頁瀏覽器會開啟此站台的預設頁面。  
  
    > [!NOTE]  
    >  如果**指令碼偵錯已停用**對話方塊出現時，選擇 **是**按鈕以繼續進行偵錯專案。  
  
4.  上**網站動作**功能表上，選擇**SharePoint 開發人員中心**，請確認瀏覽器會開啟網站http://msdn.microsoft.com/sharepoint/default.aspx，然後關閉網頁瀏覽器。  
  
## <a name="cleaning-up-the-development-computer"></a>清除開發電腦  
 在您完成測試的專案項目之後，請從 Visual Studio 的實驗執行個體中移除專案項目範本。  
  
#### <a name="to-clean-up-the-development-computer"></a>清除開發電腦  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**工具**，**擴充功能和更新**。  
  
     [擴充功能和更新] 對話方塊隨即開啟。  
  
2.  在 擴充功能的清單中，選擇 **自訂動作專案項目**，然後選擇 **解除安裝** 按鈕。  
  
3.  在出現的對話方塊中，選擇 **是**按鈕，以確認您想要解除安裝擴充功能。  
  
4.  選擇**立即重新啟動**按鈕，以完成解除安裝。  
  
5.  關閉 Visual Studio 的實驗執行個體和 CustomActionProjectItem 方案已開啟的執行個體。  
  
## <a name="next-steps"></a>後續步驟  
 完成此逐步解說之後，精靈可以加入項目範本。 當使用者加入自訂動作專案項目加入 SharePoint 專案時，精靈會收集資訊的動作 （例如其位置和選擇的動作時，瀏覽至 URL） 並將這項資訊加入至 Elements.xml 檔案，在新的專案項目。 如需詳細資訊，請參閱[逐步解說： 建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 建立自訂動作專案項目包含項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [建立項目範本和專案範本的 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio 範本結構描述參考](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [圖示影像編輯器](/cpp/windows/image-editor-for-icons)   
 [建立圖示或其他影像&#40;圖示影像編輯器&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  