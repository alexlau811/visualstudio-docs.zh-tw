---
title: "IActiveScriptDebug::GetScriptTextAttributes |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8e9cd76da3e754eabce836b386893043dcd0622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
傳回指令碼文字的任意區塊的文字屬性。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstrCode`  
 [in]指令碼區塊的文字。 這個字串不需要結束的 null。  
  
 `uNumCodeChars`  
 [in]指令碼區塊文字的字元數。  
  
 `pstrDelimiter`  
 [in]結束的指令碼區塊分隔符號的位址。 當`pstrCode`剖析文字資料流，從主應用程式通常會使用分隔符號，例如兩個單引號 （'），來偵測指令碼區塊的結尾。 這個參數會指定使用主機，允許以提供一些條件的基本前置處理指令碼引擎的分隔符號 （例如，取代單引號 ['] 具有兩個單引號做為分隔符號使用）。 方式 （和 if） 這項資訊取決於指令碼引擎的指令碼引擎使用。 如果主機未使用的分隔符號來標示指令碼區塊的結尾，請設定此參數為 NULL。  
  
 `dwFlags`  
 [in]指令碼區塊相關聯的旗標。 可以是下列值的組合：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|表示識別項和點運算子應該能識別出使用 SOURCETEXT_ATTR_IDENTIFIER 和 SOURCETEXT_ATTR_MEMBERLOOKUP 旗標，分別。|  
|GETATTRFLAG_THIS|0x0100|表示目前物件的識別項，應該識別 SOURCETEXT_ATTR_THIS 旗標。|  
|GETATTRFLAG_HUMANTEXT|0x8000|表示字串的內容和註解文字應該能識別出 SOURCETEXT_ATTR_HUMANTEXT 旗標。|  
  
 `pattr`  
 [in、 out]包含傳回的屬性的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 實作智慧主機`IDebugDocumentText`介面可以使用這個方法來委派呼叫`IDebugDocumentText::GetText`方法。  
  
 這個方法的指令碼區塊。`GetScriptletTextAttributes`方法是讓程式碼片段。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)