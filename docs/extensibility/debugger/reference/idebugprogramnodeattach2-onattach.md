---
title: IDebugProgramNodeAttach2::OnAttach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c7c7e6f7ef640b192b7ed8c57ac87375a5ad189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
附加至相關聯的程式或延後的附加程序[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>參數  
 `guidProgramId`  
 [in]`GUID`要指派給相關聯的程式。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`如果[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)不應該呼叫方法。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法期間會呼叫 attach 程序之前[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法呼叫。 `OnAttach`方法可以執行 attach 程序本身 (在此情況下，這個方法會傳回`S_FALSE`) 或延遲的附加程序`IDebugEngine2::Attach`方法 (`OnAttach`方法會傳回`S_OK`)。 在可能情況下，`OnAttach`方法可以設定`GUID`要進行偵錯程式的給定`GUID`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)