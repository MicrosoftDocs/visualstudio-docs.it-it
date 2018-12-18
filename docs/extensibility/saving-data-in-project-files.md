---
title: Salvataggio dei dati nei file di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35514385a4ed1d28052ebb21d12ed0b053dd52dc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="saving-data-in-project-files"></a>Salvataggio di dati nei file di progetto
Un sottotipo di progetto può salvare e recuperare i dati specifici del sottotipo nel file di progetto. Il Framework di pacchetto gestito (MPF) sono disponibili due interfacce per eseguire questa attività:  
  
-   Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> interfaccia consente ai valori delle proprietà di accesso dal **MSBuild** sezione del file di progetto. I metodi forniti da <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> può essere chiamato da qualsiasi utente ogni volta che l'utente dovrà caricare o salvare i dati correlati di compilazione.  
  
-   Il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> è utilizzato per rendere persistenti i dati correlati non compilazione nel codice XML in formato libero. I metodi forniti da <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> vengono chiamati dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ogni volta che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve rendere persistenti i dati correlati non compilazione nel file di progetto.  
  
 Per ulteriori informazioni su come mantenere build e i dati correlati non compilazione, vedere [persistenza dei dati nel File di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="saving-and-retrieving-build-related-data"></a>Salvataggio e recupero di generazione dati correlati  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>Per salvare una compilazione i dati correlati nel file di progetto  
  
-   Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> per salvare un percorso completo del file di progetto.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Per recuperare la build dati correlati dal file di progetto  
  
-   Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> metodo per recuperare un percorso completo del file di progetto.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## <a name="saving-and-retrieving-non-build-related-data"></a>Salvataggio e il recupero non-generazione dati correlati  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>Per salvare non compilazione i dati correlati nel file di progetto  
  
1.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> metodo per determinare se un frammento XML è stato modificato dall'ultimo salvato nel file corrente.  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> per salvare i dati XML nel file di progetto.  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Per recuperare i dati correlati non compilazione nel file di progetto  
  
1.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> per inizializzare le proprietà di estensione di progetto e altri dati indipendenti dalla compilazione. Questo metodo viene chiamato se non sono presenti dati di configurazione XML presenti nel file di progetto.  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> metodo per caricare i dati XML dal file di progetto.  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
>  Tutti gli esempi di codice forniti in questo argomento sono parti di un esempio più esaustivo in [esempi di VSSDK](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Vedere anche  
 [Salvataggio permanente dei dati nel file di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)