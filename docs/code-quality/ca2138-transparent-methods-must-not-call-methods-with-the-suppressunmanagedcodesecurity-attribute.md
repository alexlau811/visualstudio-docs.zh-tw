---
title: CA2138：透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: af499ac6299498f09ab7e6a6ff54b02dc4901815
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138：透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 安全性透明方法呼叫的方法，以標示<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性。

## <a name="rule-description"></a>規則描述
 此規則會引發任何透明方法，直接呼叫原生程式碼，例如，使用透過 P/Invoke （平台叫用） 呼叫。 P/Invoke 和 COM interop 方法會標記為<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性導致正在進行對呼叫方法的 LinkDemand。 安全性透明程式碼無法滿足 Linkdemand，因為程式碼也不能呼叫標記使用 SuppressUnmanagedCodeSecurity 屬性、 方法或使用 SuppressUnmanagedCodeSecurity 屬性標記之類別的方法。 該方法會失敗，或視需要會轉換成完整的要求。

 違反此規則會導致<xref:System.MethodAccessException>層級 2 安全性透明度模型，而完整的要求，如<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>在層級 1 透明度模型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性和標記的方法與<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]