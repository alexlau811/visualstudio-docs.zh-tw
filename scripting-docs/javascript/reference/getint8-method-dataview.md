---
title: "getInt8 方法 (DataView) |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 867eefa0-f2e0-44b9-85bc-efb849d55138
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4963cb1b407b964b082daa10660fe812dcb700b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="getint8-method-dataview"></a>getInt8 方法 (DataView)
從開始檢視中取得指定的位元組位移的 Int8 值。 沒有對齊方式限制;多位元組值可能會擷取從任何的位移。  
  
## <a name="syntax"></a>語法  
  
```  
var testInt = dataView.getInt8(byteOffset);   
```  
  
## <a name="parameters"></a>參數  
 `testInt`  
 必要項。 從方法傳回的 Int8 值。  
  
 `byteOffset`  
 值應該擷取的緩衝區中的位置。  
  
## <a name="remarks"></a>備註  
 如果它們會讀取檢視結尾之外，這些方法會引發例外狀況。  
  
## <a name="example"></a>範例  
 下列範例會示範如何取得在 DataView 中的第一個 Int8。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt8(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]