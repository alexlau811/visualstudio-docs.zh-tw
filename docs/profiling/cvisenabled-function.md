---
title: CvIsEnabled 函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47129a84b38a4182514bf91be3c55704cf506410
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2018
---
# <a name="cvisenabled-function"></a>CvIsEnabled 函式
判斷任何工作階段是否已啟用指定的 ETW 提供者。  
  
## <a name="syntax"></a>語法  
  
```C  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>參數  
 `category`  
 分類。  
  
 `level`  
 重要性層級。  
  
 `pProvider`  
 有效的提供者物件。 不可以是 NULL。  
  
## <a name="return-value"></a>傳回值  
 如果提供者目前已啟用，傳回 S_OK。 如果提供者目前已停用，傳回 S_FALSE。 發生任何錯誤時傳回錯誤碼。 使用 FAILED 巨集可檢查是否有錯誤狀況，然後檢查是 S_OK/S_FALSE。  
  
## <a name="requirements"></a>需求  
 **標頭︰** cvmarkers.h  
  
## <a name="see-also"></a>請參閱  
 [C++ 程式庫參考](../profiling/cpp-library-reference.md)