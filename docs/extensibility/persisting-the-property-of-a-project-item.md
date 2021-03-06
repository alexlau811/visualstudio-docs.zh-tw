---
title: 保存的專案項目屬性 |Microsoft 文件
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6b0bc529e01d8ef34b6959b98d773857000ec1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="persisting-the-property-of-a-project-item"></a>保存專案項目的屬性
若要保存您加入專案項目，例如作者的原始程式檔的屬性。 您可以將屬性儲存在專案檔。

 屬性保存在專案檔的第一個步驟是取得做為專案的階層架構<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面。 您可以取得此介面，使用自動化，或使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>。 一旦您取得的介面，您可以使用它來判斷目前選取的專案項目。 專案項目 ID 之後，您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>以加入屬性。

 在下列程序中，您將保存 VsPkg.cs 屬性`Author`值`Tom`專案檔中。

### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>若要取得 DTE 物件的專案階層

1.  將下列程式碼加入至您的 VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>保存與 DTE 物件的專案項目屬性

1.  將下列程式碼加入至先前的程序中的方法中指定的程式碼：

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>若要取得使用 IVsMonitorSelection 專案階層架構

1.  將下列程式碼加入至您的 VSPackage:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

2.

### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>將選取的專案項目屬性保存，指定專案階層架構

1.  將下列程式碼加入至先前的程序中的方法中指定的程式碼：

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-verify-that-the-property-is-persisted"></a>若要確認此屬性會保存

1.  啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]再開啟或建立的方案。

2.  選取的專案項目中的 VsPkg.cs**方案總管 中**。

3.  使用中斷點或另外判斷已載入 VSPackage 和 SetItemAttribute 執行。

    > [!NOTE]
    > 您可以自動載入 VSPackage UI 內容中<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>。 如需詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。

4.  關閉[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，然後在 [記事本] 中開啟專案檔。 您應該會看到\<作者 > 標記值 Tom，如下：

    ```xml
    <Compile Include="VsPkg.cs">
        <Author>Tom</Author>
    </Compile>
    ```

## <a name="see-also"></a>另請參閱

- [自訂工具](../extensibility/internals/custom-tools.md)