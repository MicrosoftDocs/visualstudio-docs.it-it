---
title: 'Procedura: registrare i tipi di File Editor | Documenti Microsoft'
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4ac67139de317c15d4e85be43f7dace132373257
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-register-editor-file-types"></a>Procedura: registrare i tipi di File dell'Editor
È il modo più semplice per registrare i tipi di file di editor utilizzando gli attributi di registrazione forniti come parte di [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] classi framework (gestito MPF) del pacchetto gestito. Se si implementa il pacchetto in nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], è anche possibile scrivere uno script del Registro di sistema che registra l'editor e le estensioni associate.

## <a name="registration-using-mpf-classes"></a>Registrazione utilizzo delle classi MPF

#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Per registrare i tipi di file di editor utilizzando le classi MPF

1.  Fornire il <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> classe con i parametri appropriati per l'editor nella classe di un VSPackage.

    ```
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",
         TemplateDir = "..\\..\\Templates",
         NameResourceID = 106)]
    ```

     Dove ". Esempio"è l'estensione è registrata per questo editor e"32"è il livello di priorità.

     Il `projectGuid` è il GUID per i tipi di file esterno, definiti <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Viene fornito il tipo di file esterni, in modo che il file risultante non deve essere una parte del processo di compilazione.

     `TemplateDir` rappresenta la cartella che contiene i file di modello che sono inclusi con l'esempio di editor di base gestito.

     `NameResourceID` è definito nel file del progetto BasicEditorUI Resources.h e identifica l'editor come "My Editor".

2.  Eseguire l'override del metodo <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.

     Nell'implementazione del <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo, chiamare il <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> (metodo) e passare l'istanza di una factory dell'editor, come illustrato di seguito.

    ```csharp
    protected override void Initialize()
    {
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,
        "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
           //Create Editor Factory
        editorFactory = new EditorFactory(this);
        base.RegisterEditorFactory(editorFactory);
    }
    ```

     Questo passaggio registra la factory editor sia le estensioni di file dell'editor.

3.  Annullare la registrazione il factory editor.

     Factory editor viene automaticamente annullata quando viene eliminato il pacchetto VSPackage. Se l'oggetto factory editor implementa il <xref:System.IDisposable> interfaccia, il relativo `Dispose` metodo viene chiamato dopo la factory è stata annullata la registrazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="registration-using-a-registry-script"></a>Registrazione tramite uno Script del Registro di sistema
 Registrazione di factory editor e tipi di file in nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] viene eseguita tramite uno script del Registro di sistema di scrivere nel Registro di sistema di windows, come illustrato nell'esempio seguente.

### <a name="to-register-editor-file-types-using-a-registry-script"></a>Per registrare i tipi di file di editor utilizzando uno script del Registro di sistema

1.  Nello script del Registro di sistema, definire la factory editor e la factory editor stringa GUID come illustrato nel `GUID_BscEditorFactory` sezione dello script del Registro di sistema seguente. Inoltre, definire l'estensione e la priorità dell'estensione di editor:

    ```
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0

            LogicalViews
            {
                val %LOGVIEWID_TextView% = s ''
            }

            OpenWithEntries
            {
            }

            Extensions            {                val rtf = d 50            }
        }
    }
    ```

     L'estensione del file dell'editor in questo esempio è stato identificato come "RTF" e la priorità è "50". Le stringhe GUID sono definite nel file Resource. h del progetto di esempio BscEdit.

2.  Registrare il pacchetto VSPackage.

3.  Registrare la factory editor.

     La factory editor viene registrata nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementazione.

    ```cpp
    // create editor factory.
    if (m_srpEdFact == NULL)
    {
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;
        if (NULL == pEdFact)
          return E_OUTOFMEMORY;

        if (!pEdFact->FInit(this))
          return E_UNEXPECTED;

        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()
    }
    // Query service for IVsRegisterEditors, register the editor factory
    CComPtr<IVsRegisterEditors> srpRegEd;
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))
      {
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,
                      m_srpEdFact, &m_dwEditorCookie)))
          {
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));
            return E_FAIL;
          }
      }
        return S_OK;
    }
    ```

     Le stringhe GUID sono definite nel file Resource. h del progetto BscEdit.