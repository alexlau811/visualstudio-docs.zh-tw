---
title: Microsoft 說明檢視器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3ddc23ab56df017ef0a37c56cd5b0a81ee33a07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft 說明檢視器 SDK
本文章包含 Visual Studio 說明檢視器整合者執行下列工作：  
  
-   建立主題 （F1 支援）  
  
-   建立說明檢視器內容品牌封裝  
  
-   部署文件的集  
  
-   加入至 Visual Studio shell （整合模式或隔離） 的說明  
  
-   其他資源  
  
### <a name="creating-a-topic-f1-support"></a>建立主題 （F1 支援）  
本節提供呈現的主題、 主題需求的簡短描述如何建立主題 （包括 F1 支援需求），以及最終的範例主題以其呈現結果之元件的概觀。  
  
**說明檢視器主題概觀**  
  
說明檢視器時轉譯呼叫主題時，取得與在安裝或上次更新，以及主題 XHTML 主題相關聯的品牌封裝項目，並結合以產生呈現的內容檢視中的兩個 (商標資料 +主題資料）。  品牌封裝包含標誌、 支援內容的行為和商標文字 （著作權，等等）。  如需有關品牌封裝元素，[建立品牌封裝] 請參閱下文。  萬一沒有與主題相關聯的品牌封裝，說明檢視器會使用後援的品牌封裝位於說明檢視器應用程式根目錄 (Branding_en US.mshc)。  
  
**說明檢視器主題需求**  
  
若要在說明檢視器內正確轉譯，原始的主題內容必須是 W3C 基本 1.1 XHTML。  
  
主題通常包含兩個區段：  
  
-   中繼資料 （請參閱內容的中繼資料參考）： 資料有關該主題，例如，主題的唯一識別碼，關鍵字值，目錄識別碼的主題父節點識別碼、 等等。  
  
-   本文內容： 符合 W3C 基本 1.1 XHTML 的包含支援內容的行為 （可摺疊區域中，程式碼片段等。完整清單如下所示）。  
  
Visual Studio 品牌封裝支援控制項：  
  
-   連結  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   繼承的成員  
  
-   LanguageSpecificText  
  
支援的語言字串 （不區分大小寫）：  
  
-   Javascript  
  
-   csharp 或 c#  
  
-   cplusplus 或 visual c + + 或 c + +  
  
-   jscript  
  
-   visualbasic 或 vb  
  
-   f # fsharp 或 fs  
  
-   其他-表示語言名稱的字串  
  
**建立主題說明檢視器**  
  
建立新的 XHTML 文件，名為 ContosoTopic4.htm，並包含標題標籤 （如下）。  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
接下來，將資料新增到如何定義主題的顯示 （本身品牌與否） 的方式來參考本主題的 F1，本主題在目錄中，其識別碼 （由其他主題的連結參考） 中存在等。請參閱下面 「 內容中繼資料 」 表格以支援中繼資料的完整清單。  
  
-   在此情況下，我們將使用我們自己品牌封裝時，Visual Studio 說明檢視器的品牌封裝的 variant。  
  
-   新增 F1 中繼名稱和值 ("Microsoft.Help.F1"內容 ="ContosoTopic4")，將會符合所提供的 F1 值 IDE 屬性包中。  （請參閱 F1 支援 > 一節，如需詳細資訊）。 這是對應到 F1 的值從 ide 顯示本主題在 IDE 中選擇 f1 鍵時所呼叫。  
  
-   新增主題識別碼。 這是可由其他主題來連結至本主題的字串。  它是本主題說明檢視器識別碼。  
  
-   對於目錄中，加入本主題的父節點，即可定義此主題目錄節點出現的位置。  
  
-   對於目錄中，加入本主題的節點順序。 N 個子節點的父節點時，定義子節點順序本主題的位置。 例如，本主題是 4 的子主題的數字 4。)  
  
範例中繼資料 > 一節：  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
<meta name="SelfBranded" content="false" />     
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
**主題主體**  
  
（不包括頁首和頁尾） 中主題的主體會包含頁面的連結、 注意 > 一節、 可摺疊的區域，程式碼片段和一段特定語言的文字。  請參閱商標的區域顯示主題的資訊。  
  
1.  新增主題標題標記：  `<div class="title">Contoso Topic 4</div>`  
  
2.  新增附註 > 一節： `<div class="alert"> add your table tag and text </div>`  
  
3.  加入可摺疊的區域：  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  加入程式碼片段：  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  加入程式碼的語言特定的文字：`<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />`請注意該 devLangnu = 可讓您輸入其他語言。 例如，devLangnu ="Fortran 」 將會顯示 Fortran 時程式碼片段 DisplayLanguage = Fortran  
  
6.  加入頁面連結： `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  注意： 不支援新 「 顯示語言 」 （例如，F #、 Cobol、 Fortran） 程式碼顏色標示的程式碼片段會是單色。  
  
**說明檢視器主題的範例**的程式碼說明如何定義中繼資料、 程式碼片段，可摺疊的區域和語言特定的文字。  
  
```html
<?xml version="1.0" encoding="utf-8"?>  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
<meta name="SelfBranded" content="false" />     
</head>  
  
<body>  
<div class="title">Contoso Topic 4</div>  
  
  <div id="header">  
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">  
        <tr id="headerTableRow2"><td align="left">  
            <span id="nsrTitle">Contoso Topic 1</span>  
          </td>  
<td align="right">  
</td></tr>  
<tr id="headerTableRow1"><td align="left">  
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>  
          </td></tr>  
      </table>  
</div>  
  
<h2>Table of Contents</h2>  
  
<ul class="toc">  
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>  
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>  
</ul>  
  
<div class="topic">  
  
<div id="mainSection">  
<div id="mainBody">  
  
<a name="introduction"></a>  
<h2>1.0 Introduction</h2>  
<p>[This documentation is for sample purposes only.]</p>  
  
<p>Contoso Topic 1 contains examples of:  
<ul>  
<li>Collapsible Area</li>  
<li>Bookmark ("See also")</li>  
<li>Code Snippets from Branding Package</li>  
</ul>  
 </p>  
<div class="alert"><table><tr><th>  
<strong>Note </strong></th></tr>  
<tr><td>  
<p>This is an example of a <span class="label">Note </span>section.    
Call out important items for your reader in this <span class="label">Note </span>box.  
</p></td></tr>  
</table>  
</div>  
</div>  
  
<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">  
  
            <a id="sectionToggle0"><!----></a>  
  
<div>  
Example of Collapsible Area  
<br/>  
Lorem ipsum dolor sit amet...  
</div>  
</CollapsibleArea>  
  
<div id="snippetGroup" >  
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >  
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip  
Dim messageBoxVB as New System.Text.StringBuilder()  
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)  
    messageBoxVB.AppendLine()  
 ...  
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")  
End Sub  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >  
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)   
{   
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();  
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );  
messageBoxCS.AppendLine();  
...  
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );  
}  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >  
some F# code  
</CodeSnippet>  
</div>  
  
<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />  
  
<a name="seealso"></a>  
<h1 class="heading">See Also</h1>  
  
    <div id="seeAlsoSection" class="section">   
    <div class="seeAlsoStyle">  
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>  
    </div>  
 </div>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**F1 支援**  
  
在 Visual Studio 中，選取 F1 產生提供從 IDE 中的資料指標位置的值並於其中填入 「 屬性包"與提供的值 （根據游標位置。 當游標位於功能 x 時，功能 x 是在作用中/焦點，並填入具有值的屬性包。  選取 F1 時填入屬性包，及 Visual Studio F1 程式碼看起來客戶預設說明來源是否本機或線上 （線上是預設值），接著會建立設定的使用者為基礎的適當字串 （線上是預設值）-殼層執行（請參閱協助系統管理員指南 exe 啟動參數） 的本機說明檢視器再加上從屬性包，如果本機說明預設值或 MSDN URL 與參數清單中的關鍵字後面的參數。  
  
如果三個字串所傳回的 f1 鍵，參考為多重值字串時，請在第一個詞彙，尋找為叫用次數，以及如果找不到，我們已完成;否則，請移至下一個的字串。  順序很重要。 多重值關鍵字的呈現方式應該是最長到最短字串的字串。  若要確認此案例中的多重值的關鍵字，看看線上 F1 URL 字串，其中包含所選的關鍵字。  
  
在 Visual Studio 2012 中，我們故意更強的除以之間進行線上和離線時，這樣如果使用者的設定為 Online，然後我們只是 F1 要求直接傳遞至我們的線上查詢服務 MSDN，而不是協助程式庫代理程式透過路由傳送我們在 Visual Studio 2010。 我們再仰賴的狀態為 「 廠商安裝的內容 = true 」 來判斷是否要執行一些不同的內容中。 如果為 true，我們再執行此剖析和路由邏輯，根據您想要提供給客戶支援。 如果為 false，然後我們剛才移至 MSDN。 如果是本機使用者的設定，然後所有的呼叫只要移至本機說明引擎。  
  
F1 流程圖表：  
  
![F1 流程](../../extensibility/internals/media/f1flow.png "F1flow")  
  
當說明檢視器的預設說明內容來源設定為 線上 （啟動瀏覽器中）：  
  
-   Visual Studio 夥伴 (VSP) 功能會發出至 F1 屬性包 （屬性包 prefix.keyword 和線上 URL 登錄中找到的前置詞） 的值： F1 傳送 VSP URL + 參數至瀏覽器。  
  
-   Visual Studio 功能 （語言編輯器，Visual Studio 特定的功能表項目等）： F1 將 Visual Studio URL 傳送到瀏覽器。  
  
當說明檢視器的預設說明內容來源設定為本機說明 （啟動說明檢視器中）：  
  
-   VSP 功能關鍵字相符 F1 屬性包與本機存放區索引之間的位置 (也就是屬性包 prefix.keyword = 本機存放區索引中找到的值): F1 呈現說明檢視器中的主題。  
  
-   Visual Studio 功能 （若要覆寫從 Visual Studio 功能所發出的屬性包 VSP 任何選項）： F1 呈現 Visual Studio 中的主題說明檢視器。  
  
設定下列登錄值以啟用 F1 後援廠商說明內容。 F1 後援表示線上說明檢視器設定為尋找 F1 說明內容，而且廠商內容在本機安裝到使用者的硬碟機。 即使預設設定是線上說明的說明檢視器應該查看本機說明內容。  
  
1.  設定**VendorContent**協助 2.3 登錄機碼下的值：  
  
    -   32 位元作業系統：  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         「 VendorContent"= dword: 00000001  
  
    -   64 位元作業系統：  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         「 VendorContent"= dword: 00000001  
  
2.  登錄夥伴命名空間，以協助 2.3 登錄機碼下：  
  
    -   32 位元作業系統：  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< 命名空間\>*  
  
         「 位置 」 = 「 離線 」  
  
    -   64 位元作業系統：  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< 命名空間\>*  
  
         「 位置 」 = 「 離線 」  
  
**剖析的基礎原生命名空間**  
  
若要開啟基礎原生的命名空間剖析，請在登錄中加入新的 DWORD 的名稱： BaseNativeNamespaces 並設定其值為 1 （下他們想要支援類別目錄索引鍵）。  例如，如果您想要使用 Visual Studio 類別目錄，您可以加入機碼路徑：  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
當標頭/方法遇到格式 F1 關鍵字時，'/' 字元將會剖析，導致下列的建構：  
  
-   標頭： 將會是可用來在登錄中註冊的命名空間  
  
-   方法： 這會成為取得通過的關鍵字。  
  
例如，假設自訂的程式庫呼叫 CustomLibrary 和方法呼叫 MyTestMethod，當要求進入它 F1 將會格式化為`CustomLibrary/MyTestMethod`。  
  
使用者可以註冊為夥伴登錄區底下的命名空間的 CustomLibrary 並提供任何位置索引鍵，並傳遞給查詢的關鍵字將 MyTestMethod。  
  
**啟用偵錯工具在 IDE 中的說明**  
  
新增下列登錄機碼和值：  
  
HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic 說明鍵： 顯示偵錯輸出中零售值: [是]  
  
在 IDE 中，[說明] 功能表項目之下，選取 [偵錯說明內容]  
  
**內容的中繼資料**  
  
下表中出現在括號之間的任何字串是一個預留位置，必須將可辨識的值取代。 例如，在\<中繼 name="Microsoft.Help.Locale"內容 ="[語言程式碼]"/ >，"[語言程式碼]"必須取代值，例如 「 en-us-我們"。  
  
|屬性 （HTML 表示）|描述|  
|--------------------------------------|-----------------|  
|\< 中繼 name="Microsoft.Help.Locale"內容 ="[語言代碼]"/ >|本主題的地區設定。 如果此標記使用主題中，必須一次使用，且它必須插入上述任何其他 Microsoft 說明標記。 如果未使用此標記，主題的本文文字是以使用斷詞工具所關聯之產品的地區設定，如果您指定了; 編製索引否則，en-us-我們會使用斷詞工具。 此標記符合 ISOC RFC 4646。 若要確保 Microsoft 說明可正確運作，使用此屬性而不是一般的 [語言] 屬性。|  
|\< 中繼 name="Microsoft.Help.TopicLocale"內容 ="[語言代碼]"/ >|本主題的地區設定時也會使用其他地區設定。 如果此標記用於主題，它必須使用一次。 類別目錄包含一個以上的語言中的內容時，請使用這個標記。 在目錄中的多個主題都可以有相同的識別碼，但每個必須指定唯一的 TopicLocale。 指定符合目錄的地區設定 TopicLocale 這個主題會顯示在目錄中的主題。 不過，本主題的所有語言版本會都顯示在搜尋結果中。|  
|\< 標題 > [標題] \< /標題 >|指定本主題的標題。 此標記為必要項，並必須使用主題中的一次。 如果本主題的本文不包含標題\<d i v > 區段中，這個標題會顯示主題和內容的資料表中。|  
|\< 中繼名稱 ="Microsoft.Help.Keywords"內容 ="[aKeywordPhrase]"/ >|指定連結的說明檢視器的 [索引] 窗格中顯示的文字。 按一下連結時，會顯示主題。您可以指定多個索引關鍵字的主題，或如果您不想要顯示在索引中的此主題的連結，您可以省略這個標記。 "K"關鍵字，從舊版的說明可以轉換成這個屬性。|  
|\< 中繼 name="Microsoft.Help.Id"內容 ="[TopicID]"/ >|設定本主題的識別項。 此標記為必要項，並必須使用主題中的一次。 識別碼必須是唯一類別目錄中有相同的地區設定的主題。 在另一個主題中，您可以建立本主題的連結，使用此識別碼。|  
|\< 中繼 name="Microsoft.Help.F1"content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|指定本主題的 f1 說明關鍵字。 您可以指定多個主題的 F1 關鍵字，或如果您不想要應用程式使用者按下 F1 時顯示本主題，您可以省略這個標記。 通常，只有一個 F1 關鍵字會指定主題。 "F"關鍵字，從舊版的說明可以轉換成這個屬性。|  
|\< 中繼名稱 ="Description"content ="[主題 description]"/ >|提供簡短摘要，本主題中的內容。 如果此標記用於主題，它必須使用一次。 這個屬性是由查詢程式庫中; 直接存取它不會儲存在索引檔案。|  
 中繼 name="Microsoft.Help.TocParent"內容 ="[sys.internal_tables]"/ >|指定的父主題本主題中的目錄。 此標記為必要項，並必須使用主題中的一次。 這個值會是父代 Microsoft.Help.Id。 主題可以有一個位置資料表中的內容。 "-1"會被視為目錄根的主題識別碼。 在[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]，該頁面是說明檢視器 首頁。 這是我們特別將 TocParent = 1 新增到一些主題，以確保，它們顯示在上方層級相同的原因。說明檢視器首頁是系統頁面，因此不可取代。 如果 VSP 嘗試加入識別碼為-1 的頁面時，它可能會加入至內容集，但說明檢視器一律會使用 [系統] 頁面的說明檢視器首頁|  
|\< 中繼 name="Microsoft.Help.TocOrder"內容 ="[正整數]"/ >|指定的目錄中本主題出現位置相對於其對等主題。 此標記為必要項，並必須使用主題中的一次。 值為整數。 指定數值較小整數主題上方的主題指定的較高值的整數。|  
|\< 中繼 name="Microsoft.Help.Product"內容 ="[product code]"/ >|指定此主題描述的產品。 如果此標記用於主題，它必須使用一次。 這項資訊也可做為參數傳遞給協助索引子。|  
|\< 中繼 name="Microsoft.Help.ProductVersion"內容 ="[版本]"/ >|指定此主題描述的產品版本。 如果此標記用於主題，它必須使用一次。 這項資訊也可做為參數傳遞給協助索引子。|  
|\< 中繼 name="Microsoft.Help.Category"內容 ="[string]"/ >|用來識別子內容的產品。 您可以識別多個小節的主題，或如果您不想找出任何小節的連結，您可以省略這個標記。 此標記用來儲存 TargetOS 和 TargetFrameworkMoniker 的屬性，當轉換從較早版本的說明主題。 內容的格式是 AttributeName:AttributeValue。|  
|\< 中繼 name="Microsoft.Help.TopicVersion 內容 ="[主題版本 number]"/ >|多個版本存在的目錄中時，請指定此版本的主題。 Microsoft.Help.Id 不保證是唯一的因為此標記時，需要多個版本的主題是指在目錄中，比方說，類別目錄包含.NET Framework 3.5 和主題主題，適用於.NET Framework 4 和兩者都有相同的微軟性。Help.Id。|  
|\< 中繼名稱 ="SelfBranded"content ="[為 TRUE 或 FALSE]"/ >|指定本主題使用 Help Library 管理員啟動商標或商標套件的特定主題。 此標記必須是 TRUE 或 FALSE。 如果它會為 TRUE，則相關主題的品牌封裝會覆寫 Help Library 管理員啟動，以便讓主題呈現如預期般，即使它與不同的呈現方式的其他內容時才設定品牌封裝。 如果是 FALSE，目前的主題會轉譯根據 Help Library 管理員啟動時設定品牌封裝中。 根據預設，Help Library 管理員假設自我商標除非 SelfBranded 變數宣告為 TRUE; 否則為 false因此，您沒有宣告\<中繼名稱 ="SelfBranded"content ="FALSE"/ >。|  
  
### <a name="creating-a-branding-package"></a>建立品牌封裝  
Visual Studio 版本包含許多不同 Visual Studio 產品，包括 Visual Studio 協力廠商的隔離和整合式的 shell。  每項產品需要某種程度的品牌唯一產品支援主題式說明內容。  例如，Visual Studio 主題需要有一致的品牌簡報，而 SQL Studio 中，以包裝 ISO Shell，則需要使用它自己唯一說明內容的商標的每個主題。  整合式 Shell 協力廠商可能會想要在 Visual Studio 產品的說明內容的父系維持自己主題商標其說明主題。  
  
品牌封裝會安裝包含說明檢視器的產品。  適用於 Visual Studio 產品：  
  
-   後援的品牌封裝 (Branding_\<地區設定 >.mshc) 安裝說明檢視器 2.3 應用程式根目錄中 (範例： C:\Program Files (x86) \Microsoft Help Viewer\v2.3) 說明檢視器語言組件。  這適用於未安裝其中任一產品，品牌封裝的情況下 （已安裝任何內容） 或已安裝的品牌封裝已損毀的位置。  請注意，使用此應用程式根目錄後援品牌封裝時，會忽略 Visual Studio 項目 （標誌與意見反應）。  
  
-   安裝 Visual Studio 內容時，從內容封裝服務，商標套件也會安裝 （適用於第一個時間內容的安裝案例）。  品牌封裝的更新時下, 一個內容的更新或其他封裝的安裝動作發生情況時，會安裝的更新。  
  
Microsoft 說明檢視器支援主題主題中繼資料為基礎的商標。  
  
-   主題的中繼資料而定義自我品牌 = true、 轉譯現況的主題，會執行任何動作 （就商標）。  
  
-   主題的中繼資料而定義自我品牌 = false，使用商標套件 TopicVendor 中繼資料值相關聯。  
  
-   其中主題中繼資料定義 name="Microsoft.Help.TopicVendor"內容 =\<廠商 MSHA 在品牌封裝名稱 >，使用商標套件中的內容值定義。  
  
-   請注意，Visual Studio 類別目錄中，有優先順序應用的品牌封裝。  套用第一個 Visual Studio 預設商標，然後，如果主題中繼資料中定義，而且支援與相關聯的品牌封裝 （如安裝 msha 中所定義），覆寫套用商標的廠商定義。  
  
商標的項目通常會分成三個主要類別：  
  
-   （範例包括意見反應 連結、 條件式免責聲明文字、 標誌） 的標頭元素  
  
-   內容 （例如展開/摺疊控制項文字項目和程式碼片段項目） 的行為  
  
-   頁尾項目 （例如 Copyright）  
  
將其視為加上品牌的項目包含的項目 （此規格中詳述）：  
  
-   產品類別目錄/標誌 （例如，Visual Studio）  
  
-   意見反應連結和電子郵件項目  
  
-   免責聲明文字  
  
-   著作權的文字  
  
Visual Studio 說明檢視器的品牌封裝中支援的檔案包括：  
  
-   （標誌、 圖示） 的圖形  
  
-   Branding.js-指令碼檔案支援內容的行為  
  
-   Branding.xml-跨目錄內容以一致的方式使用的字串。  注意： Visual Studio 中 branding.xml 當地語系化文字項目包含由 _locID ="\<唯一值 > 」  
  
-   Branding.css-樣式定義的簡報一致性  
  
-   Printing.css-一致的列印呈現的樣式定義  
  
如先前所述，品牌封裝與主題相關聯:  
  
-   當 SelfBranded = false 已定義的中繼資料中，本主題會繼承品牌封裝的類別目錄  
  
-   或當 SelfBranded = false 和那里唯一的品牌封裝定義於 MSHA 和可用時安裝內容  
  
如 VSPs 實作自訂商標設定封裝 (VSP 內容，SelfBranded = True)，若要繼續的一種方式為啟動與後援的品牌封裝 （安裝說明檢視器），並將變更的檔案名稱。  Branding_\<地區設定 >.mshc 檔案是以副檔名變更為.mshc zip 檔案，只要從.mshc 將副檔名變更為.zip 和解壓縮內容。  請參閱以下的品牌封裝元素，並修改依適當情況 （例如，變更標誌 VSP 標誌和標誌 Branding.xml 檔案中的參考、 Branding.xml 更新每個 VSP 細節等）。  
  
完成所有修改，請建立包含所需的品牌元素的 zip 檔案，並將副檔名變更為.mshc。  
  
若要關聯到自訂商標套件，建立包含商標 mshc 檔案內容的 mshc （包含主題） 以及參考 MSHA。  請參閱下列說明如何建立基本 MSHA"MSHA"。  
  
Branding.xml 檔案包含用來以一致的方式呈現主題中的特定項目時，本主題中的清單項目\<中繼 name="Microsoft.Help.SelfBranded"內容 ="false"/ >。  下列為 Branding.xml 檔案中的項目 Visual Studio 清單。  請注意，這份清單適用於做為範本 ISO 殼層採用他們用來修改這些項目 （例如標誌、 意見反應，並且 Copyright） 以符合他們自己產品商標的需求。  
  
附註： 註明"{n}"的變數的程式碼相依性，移除或變更這些值會導致錯誤，而且可能是應用程式損毀。在 Visual Studio 品牌封裝中包含當地語系化的識別項 (範例 _locID="codesnippet.n")。  
  
**Branding.xml**  
  
|||  
|-|-|  
|功能：|**CollapsibleArea**|  
|用法:|展開摺疊內容控制項文字|  
|**目**|**值**|  
|ExpandText|Expand|  
|CollapseText|摺疊|  
|功能：|**CodeSnippet**|  
|用法:|控制項的程式碼片段的文字。  注意: 「 非中斷 」 空間的程式碼片段內容會變更到空間。|  
|**目**|**值**|  
|CopyToClipboard|複製至剪貼簿|  
|ViewColorizedText|以色彩標示的檢視|  
|CombinedVBTabDisplayLanguage|Visual Basic （範例）|  
|VBDeclaration|宣告|  
|VBUsage|使用量|  
|功能：|**意見反應、 頁尾和標誌**|  
|用法:|提供客戶提供透過電子郵件之目前主題的意見反應的意見反應控制項。  著作權文字內容。  標誌的定義。|  
|**目**|**值 （這些字串可以修改以符合內容 adopter 需要）。**|  
|著作權|© 2013 Microsoft Corporation。 著作權所有，並保留一切權利。|  
|SendFeedback|\<href ="{0}"{1} > 傳送意見反應 \< /a > 給 Microsoft 的這個主題。|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|功能：|**免責聲明**|  
|用法:|一組案例的特定免責聲明機器轉譯內容。|  
|**目**|**值**|  
|MT_Editable|本文是機器翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|  
|MT_NonEditable|本文是機器翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|  
|MT_QualityEditable|本文是人工翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|  
|MT_QualityNonEditable|本文是人工翻譯。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|  
|MT_BetaContents|本文是機器翻譯初步發行版。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|  
|MT_BetaRecycledContents|本文是人工翻譯為初步發行版。 如果您有網際網路連線時，選取 檢視線上本主題 「 以同時顯示原始英文內容的可編輯模式檢視這個頁面。|  
|功能：|**用於 LinkTable**|  
|用法:|支援線上主題連結|  
|**目**|**值**|  
|LinkTableTitle|連結資料表|  
|TopicEnuLinkText|檢視的英文版 \< /a > 的電腦使用本主題。|  
|TopicOnlineLinkText|檢視這個主題\<href ="{0}"{1} > 線上 \< /a >|  
|OnlineText|Online|  
|功能：|**視訊的音訊控制項**|  
|用法:|顯示項目和視訊內容的文字|  
|**目**|**值**|  
|MultiMediaNotSupported|必須安裝 Internet Explorer 9 或更高，以支援 {0} 內容。|  
|VideoText|顯示視訊|  
|AudioText|串流處理音訊|  
|OnlineVideoLinkText|\<p > 若要檢視與本主題相關聯的視訊，請按一下 {0}\<href ="\ {1 \}"> {2}here\</a >。\</ p >|  
|OnlineAudioLinkText|\<p > 若要聆聽與這個主題相關聯的音訊，按一下 {0}\<href ="\ {1 \}"> {2}here\</a >。\</ p >|  
|功能：|**未安裝的內容控制項**|  
|用法:|用於 contentnotinstalled.htm 呈現的文字元素 （字串）|  
|**目**|**值**|  
|ContentNotInstalledTitle|您的電腦上找不到任何內容。|  
|ContentNotInstalledDownloadContentText|\<p > 若要將內容下載到您的電腦， \<href ="{0}"{1} > 按一下管理索引標籤\</a >。\</ p >|  
|ContentNotInstalledText|\<p > 您的電腦上已安裝的任何內容。 請參閱您的系統管理員的本機說明內容安裝。 \< /p >|  
|功能：|**主題找不到控制項**|  
|用法:|用於 topicnotfound.htm 呈現的文字元素 （字串）|  
|**目**|**值**|  
|TopicNotFoundTitle|在您的電腦上找不到要求的主題。|  
|TopicNotFoundViewOnlineText|\<p > 您的電腦上找不到所要求的主題，但是您可以\<href ="{0}"{1} > 檢視線上主題\</a >。\</ p >|  
|TopicNotFoundDownloadContentText|\<p > 請參閱類似主題的連結的瀏覽窗格或\<href ="{0}"{1} > 按一下管理索引標籤\</a > 若要將內容下載到您的電腦。\</ p >|  
|TopicNotFoundText|\<p > 您的電腦上找不到所要求的主題。 \< /p >|  
|功能：|**主題已損毀的控制項**|  
|用法:|用於 topiccorrupted.htm 呈現的文字元素 （字串）|  
|**目**|**值**|  
|TopicCorruptedTitle|無法顯示要求的主題。|  
|TopicCorruptedViewOnlineText|\<p > 說明檢視器 」 無法顯示要求的主題。 可能在主題的內容或為基礎的系統相依性錯誤。 \< /p >|  
|功能：|**首頁上的控制項**|  
|用法:|支援說明檢視器的最上層節點內容的顯示文字。|  
|**目**|**值**|  
|HomePageTitle|說明檢視器首頁|  
|HomePageIntroduction|\<p > 歡迎使用 Microsoft 說明檢視器，為基本來源的每一位使用者使用 Microsoft 工具、 產品、 技術和服務的資訊。 說明檢視器可讓您存取 how to 及參考資訊、 程式碼範例、 技術文件，等等。 若要尋找的需要請瀏覽目錄的內容，使用全文檢索搜尋或瀏覽使用關鍵字索引的內容。 \< /p >|  
|HomePageContentInstallText|\<p >\<b / > 使用\<href ="{0}"{1} > 管理內容\</a > 索引標籤，以執行下列動作：\<u l >\<l i > 將內容加入至您的電腦。\</ l i >\<l i > 檢查您的本機內容的更新。\</ l i >\<l i > 從電腦移除內容。\</ l i >\</u l > \< /p >|  
|HomePageInstalledBooks|已安裝的書籍|  
|HomePageNoBooksInstalled|您的電腦上找不到任何內容。|  
|HomePageHelpSettings|說明內容的設定|  
|HomePageHelpSettingsText|\<p > 您目前的設定是本機說明。 說明檢視器會顯示您已安裝在電腦的內容。\<b / > 若要變更您的來源的說明內容，在 Visual Studio 功能表列上選擇\</><span style ="{0}"> 協助，請設定說明偏好\</s p a n i n k >。\<b / > \< /p >|  
|Mb|MB|  
  
**branding.js**  
  
Branding.js 檔案包含 JavaScript 使用由 Visual Studio 說明檢視器的商標設定項目。  以下是商標的項目和支援的 JavaScript 函式的清單。  此檔案的頂端 < 可當地語系化字串 > 一節中定義的這個檔案要當地語系化的所有字串。  請注意 ICL 檔案已經建立的 loc 字串中的 branding.js 檔案。  
  
||||  
|-|-|-|  
|**商標的功能**|**JavaScript 函式**|**描述**|  
|Var...||定義變數|  
|取得使用者程式碼語言|setUserPreferenceLang|對應索引 # 程式碼語言|  
|設定並取得 cookie 值|getCookie setCookie||  
|繼承的成員|changeMembersLabel|展開/摺疊繼承的成員|  
|當 SelfBranded = False|onLoad|讀取要檢查它是否列印要求的查詢字串。  設定所有 codesnippets 專注使用者慣用的索引標籤。如果是列印要求將 isPrinterFriendly 設為 true。 檢查有高對比模式。|  
|程式碼片段|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|在清單中寫入所有的可摺疊的控制項物件。|  
||CA_Click|可摺疊的區域的狀態為基礎，定義的映像和呈現的文字|  
|標誌的對比支援|isBlackBackground()|呼叫以判斷背景是否為黑色。  精確時，才在高對比模式。|  
||isHighContrast()|使用色彩的範圍偵測高對比模式|  
||onHighContrast(black)|當偵測到高對比時呼叫|  
|LST 功能|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|多媒體功能|標題 （開始、 結束時，文字樣式）||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify （styleName、 styleValue）||  
||showCC(id)||  
||subtitle(id)||  
  
**HTM 檔案**  
  
品牌封裝包含一組支援的通訊金鑰資訊與說明內容的使用者，例如首頁，其中包含描述安裝哪些內容集 > 一節和頁面的主題無法時告知使用者案例的 HTM 檔案主題的本機集合中找到。 請注意這些 HTM 檔案可修改，每項產品。  ISO 殼層廠商就能夠使用預設品牌封裝及變更的行為和這些網頁的內容套件需要的。  這些檔案是指其個別的商標套件，才能將商標的標記，以取得 branding.xml 檔案中的對應內容中。  
  
||||  
|-|-|-|  
|**檔案**|**使用**|**顯示內容來源**|  
|homepage.htm|這是一個網頁顯示目前已安裝的內容，以及適用於其內容相關的使用者顯示的任何其他訊息。  此檔案具有額外的中繼資料屬性 」 Microsoft.Help.Id"內容 ="-1"，而放置此內容在本機內容目錄的頂端。||  
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.xml、 標記\<HomePageTitle >|  
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.xml、 標記\<HomePageIntroduction >|  
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.xml、 標記\<HomePageContentInstallText >|  
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|標題區段 Branding.xml 標記\<HomePageInstalledBooks >，從應用程式，產生的資料\<HomePageNoBooksInstalled > 時就會安裝任何書籍。|  
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|標題區段 Branding.xml 標記\<HomePageHelpSettings >，區段文字\<HomePageHelpSettingsText >。|  
|topiccorrupted.htm|主題存在於本機設定，但無法顯示某些原因 （損毀的內容）。||  
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.xml、 標記\<TopicCorruptedTitle >|  
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.xml、 標記\<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|當主題找不到本機內容中設定，也可以使用線上||  
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.xml、 標記\<TopicNotFoundTitle >|  
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.xml、 標記\<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.xml、 標記\<TopicNotFoundText >|  
|contentnotinstalled.htm|當沒有本機內容安裝產品。||  
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.xml、 標記\<ContentNotInstalledTitle >|  
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.xml、 標記\<ContentNotInstalledDownloadContentText >|  
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.xml、 標記\<ContentNotInstalledText >|  
  
**CSS 檔案**  
  
Visual Studio 說明檢視器品牌封裝包含兩個 css 檔案，以支援一致的 Visual Studio 說明內容呈現：  
  
-   Branding.css-包含 css 項目呈現位置 SelfBranded = false  
  
-   Printer.css-包含 css 項目呈現位置 SelfBranded = false  
  
Branding.css 檔案包含 Visual Studio 主題簡報的定義 (需要注意的是 branding.css 內 Branding_\<地區設定 >.mshc 從封裝服務可能會變更)。  
  
**圖形檔案**  
  
Visual Studio 內容會顯示 Visual Studio 標誌，以及其他圖形。  Visual Studio 說明檢視器的品牌封裝中的圖形檔案的完整清單如下所示。  
  
||||  
|-|-|-|  
|**檔案**|**使用**|**範例**|  
|clear.gif|用來呈現可摺疊的區域||  
|footer_slice.gif|頁尾簡報||  
|info_icon.gif|用來顯示資訊|免責聲明|  
|online_icon.gif|這個圖示是要與線上連結產生關聯||  
|tabLeftBD.gif|用來呈現的程式碼片段容器||  
|tabRightBD.gif|用來呈現的程式碼片段容器||  
|vs_logo_bk.gif|用於 Branding.xml 標記中定義一般對比標誌參考\<LogoFileName >。  適用於 Visual Studio 產品標誌名稱會是 vs_logo_bk.gif。||  
|vs_logo_wh.gif|用於 Branding.xml 標記中定義一般高標誌參考\<LogoFileNameHC >。  適用於 Visual Studio 產品標誌名稱會是 vs_logo_wh.gif。||  
|ccOff.png|隱藏式輔助字幕圖形||  
|ccOn.png|隱藏式輔助字幕圖形||  
|ImageSprite.png|用來呈現可摺疊的區域|展開或摺疊圖形|  
  
### <a name="deploying-a-set-of-topics"></a>部署一系列主題  
這是既簡單又快速的教學課程，要建立設定組成 MSHA 檔案以及封包的設定說明檢視器內容部署或 MSHC 所含的主題。 描述一組的 cab 檔案的 XML 檔案或 MSHC 檔案 MSHA。 說明檢視器可以讀取 MSHA 取得一份內容 (。封包或。MSHC 檔案） 適用於本機安裝。  
  
這是僅描述的說明檢視器 MSHA 的非常基本的 XML 結構描述的入門。  請注意，範例實作下面這個簡短的概觀，以及範例 HelpContentSetup.msha。  
  
此入門，目的 MSHA，名稱是的 HelpContentSetup.msha （檔案名稱可以是任何項目，擴充功能。MSHA)。 HelpContentSetup.msha （下面的範例） 應該包含 cabs 或 MSHCs 可用的清單。  請注意，檔案類型必須是內 （不支援 MSHA 和 CAB 檔案類型的組合） MSHA 一致。 每個封包或 MSHC，應該有\<div 類別 = 「 套件 」 >...\</div > （請參閱下面的範例）。  
  
注意： 在實作下列範例中，我們包含商標的封裝。 這是包含以取得所需的 Visual Studio 內容呈現項目和內容行為非常重要。  
  
範例 [HelpContentSetup.msha] 檔案: (取代 「 內容設定名稱 1 」 和 「 內容集名稱 2 」 等等，都是以檔案名稱。)  
  
```html
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>.  
  
```  
  
1.  建立本機資料夾，就像 「 C:\SampleContent"  
  
2.  此範例中，我們將使用 MSHC 檔案包含的主題。  MSHC 是副檔名為.zip，以從變更的郵遞區號。MSHC。  
  
3.  建立以下 HelpContentSetup.msha 為文字檔案 （「 記事本 」 用來建立檔案） 並將它儲存到上面所述的資料夾 （請參閱步驟 1）。  
  
請注意，"商標 」 存在，而且是唯一的類別。 商標 mshc 一併併入此入門，因此已安裝的內容將會有商標且 MSHCs 中所包含的內容行為將會需要品牌封裝中包含的適當的支援項目。 未這麼做，系統會針對不屬於擷取 （安裝） 的支援項目內容時，會導致錯誤。  
  
若要取得 Visual Studio 品牌封裝，將複製到您的工作資料夾的 Branding_en US.mshc 檔案位於 C:\Program Files (x86) \Microsoft Help Viewer\v2.3\。  
  
```html  
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>  
<div class="package">  
<span class="packageType">branding</span>  
<span class="name">Branding_en-US</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**摘要**  
  
使用和擴充上述的步驟會啟用 VSPs 部署 Visual Studio 說明檢視器及其內容集。  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>將說明加入至 Visual Studio Shell （整合式驗證和獨立模式）  
**簡介**  
  
本逐步解說示範如何併入在 Visual Studio Shell 應用程式的說明內容，然後再部署它。  
  
**需求**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 隔離 Shell 可轉散發套件](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**概觀**  
  
[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]殼層是版本的[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]IDE 的基底應用程式。 這類應用程式包含在 Isolated Shell，連同您建立的延伸模組。 使用 Isolated Shell 的專案範本，其中包含在[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]SDK，建置擴充功能。  
  
建立 Isolated Shell 為基礎的應用程式和其說明的基本步驟：  
  
1.  取得[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]ISO 殼層可轉散發套件 （Microsoft 下載）。  
  
2.  在 Visual Studio 中，建立說明延伸模組為基礎的 Isolated Shell 中，例如，本逐步解說稍後所述的 Contoso 說明延伸模組。  
  
3.  擴充功能和可轉散發 MSI （應用程式安裝程式） 部署至 ISO 殼層會換行。 這個逐步解說中不包括安裝步驟。  
  
建立 Visual Studio 內容存放區。 整合式 Shell 案例中，變更視覺化 Studio12 產品類別目錄名稱，如下所示：  
  
-   建立資料夾 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15。  
  
-   建立名為 CatalogType.xml 檔案，並將它新增至資料夾。 此檔案應該包含下列程式碼：  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
在登錄中定義的內容存放區。 整合式 shell 中，變更為 產品類別目錄名稱的 VisualStudio15:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     索引鍵： LocationPath 字串值： C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     索引鍵： CatalogName 字串值：[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]文件  
  
**建立專案**  
  
若要建立 Isolated Shell 擴充功能：  
  
1.  在 Visual Studio 中，在**檔案**，選擇**新專案**下**其他專案類型**選擇**擴充性**，然後選擇  **Visual Studio Shell 隔離**。 將專案命名`ContosoHelpShell`) 來建立 Visual Studio Isolated Shell 範本為基礎的擴充性專案。  
  
2.  在方案總管 中，在 ContosoHelpShellUI 專案中的資源檔案 資料夾開啟 ApplicationCommands.vsct。 請確定這一行會取消註解 （搜尋"No_Help"）： `<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  選擇 F5 鍵以編譯及執行**偵錯**。 Isolated Shell IDE 的實驗執行個體，在選擇**協助**功能表。 請確定**檢視說明**，**加入和移除說明內容**，和**設定說明偏好**命令會顯示。  
  
4.  在方案總管 中，在 ContosHelpShell 專案中的 Shell Customization 資料夾中，開啟 ContosoHelpShell.pkgdef。 若要定義 Contoso 說明目錄中，加入下列幾行：  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  在方案總管 中，在 ContosHelpShell 專案中的 Shell Customization 資料夾中，開啟 ContosoHelpShell.Application.pkgdef。 若要啟用 F1 說明，請加入下列幾行：  
  
    ```  
    // F1 Help Provider  
  
    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="13407"  
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"  
    @="Help3 Provider"  
    [$RootKey$\HelpProviders]  
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"  
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="Help3 Provider"  
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  在 方案總管的 ContosoHelpShell 方案時，內容功能表上選擇**屬性**功能表項目。 在下**組態屬性**，選取**Configuration Manager**。 在**組態**資料行，將每個 「 偵錯 」 的值變更為 [發行]。  
  
7.  建置方案。 這將用於下一節中的發行資料夾中建立一組檔案。  
  
若要測試這，如同部署：  
  
1.  在電腦上您要部署若要安裝下載的 (corresponding) ISO 殼層 Contoso。  
  
2.  建立資料夾中的\\\Program Files (x86)\\，並將其命名`Contoso`。  
  
3.  內容複製到 ContosoHelpShell 發行資料夾\\\Program Files (x86) \Contoso\ 資料夾。  
  
4.  選擇啟動登錄編輯程式**執行**中**啟動**功能表，並輸入`Regedit`。 在 登錄編輯器中，選擇 **檔案**，然後**匯入**。 瀏覽至 ContosoHelpShell 專案資料夾。 在 ContosoHelpShell 子資料夾中，選擇 ContosoHelpShell.reg。  
  
5.  建立內容存放區：  
  
     ISO shell-建立 Contoso 內容存放區 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     如[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]整合式 Shell、 建立資料夾 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  建立 CatalogType.xml 並加入要包含的內容存放區 （上一個步驟）：  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  加入下列登錄機碼：  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath 字串值：  
  
     ISO shell:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 整合式的 Shell:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-美國  
  
     索引鍵： CatalogName 字串值：[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]文件。 ISO 殼層，這是您目錄的名稱。  
  
8.  將您的內容 （封包或 MSHC 和 MSHA） 複製到本機資料夾。  
  
9. 整合式 Shell 命令列範例測試內容存放區。 ISO shell，變更適當地比對的產品類別目錄和 launchingApp 值。  
  
     "C:\Program 檔案 (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe"/catalogName VisualStudio15 /helpQuery 方法 = 」 頁面與 id = ContosoTopic0"/launchingApp Microsoft visual Studio，12.0  
  
10. 啟動 Contoso 應用程式 （來自 Contoso 應用程式根目錄）。 在 ISO 殼層中，選擇 **協助**功能表項目，並將變更**設定說明偏好**至**使用本機說明**。  
  
11. 在殼層中，選擇 **協助**功能表項目，然後**檢視說明**。 應啟動的本機說明檢視器。 選擇 [管理內容] 索引標籤。在下**安裝來源**，選擇**磁碟**選項按鈕。 選擇 **...** 按鈕並瀏覽至包含 Contoso 內容 （複製到上一個步驟中的本機資料夾） 的本機資料夾。 選擇 [HelpContentSetup.msha]。 Contoso 應該顯示為活頁簿中的活頁簿選取項目中。 選擇**新增**，然後選擇 **更新**按鈕 （右上角的下方）。  
  
12. 在 Contoso IDE 中，選擇 F1 鍵，以測試 F1 功能。  
  
### <a name="additional-resources"></a>其他資源  
執行階段 API，請參閱[Windows 說明 API](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)。  
  
如需有關如何運用協助應用程式開發介面的詳細資訊，請參閱[說明檢視器程式碼範例](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
若要提供有關這些元件的意見反應，請使用[Microsoft Connect](http://connect.microsoft.com/)。  
  
請將 功能的建議[Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
若要取得其他說明，請嘗試[MSDN 開發人員文件，以及說明系統論壇](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
更新重大問題，請參閱[說明檢視器讀我檔案](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
若要直接連絡說明檢視器 PM 小組，傳送電子郵件 hlpfdbk@microsoft.com