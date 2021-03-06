---
title: 訊息標記 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb0ff0bfb8f4b7abf3abc7f31204d963c1f0a68b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="message-markers"></a>訊息標記
訊息標記表示記錄檔輸出。 訊息是由特定執行緒在特定時間發出的字串。 您可以將訊息匯出成文字檔，以便與其他工具搭配使用。 您可以將指標放在並行視覺化檢視中的訊息上，以檢視訊息字串。 您可以檢視在[標記報告](../profiling/markers-report.md)中檢視所有訊息標記。  下圖顯示訊息標記。  
  
## <a name="message-aggregation-markers"></a>訊息彙總標記  
 有時多個訊息發生的位置太靠近並行視覺化檢視中的另一個標記，以至於無法個別繪製。 發生這種情況時，會顯示一個表示基礎訊息的灰色「訊息彙總標記」。 當您將指標放在這些圖示的其中一個時，工具提示會顯示所代表基礎訊息的數目。 若要檢視訊息，請予以放大。  如果您縮放到最大後仍然出現彙總標記，您可以在[標記報告](../profiling/markers-report.md)中檢視基礎訊息。  
  
## <a name="see-also"></a>請參閱  
 [並行視覺化檢視標記](../profiling/concurrency-visualizer-markers.md)   
 [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)