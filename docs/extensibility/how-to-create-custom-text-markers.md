---
title: 'Procedura: creare marcatori di testo personalizzato | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5c44a507cc291b203fc9ba330b248a854f61b81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-custom-text-markers"></a>Procedura: creare marcatori di testo personalizzato
Se si desidera creare un indicatore di testo personalizzato per enfatizzare o organizzare il codice, è necessario eseguire i passaggi seguenti:  
  
-   Registrare il nuovo indicatore di testo, in modo che possano accedervi altri strumenti  
  
-   Fornire un'implementazione predefinita e la configurazione dell'indicatore di testo  
  
-   Creare un servizio che può essere utilizzato da altri processi per rendere utilizzare dell'indicatore di testo  
  
 Per informazioni dettagliate su come applicare un indicatore di testo a un'area di codice, vedere [procedura: utilizzare testo marcatori](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Per registrare un marcatore personalizzato  
  
1.  Creare una voce del Registro di sistema come segue:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >*\Text Editor\External marcatori\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >*è un `GUID` utilizzato per identificare il marcatore da aggiungere  
  
     *\<Versione >* è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ad esempio 8.0  
  
     *\<PackageGUID >* è il GUID del pacchetto VSPackage implementa l'oggetto di automazione.  
  
    > [!NOTE]
    >  Il percorso radice dell'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >* può essere sostituita con una radice alternativa, quando viene inizializzata la shell di Visual Studio, per ulteriori informazioni, vedere [Della riga di comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Creare quattro valori sotto HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >*\Text Editor\External marcatori\\*\<MarkerGUID >*  
  
    -   (Predefinito)  
  
    -   Service  
  
    -   DisplayName  
  
    -   Pacchetto  
  
    -   `Default` è una voce facoltativa di tipo REG_SZ. Se impostato, il valore della voce è una stringa che contiene alcune informazioni di identificazione utile, ad esempio "Custom indicatore di testo".  
  
    -   `Service` è una voce di tipo REG_SZ contenente la stringa del GUID del servizio che fornisce il marcatore di testo personalizzato da proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Il formato è {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName` è una voce di tipo REG_SZ contenente l'ID della risorsa del nome dell'indicatore di testo personalizzato. Il formato è #YYYY.  
  
    -   `Package` è una voce del tipo REG_SZ contenente il `GUID` di VSPackage che fornisce il servizio elencato nel servizio. Il formato è {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Per creare un indicatore di testo personalizzato  
  
1.  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     L'implementazione di questa interfaccia definisce il comportamento e l'aspetto del tipo di marcatore personalizzata.  
  
     Questa interfaccia viene chiamata quando  
  
    1.  Un utente avvia l'IDE per la prima volta.  
  
    2.  Un utente seleziona il **predefinite** in corrispondenza di **tipi di carattere e colori** pagina delle proprietà nel **ambiente** cartella, nel riquadro a sinistra del  **Opzioni** la finestra di dialogo viene ottenuta la **strumenti** menu dell'IDE.  
  
2.  Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> metodo, specificando che `IVsPackageDefinedTextMarkerType` implementazione deve essere restituita in base al tipo di marcatore GUID specificato nella chiamata al metodo.  
  
     L'ambiente chiama questo momento il primo metodo, viene creato il tipo di marcatore personalizzata e specifica un GUID che identifica il tipo di marcatore personalizzata.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Per indicare il tipo di marcatore come servizio  
  
1.  Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> metodo per <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> viene restituito.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> metodo, specificando il GUID che identifica il servizio di tipo marcatore personalizzata e fornisce un puntatore all'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaccia. Il <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementazione deve restituire un puntatore all'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interfaccia.  
  
     Cookie univoco che identifica il servizio viene restituito. In un secondo momento, è possibile utilizzare il cookie di revocare il servizio di tipo marcatore personalizzata chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaccia che specifica il valore del cookie.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)   
 [Procedura: utilizzare gli indicatori di testo](../extensibility/how-to-use-text-markers.md)