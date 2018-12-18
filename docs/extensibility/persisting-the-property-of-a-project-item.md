---
title: Salvare in modo permanente la proprietà di un elemento di progetto | Documenti Microsoft
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
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="persisting-the-property-of-a-project-item"></a>Salvare in modo permanente la proprietà di un elemento di progetto
È consigliabile mantenere una proprietà che aggiungere un elemento di progetto, ad esempio l'autore di un file di origine. È possibile farlo archiviando la proprietà nel file di progetto.

 Il primo passaggio per mantenere una proprietà in un file di progetto è per ottenere la gerarchia del progetto come un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia. È possibile ottenere questa interfaccia tramite l'automazione oppure utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Una volta ottenuto l'interfaccia, è possibile utilizzare, per determinare quale elemento del progetto è attualmente selezionata. Dopo aver creato l'ID di elemento di progetto, è possibile utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> per aggiungere la proprietà.

 Nelle procedure seguenti, mantenere la proprietà VsPkg.cs `Author` con il valore `Tom` nel file di progetto.

### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Per ottenere la gerarchia del progetto con l'oggetto DTE

1.  Aggiungere il pacchetto VSPackage nel codice seguente:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Per mantenere la proprietà di elemento di progetto con l'oggetto DTE

1.  Il codice di cui il metodo nella procedura precedente, aggiungere il codice seguente:

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

### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Per ottenere la gerarchia del progetto mediante IVsMonitorSelection

1.  Aggiungere il pacchetto VSPackage nel codice seguente:

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

### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Per rendere persistente la proprietà di elemento di progetto selezionato, data la gerarchia del progetto

1.  Il codice di cui il metodo nella procedura precedente, aggiungere il codice seguente:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-verify-that-the-property-is-persisted"></a>Per verificare che la proprietà viene mantenuta.

1.  Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e quindi aprire o creare una soluzione.

2.  Selezionare il progetto elemento VsPkg.cs in **Esplora**.

3.  Utilizzare un punto di interruzione o altrimenti determinare che viene caricato il pacchetto VSPackage e che venga eseguito SetItemAttribute.

    > [!NOTE]
    > È possibile utilizzare autoload un pacchetto VSPackage nel contesto dell'interfaccia utente <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Per ulteriori informazioni, vedere [VSPackage durante il caricamento](../extensibility/loading-vspackages.md).

4.  Chiudi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e quindi aprire il file di progetto nel blocco note. Verrà visualizzato il \<autore > tag con il valore Tom, come indicato di seguito:

    ```xml
    <Compile Include="VsPkg.cs">
        <Author>Tom</Author>
    </Compile>
    ```

## <a name="see-also"></a>Vedere anche

- [Strumenti personalizzati](../extensibility/internals/custom-tools.md)