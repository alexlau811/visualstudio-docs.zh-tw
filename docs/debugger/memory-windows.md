---
title: 偵錯工具中的變數，以檢視記憶體 |Microsoft 文件
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 550c5ffe641fac5bb2d080a892143bf3ff9744b0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具中的 [記憶體] 視窗
**記憶體**視窗可讓您檢視您的應用程式使用的記憶體空間。 **監看式**視窗中，**快速監看式**對話方塊中，**自動變數**視窗中，和**區域變數**視窗會顯示的變數，也就是內容儲存在記憶體中的特定位置。 但是**記憶體** 視窗會顯示整體。 這類檢視對於檢查無法適當地顯示在其他視窗的大批資料 (例如，緩衝區或很大的字串) 來說極為方便。 不過，**記憶體**視窗並不限於顯示資料。 它還會顯示記憶體空間內的所有內容，不管這些內容是資料、程式碼，或是未指派之記憶體內的無意義資料。  
  
 **記憶體**視窗是在已啟用位址層級偵錯時，才可以使用**選項**對話方塊中，**偵錯**節點。 **記憶體**視窗不適用於指令碼或 SQL，這些語言都無法辨識記憶體的概念。  
  
## <a name="opening-a-memory-window"></a>開啟記憶體視窗  
  
#### <a name="to-open-a-memory-window"></a>若要開啟記憶體視窗  
  
1.  如果目前不在偵錯模式下，請啟動偵錯。  
  
2.  在**偵錯**功能表上，指向**Windows**。 然後指向 **記憶體**，然後按一下 **記憶體 1**，**記憶體 2**，**記憶體 3**，或**記憶體 4**。 (較低層級版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]只有單一**記憶體**視窗。 如果您使用其中一個版本，只要按一下**記憶體**。)  
  
## <a name="paging-in-the-memory-window"></a>記憶體視窗中的分頁  
 **記憶體**時段具有非標準的方式操作的垂直捲軸。 現代電腦的位址空間很大，如果您抓住捲軸方塊並將它拖曳到隨機位置，很容易就會迷失。 因此，捲動方塊採「彈簧式設計」，永遠維持在捲軸的中央。 在機器碼應用程式中，您可以向上或向下翻頁，但不能自由捲動。  
  
 較高的記憶體位址會出現在視窗底部。 若要檢視較高的位址，請向下捲動而非向上捲動。  
  
#### <a name="to-page-up-or-down-in-memory"></a>若要在記憶體中向上或向下翻頁  
  
1.  若要向下翻頁 (移至較高的記憶體位址)，請按一下垂直捲軸中捲動方塊的下方某處。  
  
2.  若要向上翻頁 (移至較低的記憶體位址)，請按一下垂直捲軸中捲動方塊的上方某處。  
  
## <a name="selecting-a-memory-location"></a>選取記憶體位置  
 如果您想要立即移到選取的位置，在記憶體中，您可以使用拖放作業，或藉由編輯中的值**位址**方塊。 **位址**方塊可接受，而不是只是數值運算式評估為位址。 根據預設，**記憶體**視窗會把**位址**即時的運算式，在程式執行時，會重新評估的運算式。 現場運算式非常有用。 例如，您可使用它們來檢視指標所碰觸的記憶體。  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>若要透過拖放方式來選取記憶體位置  
  
1.  在任何視窗中選取記憶體位址或含記憶體位址的指標變數。  
  
2.  將位址或指標拖曳**記憶體**視窗。  
  
#### <a name="to-select-a-memory-location-by-editing"></a>若要使用編輯方式來選取記憶體位置  
  
1.  在**記憶體**視窗中，選取**位址**方塊。  
  
2.  輸入或貼上您想要查看，然後按下的位址**ENTER**。  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>變更記憶體視窗顯示資訊的方式  
 您可以自訂方式**記憶體**視窗顯示記憶體內容。 根據預設，記憶體內容會在十六進位格式中以一位元組整數資料型別出現，而且欄位數會自動依據目前視窗寬度來決定。  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>若要變更記憶體內容格式  
  
1.  以滑鼠右鍵按一下**記憶體**視窗。  
  
2.  選擇您要的格式。  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>若要變更記憶體視窗中的欄位數  
  
1.  在頂端工具列中**記憶體**視窗中，找出**資料行**清單。  
  
2.  在**資料行**清單中，選取您想要顯示或選取的資料行數目**自動**的自動調整視窗的寬度。  
  
 如果您不想要的內容**記憶體**視窗變更為您的程式執行，您可以關閉實況運算式評估。  
  
#### <a name="to-toggle-live-evaluation"></a>若要切換實況評估  
  
1.  以滑鼠右鍵按一下**記憶體**視窗。  
  
2.  在捷徑功能表，按一下 **自動重新評估**。  
  
     如果開啟實況評估，則會選取這個選項，您只要再按一下該選項即可關閉實況評估。 如果關閉實況評估，則不會選取這個選項，您只要再按一下該選項即可開啟實況評估。  
  
 您可以隱藏或顯示在頂端工具列**記憶體**視窗。 隱藏工具列時，您無法存取 [位址] 方塊或其他工具。  
  
#### <a name="to-toggle-the-toolbar"></a>若要切換工具列  
  
1.  以滑鼠右鍵按一下**記憶體**視窗。  
  
2.  在捷徑功能表，按一下 **顯示工具列**。  
  
     工具列會不會出現，需視先前的狀態而定。  
  
## <a name="following-a-pointer-through-memory"></a>隨著指標變動記憶體位置  
 您也可以在機器碼應用程式中，將暫存器名稱當成機動性的運算式。 例如，您可使用堆疊指標隨著堆疊而變動位置。  
  
#### <a name="to-follow-a-pointer-through-memory"></a>若要隨著記憶體變動指標  
  
1.  在**記憶體**視窗**位址**方塊中，輸入指標運算式。 指標變數必須在目前的範圍內。 有時您可能會需要取值 (Dereference)，視語言而定。  
  
2.  按 **ENTER** 鍵。  
  
     現在，當您使用執行命令例如**步驟**，會顯示的記憶體位址會自動隨著指標變動而變動。  
  
## <a name="see-also"></a>另請參閱  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)