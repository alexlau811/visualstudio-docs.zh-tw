---
title: SccUncheckout 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c363da795e588963c234af05a856f3352a7b2815
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sccuncheckout-function"></a>SccUncheckout 函式
此函式會復原先前的簽出作業，藉此將選取的檔案或檔案的內容還原到之前簽出的狀態。 所有的檔案簽出之後所做的變更都會遺失。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]這是要復原簽出檔案的完整格式的本機路徑名稱的陣列。  
  
 fOptions  
 [in]命令的旗標 （不使用）。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|復原簽出成功。|  
|SCC_E_FILENOTCONTROLLED|選取的檔案不是原始程式碼控制之下。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。 復原簽出失敗。|  
|SCC_E_NOTCHECKEDOUT|使用者沒有簽出檔案。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_PROJNOTOPEN|無法從原始檔控制開啟專案。|  
|SCC_I_OPERATIONCANCELED|作業已完成前取消。|  
  
## <a name="remarks"></a>備註  
 這項作業後`SCC_STATUS_CHECKEDOUT`和`SCC_STATUS_MODIFIED`旗標會同時清除其上已執行復原簽出檔案。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)