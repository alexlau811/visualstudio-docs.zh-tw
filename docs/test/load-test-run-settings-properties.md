---
title: Visual Studio 中的負載測試回合設定 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: d278323bd816a801d94d2d1c18755111afa43eed
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="load-test-run-settings-properties"></a>負載測試回合設定屬性

負載測試的回合設定會決定多種其他設定，包括測試的持續期間、結果收集詳細層級，以及在測試執行時所收集的計數器集合。 您可以針對每個負載測試建立和儲存多個回合設定，然後在執行測試時選取一個特定的設定。 當您使用 [新增負載測試精靈] 來建立負載測試時，就會將初始回合設定加入至負載測試。

 下表將說明負載測試回合設定的各種屬性。 您可以修改這些屬性，以符合特定的負載測試需求。

 如需詳細資訊，請參閱[設定負載測試回合設定](../test/configure-load-test-run-settings.md)。

## <a name="general-properties"></a>一般內容

|屬性|定義|
|--------------|----------------|
|**描述**|回合設定的描述。|
|**每一類型的錯誤數目上限**|要為負載測試儲存的每一類型的錯誤數目上限。<br /><br /> 您可視需求增加此數目，但是這樣做將會增加負載測試結果的大小和處理時間。|
|**回報的要求 URL 最大數目**|此負載測試中要回報結果之唯一 Web 效能測試要求 URL 的最大數目。<br /><br /> 您可視需求增加此數目，但是這樣做將會增加負載測試結果的大小和處理時間。|
|**臨界值違規數目上限**|要為這個負載測試儲存的臨界值違規數目上限。<br /><br /> 您可視需求增加此數目，但是這樣做將會增加負載測試結果的大小和處理時間。|
|**執行應用程式定義域中的單元測試**|布林 (Boolean) 值，決定當負載測試包含單元測試時，是否要在個別應用程式定義域中執行各個單元測試組件 (Assembly)。 預設為 True。<br /><br /> 如果單元測試不需要個別應用程式定義域或 app.config 檔案就可以正常運作，藉由將這個屬性的值設定為 `False`，單元測試可能會更快速執行。|
|**名稱**|[回合設定] 節點出現在 [負載測試編輯器] 中的名稱。|
|**驗證層級**|這會定義將在負載測試中執行之驗證規則的最高層級。 驗證規則與 Web 效能測試要求有關。 每條驗證規則都具有關聯的驗證層級：[高]、[中] 或 [低]。 這個負載測試回合設定將會指定當 Web 效能測試在負載測試中執行時，會執行哪些驗證規則。 例如，如果這項回合設定是設定為 [中]，所有標記為 [中] 或 [低] 的驗證規則便都會執行。|

## <a name="logging-properties"></a>記錄屬性

|屬性|定義|
|--------------|----------------|
|**測試記錄數目上限**|指定要為負載測試儲存的測試記錄數目上限。 當達到為測試記錄數目上限輸入的值時，負載測試會停止收集記錄。 因此，在測試開始時就會收集記錄，而非在測試結束時。 負載測試會繼續執行，直到完成。|
|**已完成之測試的儲存記錄檔頻率**|指定寫入測試記錄檔的頻率。 此數字表示次數，即測試每執行到輸入的次數，就會儲存至測試記錄檔。 例如，如果輸入值 10，即等於指定將第 10、20、30 次 (依此類推) 的測試寫入至測試記錄檔。 將值設定為 0 表示不儲存測試記錄檔。<br /><br /> 如需詳細資訊，請參閱[如何：指定儲存測試記錄的頻率](../test/how-to-specify-how-frequently-test-logs-are-saved.md)|
|**測試失敗時儲存記錄檔**|布林值，用於判斷當負載測試中的測試失敗時是否要儲存測試記錄。 預設為 `True`。<br /><br /> 如需詳細資訊，請參閱[如何：指定測試失敗是否會儲存至測試記錄](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

 如需詳細資訊，請參閱[修改負載測試記錄設定](../test/modify-load-test-logging-settings.md)。

## <a name="results-properties"></a>結果屬性

|屬性|定義|
|--------------|----------------|
|**儲存區類型**|儲存負載測試取得之效能計數器的方式。 選項如下所示：<br /><br /> -   **資料庫** - 需要具有 [負載測試結果存放區] 的 SQL 資料庫。<br />-   **無**。|
|**計時詳細資料儲存區**|用來判斷何種詳細資料會儲存至 [負載測試結果存放區] 中。 可用的值有三種：<br /><br /> -   **所有個別細節** - 在負載測試期間，為每項執行或發佈的測試、異動和頁面，將個別計時值收集和儲存在 [負載測試結果存放區] 中。 如果要在 [負載測試分析器] 中使用 [虛擬使用者活動圖]，這個值是必要的。<br />     如需詳細資訊，請參閱[在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)。<br />-   **無** - 不收集任何個別計時值。 這是 Visual Studio 2013 Update 4 和更新版本的預設值。<br />-   **僅限統計資料** - 在負載測試期間，並不會為每項執行或發佈的測試、異動和頁面，將個別計時值收集和儲存在 [負載測試結果存放區] 中，而是只在其中儲存統計資料。<br /><br /> 如需詳細資訊，請參閱[如何：指定計時詳細資料儲存區屬性](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)。|

## <a name="sql-tracing-properties"></a>SQL 追蹤屬性

|屬性|定義|
|--------------|----------------|
|**追蹤的 SQL 作業的最小持續期間**|SQL 追蹤所要擷取之 SQL 作業的最小持續期間 (以毫秒為單位)。 例如，如果您嘗試在負載的情況下尋找慢速的 SQL 作業，這可讓您忽略快速完成的作業。|
|**SQL 追蹤連接字串**|用來存取要追蹤之資料庫的連接字串 (Connection String)。|
|**SQL 追蹤目錄**|SQL 追蹤檔案在追蹤結束時所放置的位置。 SQL Server 必須要具有這個目錄的寫入權限，而控制器則必須具有讀取權限。|
|**SQL 追蹤已啟用**|此項會啟用 SQL 作業的追蹤， 預設值是 `False`。|

## <a name="test-iterations-properties"></a>測試反覆項目屬性

|屬性|定義|
|--------------|----------------|
|**測試反覆項目**|指定在負載測試完成之前所要執行的個別測試總數。 這個屬性只有在 [使用測試反覆項目] 屬性為 `True` 時才適用。|
|**使用測試反覆項目**|如果 [使用測試反覆項目] 為 `True`，則負載測試將會反覆執行，直到負載測試內完成之個別測試數目達到 [測試反覆項目] 屬性所指定的數目為止。 在這種情況下，將會忽略以時間為主的設定，包括 [準備持續時間]、[執行持續時間] 和 [緩和持續時間]。 如果 [使用測試反覆項目] 為 `False`，則會套用所有時間設定，而會忽略 [測試反覆項目]。|

 如需詳細資訊，請參閱[如何：在回合設定中指定測試反覆項目的數目](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)。

## <a name="timing-properties"></a>計時屬性

|屬性|定義|
|--------------|----------------|
|**緩和持續期間**|測試緩和期的持續時間，以 hh:mm:ss 的格式表示。 負載測試完成時，負載測試內的個別測試可能仍然繼續執行。 在緩和期中，這些測試可以繼續執行，直到測試完成或緩和期結束為止。 預設情況下並沒有緩和期；個別測試將依據 [執行持續期間] 設定，在負載測試完成時便告終止。|
|**執行持續期間**|測試的時間長短，格式為 hh:mm:ss。|
|**採樣速率**|擷取效能計數器值的間隔時間，格式為 hh:mm:ss。<br /><br /> 如需詳細資訊，請參閱[如何：指定採樣速率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)。|
|**準備持續期間**|開始測試和開始記錄資料取樣之間的這一段時間，格式為 hh:mm:ss。 這經常用來在錄製樣本值之前，使負載虛擬使用者逐步達到特定的載入層級。 在準備期結束前所擷取到的樣本值，將會顯示在 [負載測試分析器] 中。|

## <a name="webtest-connections-properties"></a>WebTest 連接屬性

|屬性|定義|
|--------------|----------------|
|**WebTest 連接模型**|這會為在負載測試內執行的 Web 效能測試，控制從負載測試代理程式到 Web 伺服器之間的連接使用方式。 可用的 Web 效能測試連接模型選項有三種：<br /><br /> -   [每使用者連接] 模型會模擬使用真實瀏覽器之使用者的行為。 當模擬 Internet Explorer 6 或 Internet Explorer 7 時，每個執行 Web 效能測試的虛擬使用者，都會使用一個或兩個專用於 Web 伺服器的連接。 在 Web 效能測試發出第一個要求時，便會建立第一個連接。 當某個頁面含有一個以上的相依要求時，才會建立第二個連接， 而這些要求便會透過這兩個連接同時發送出去。 接著當 Web 效能測試繼續發送要求時，便會重複使用這些連接。 當 Web 效能測試完成時，這些連接就會關閉。 這個模型的缺點是，在代理程式電腦上保持開啟的連接數目可能很高 (高達使用者負載的兩倍)。 因此，支援這種高連接計數所需的資源可能會限制可從單一負載測試代理程式驅動的使用者負載。 當模擬 Internet Explorer 8 時，支援六個並行連接。<br />-   [連接集區] 模型會讓多個虛擬 Web 效能測試使用者共用與網頁伺服器的連接，節省負載測試代理程式上的資源。 如果使用者負載大於連接集區大小，由不同虛擬使用者所執行的 Web 效能測試就會共用一個連接。 這表示一個 Web 效能測試在發出要求之前，可能必須等待正在使用連接的另一個 Web 效能測試。 Web 效能測試在提交要求之前所等待的平均時間，都會由負載測試效能計數器 Average Connection Wait Time (平均連接等候時間) 追蹤。 這個時間應該要小於頁面的平均回應時間， 否則，連接集區大小就有可能不足。<br />-   [每一測試反覆項目的連接] 模型會指定每個測試反覆項目使用專用連接。|
|**WebTest 連接集區大小**|這會指定在負載測試代理程式和 Web 伺服器之間，可以產生的最大連接數目， 但只適用於 [連接集區] 模型。|

##  <a name="LoadTestRunSettingsHowToChange"></a> 變更回合設定屬性
 您可以使用不同的屬性設定，將其他回合設定加入至負載測試，以便在不同的狀況下執行負載測試。 例如，您可以加入新的測試設定並且使用不同的取樣率，或指定較長的執行持續期間。 您一次只能使用一個回合設定，而且必須透過讓回合設定變成作用中的方式指定要使用的回合設定。 如需範例，請參閱[如何：選取負載測試的使用中回合設定](../test/how-to-select-the-active-run-setting-for-a-load-test.md)。

### <a name="to-change-run-settings"></a>若要變更回合設定

1.  開啟負載測試。

2.  展開 [回合設定] 資料夾。

3.  選擇 [回合設定] 節點。

4.  在 [檢視] 功能表上選擇 [屬性視窗]。

     [屬性視窗] 隨即顯示，並顯示選取之回合設定的屬性。

5.  使用 [屬性視窗] 變更回合設定。 例如，將執行持續期間變更為 [00:05:00] 以執行測試五分鐘。

    > [!NOTE]
    > 如需回合設定屬性及其描述的完整清單，請參閱[負載測試回合設定屬性](../test/load-test-run-settings-properties.md)。

6.  當您變更屬性完成時，請儲存負載測試。 在 [檔案] 功能表上，選擇 [儲存]。

> [!NOTE]
> 計數器集合對應也是回合設定的一部分。 如需詳細資訊，請參閱[在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)。

## <a name="see-also"></a>另請參閱

- [設定負載測試回合設定](../test/configure-load-test-run-settings.md)