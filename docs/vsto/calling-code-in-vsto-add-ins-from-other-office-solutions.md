---
title: 從其他 Office 方案呼叫 VSTO 增益集的程式碼
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 982fa23fa933bbade63222b78d677b88680601fc
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>從其他 Office 方案呼叫 VSTO 增益集的程式碼
  您可以將 VSTO 增益集中的物件公開給其他方案 (包括其他 Microsoft Office 方案)。 如果您想要讓其他方案也能使用 VSTO 增益集提供的服務，這就很有用。 例如，如果您有在 VSTO 增益集會計算 Web 服務的財務資料的 Microsoft Office excel，其他方案可以藉由呼叫 Excel VSTO 增益集在執行階段執行這些計算。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 這個程序包含兩個主要步驟：  
  
-   在您的 VSTO 增益集中，將物件公開給其他方案。  
  
-   在其他方案中，存取您的 VSTO 增益集所公開的物件，並呼叫該物件的成員。  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>類型可以在增益集中呼叫程式碼的方案  
 您可以將 VSTO 增益集的下列類型的方案中的物件公開：  
  
-   和 VSTO 增益集載入到相同應用程式處理序之文件內的 Visual Basic for Applications (VBA) 程式碼。  
  
-   和 VSTO 增益集載入到相同應用程式處理序的文件層級自訂。  
  
-   使用 Visual Studio 中的 Office 專案範本建立的其他 VSTO 增益集。  
  
-   COM VSTO 增益集 (即直接實作 <xref:Extensibility.IDTExtensibility2> 介面的 VSTO 增益集)。  
  
-   任何在與 VSTO 增益集不同的處理序中執行的方案 (這類方案也稱為 *「跨處理序用戶端」*(Out-Of-Process Client))。 這包括將 Office 應用程式自動化的應用程式 (例如 Windows Forms 或主控台應用程式)，以及在不同處理序中載入的 VSTO 增益集。  
  
## <a name="expose-objects-to-other-solutions"></a>公開給其他方案物件  
 若要將您 VSTO 增益集中的物件公開給其他方案，請在 VSTO 增益集中執行下列步驟：  
  
1.  定義您要公開給其他方案的類別。  
  
2.  覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 類別中的 `ThisAddIn` 方法。 傳回您要公開給其他方案之類別的執行個體。  
  
### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>您想要公開給其他方案的類別定義  
 您要公開的類別至少必須是公用的、其 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性必須設為 **true**，而且必須公開 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) 介面。  
  
 公開 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) 介面的建議方法是執行下列步驟：  
  
1.  定義介面，這個介面宣告您要公開給其他方案的成員。 您可以在 VSTO 增益集專案中定義這個介面。 不過，如果您要將類別公開給非 VBA 方案，可以在個別的類別庫專案中定義這個介面，讓呼叫您 VSTO 增益集的方案不需參考您的 VSTO 增益集專案，就可以參考這個介面。  
  
2.  將 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性套用至這個介面，並將這個屬性設為 **true**。  
  
3.  修改您的類別以實作這個介面。  
  
4.  套用<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性加入至類別，並將此屬性設**無**值<xref:System.Runtime.InteropServices.ClassInterfaceType>列舉型別。  
  
5.  如果您想將此類別公開給跨處理序用戶端，則您可能需要執行下列作業：  
  
    -   從 <xref:System.Runtime.InteropServices.StandardOleMarshalObject>衍生類別。 如需詳細資訊，請參閱[公開給跨處理序用戶端類別](#outofproc)。  
  
    -   在您定義介面的專案中設定 [註冊 COM Interop]  屬性。 這個屬性是您想要讓用戶端使用早期繫結來呼叫 VSTO 增益集時，才需要。  
  
 下列程式碼範例示範 `AddInUtilities` 類別，該類別具有其他方案可以呼叫的 `ImportData` 方法。 若要查看完整的逐步解說內容中的這段程式碼，請參閱[逐步解說： 從 VBA 呼叫 VSTO 增益集中的程式碼](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)。  
  
 [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
 [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="expose-classes-to-vba"></a>公開給 VBA 的類別  
 當您執行上述步驟時，VBA 程式碼只能呼叫您在介面中宣告的方法。 VBA 程式碼無法呼叫您類別中的其他任何方法，包括您的類別從 <xref:System.Object>等基底類別取得的方法。  
  
 您也可以公開[IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)介面，藉由設定<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性 AutoDispatch 或 AutoDual 值<xref:System.Runtime.InteropServices.ClassInterfaceType>列舉型別。 公開的介面時，如果您沒有宣告中的個別介面的方法。 不過，VBA 程式碼可以呼叫您類別中的任何公用和非靜態方法，包括從 <xref:System.Object>等基底類別取得的方法。 此外，使用早期繫結的跨處理序用戶端無法呼叫您的類別。  
  
###  <a name="outofproc"></a> 公開給跨處理序用戶端類別  
 如果您要將 VSTO 增益集中的類別公開給跨處理序用戶端，您應該從 <xref:System.Runtime.InteropServices.StandardOleMarshalObject> 衍生類別，以確保跨處理序用戶端可以呼叫所公開的 VSTO 增益集物件。 否則，當嘗試在跨處理序用戶端中取得所公開的物件執行個體時，可能會意外失敗。  
  
 此失敗是因為物件模型的 Office 應用程式的所有呼叫必須都對主要 UI 執行緒，但從跨處理序用戶端對您物件的呼叫將送任意 RPC （遠端程序呼叫） 執行緒。 .NET Framework 中的 COM 封送處理機制並不會切換執行緒，而是會嘗試在連入 RPC 執行緒 (而不是主要 UI 執行緒) 上封送處理對您物件的呼叫。 如果您的物件是衍生自 <xref:System.Runtime.InteropServices.StandardOleMarshalObject>之類別的執行個體，則對您物件的連入呼叫會自動封送處理至當初用以建立已公開物件的執行緒，而該執行緒會成為主應用程式的主要 UI 執行緒。  
  
 如需在 Office 方案中使用執行緒的詳細資訊，請參閱[Office 中的執行緒支援](../vsto/threading-support-in-office.md)。  
  
### <a name="override-the-requestcomaddinautomationservice-method"></a>覆寫 RequestComAddInAutomationService 方法  
 下列程式碼範例示範如何在您的 VSTO 增益集中覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 類別中的 `ThisAddIn` 。 這個範例假設您已定義類別，名為`AddInUtilities`您想要公開給其他方案。 若要查看完整的逐步解說內容中的這段程式碼，請參閱[逐步解說： 從 VBA 呼叫 VSTO 增益集中的程式碼](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)。  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 載入 VSTO 增益集時， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會呼叫 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 方法。 執行階段會將傳回的物件指派給代表 VSTO 增益集之 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 物件的 <xref:Microsoft.Office.Core.COMAddIn> 屬性。 這個 <xref:Microsoft.Office.Core.COMAddIn> 物件可供其他 Office 方案以及將 Office 自動化的方案使用。  
  
## <a name="access-objects-from-other-solutions"></a>從其他方案存取物件  
 若要呼叫您 VSTO 增益集中公開的物件，請在用戶端方案中執行下列步驟：  
  
1.  取得代表已公開 VSTO 增益集的 <xref:Microsoft.Office.Core.COMAddIn> 物件。 用戶端可以使用主 Office 應用程式的物件模型中的 `Application.COMAddIns` 屬性，存取所有可用的 VSTO 增益集。  
  
2.  存取 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 物件的 <xref:Microsoft.Office.Core.COMAddIn> 屬性。 這個屬性會傳回 VSTO 增益集中已公開的物件。  
  
3.  呼叫已公開物件的成員。  
  
 對於 VBA 用戶端和非 VBA 用戶端，您使用 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 屬性之傳回值的方式會不同。 對於跨處理序用戶端，還需要其他程式碼才能避免可能的競爭情形。  
  
### <a name="access-objects-from-vba-solutions"></a>從 VBA 方案存取物件  
 下列程式碼範例示範如何使用 VBA 呼叫 VSTO 增益集所公開的方法。 這個 VBA 巨集會呼叫名為`ImportData`VSTO 增益集中名為定義**ExcelImportData**。 若要查看完整的逐步解說內容中的這段程式碼，請參閱[逐步解說： 從 VBA 呼叫 VSTO 增益集中的程式碼](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)。  
  
```vb
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="access-objects-from-non-vba-solutions"></a>從非 VBA 方案存取物件  
 在非 VBA 方案中，您必須將 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 屬性值轉型為方案所實作的介面，然後才能在介面物件上呼叫已公開的方法。 下列程式碼範例示範如何從使用 Visual Studio 中的 Office Developer Tools 所建立的不同 VSTO 增益集呼叫 `ImportData` 方法。  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 在這個範例中，如果您嘗試將 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> 屬性的值轉型為 `AddInUtilities` 類別 (而不是 `IAddInUtilities` 介面)，則程式碼會擲回 <xref:System.InvalidCastException>。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 VSTO 增益集](../vsto/programming-vsto-add-ins.md)   
 [逐步解說： 從 VBA 在 VSTO 增益集中呼叫程式碼](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [使用擴充性介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  