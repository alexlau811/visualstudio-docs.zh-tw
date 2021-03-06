---
title: '&lt;fileAssociation&gt;元素 （ClickOnce 應用程式） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f59ef1d00951d4c49c1bcb19c6c9122e281c3ca
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt;元素 （ClickOnce 應用程式）
識別要與應用程式相關聯的副檔名。  
  
## <a name="syntax"></a>語法  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `fileAssociation` 項目是選擇性的。 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`extension`|必要。 要與應用程式相關聯的副檔名。|  
|`description`|必要。 Shell 所使用的檔案類型的描述。|  
|`progid`|必要。 可唯一識別檔案類型的名稱。|  
|`defaultIcon`|必要。 指定要用於此副檔名的檔案的圖示。 必須使用指定的圖示檔[\<檔案 > 項目](../deployment/file-element-clickonce-application.md)內[\<組件 > 項目](../deployment/assembly-element-clickonce-application.md)，其中包含這個項目。|  
  
## <a name="remarks"></a>備註  
 這個項目必須包括 XML 命名空間參考，以 「 結構描述 urn:-microsoft-com:clickonce.v1"。 如果`<fileAssociation>`項目時，它必須緊跟在後`<application>`中其父系的項目[\<組件 > 項目](../deployment/assembly-element-clickonce-application.md)。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 不會覆寫現有的檔案關聯。 不過，ClickOnce 應用程式可以覆寫目前使用者的副檔名。 解除安裝該 ClickOnce 應用程式之後，ClickOnce 會刪除檔案關聯的使用者，而每台機器關聯作用中一次。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明`fileAssociation`的部署使用的文字編輯器應用程式資訊清單的應用程式中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。 這個程式碼範例也包含[\<檔案 > 項目](../deployment/file-element-clickonce-application.md)所`defaultIcon`屬性。  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)