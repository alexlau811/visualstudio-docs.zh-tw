---
title: PROCESS_INFO_FIELDS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3376db379e4e911bcaa8e865a16c63d1251229f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
指定要擷取處理序的資訊種類。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>成員  
 PIF_FILE_NAME  
 初始化/使用`bstrFileName`欄位[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)結構。  
  
 PIF_BASE_NAME  
 初始化/使用`bstrBaseName`欄位`PROCESS_INFO`結構。  
  
 PIF_TITLE  
 初始化/使用`bstrTitle`欄位`PROCESS_INFO`結構。  
  
 PIF_PROCESS_ID  
 初始化/使用`ProcessId`欄位`PROCESS_INFO`結構。  
  
 PIF_SESSION_ID  
 初始化/使用`dwSessionId`欄位`PROCESS_INFO`結構。  
  
 PIF_ATTACHED_SESSION_NAME  
 初始化/使用`bstrAttachedSessionName`欄位`PROCESS_INFO`結構。  
  
 PIF_CREATION_TIME  
 初始化/使用`CreationTime`欄位`PROCESS_INFO`結構。  
  
 PIF_FLAGS  
 初始化/使用`Flags`欄位`PROCESS_INFO`結構。  
  
 PIF_ALL  
 填寫所有欄位。  
  
## <a name="remarks"></a>備註  
 傳遞至[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)方法，以表示的哪些欄位[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)結構會進行初始化。  
  
 也用於`Fields`欄位`PROCESS_INFO`結構，以指出哪些欄位是使用且有效。  
  
 這些旗標可能會合併使用位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)