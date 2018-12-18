---
title: Esposizione di eventi in Visual Studio SDK | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 74a9ff54d14b6212d0fc484acd2bd25fad18bb87
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Esposizione di eventi in Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]consente origine degli eventi tramite l'automazione. È consigliabile che l'origine degli eventi per progetti ed elementi di progetto.  
  
 Gli eventi vengono recuperati dai consumer di automazione dal <xref:EnvDTE.DTEClass.Events%2A> oggetto o <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). L'ambiente chiama `IDispatch::Invoke` utilizzando il `DISPATCH_METHOD` o `DISPATCH_PROPERTYGET` flag per restituire un evento.  
  
 Il processo seguente viene illustrato come vengono restituiti gli eventi specifici di VSPackage.  
  
1.  All'avvio dell'ambiente.  
  
2.  Legge dal Registro di sistema tutti i nomi di valore le chiavi di automazione, AutomationEvents e AutomationProperties di tutti i pacchetti VSPackage e archivia tali nomi in una tabella.  
  
3.  Chiama un consumer di automazione, in questo esempio, `DTE.Events.AutomationProjectsEvents` o `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  L'ambiente individua il parametro della stringa nella tabella e carica il pacchetto VSPackage corrispondente.  
  
5.  L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> utilizzando il nome passato nella chiamata; in questo esempio, AutomationProjectsEvents o AutomationProjectItemsEvents.  
  
6.  Il pacchetto VSPackage crea l'oggetto radice che dispone di metodi, ad esempio `get_AutomationProjectsEvents` e `get_AutomationProjectItemEvents` e quindi restituisce un puntatore IDispatch dell'oggetto.  
  
7.  L'ambiente chiama il metodo appropriato in base al nome passato nella chiamata di automazione.  
  
8.  Il `get_` metodo crea un altro oggetto eventi basata su IDispatch che implementa sia il `IConnectionPointContainer` interfaccia e `IConnectionPoint` l'interfaccia e restituisce un IDispatchpointer all'oggetto.  
  
 Per esporre un evento usando l'automazione, è necessario rispondere a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> ed espressioni di controllo per le stringhe che aggiunge al Registro di sistema. Nell'esempio di progetto di base, le stringhe sono "BscProjectsEvents" e "BscProjectItemsEvents".  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Voci del Registro di sistema dall'esempio di progetto di base  
 Questa sezione viene illustrato come aggiungere i valori di eventi di automazione nel Registro di sistema.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 "AutomationProjectEvents"="restituisce l'oggetto AutomationProjectEvents"  
  
 "AutomationProjectItemEvents"="restituisce l'oggetto AutomationProjectItemsEvents"  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|Predefinito (@)|REG_SZ|Non usato|Non usato. È possibile utilizzare il campo dei dati per la documentazione.|  
|AutomationProjectsEvents|REG_SZ|Nome dell'oggetto evento.|Solo il nome della chiave è rilevante. È possibile utilizzare il campo dei dati per la documentazione.<br /><br /> In questo esempio proviene dall'esempio di progetto di base.|  
|AutomationProjectItemEvents|REG_SZ|Nome dell'oggetto evento|Solo il nome della chiave è rilevante. È possibile utilizzare il campo dei dati per la documentazione.<br /><br /> In questo esempio proviene dall'esempio di progetto di base.|  
  
 Quando uno degli oggetti evento vengono richiesti da un consumer di automazione, creare un oggetto principale che dispone di metodi per qualsiasi evento che supporta il pacchetto VSPackage. L'ambiente chiama appropriata `get_` metodo su questo oggetto. Ad esempio, se `DTE.Events.AutomationProjectsEvents` viene chiamato, il `get_AutomationProjectsEvents` metodo sull'oggetto radice viene richiamato.  
  
 ![Eventi nei progetti Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Modello di automazione per gli eventi  
  
 La classe `CProjectEventsContainer` rappresenta l'oggetto di origine per BscProjectsEvents, mentre `CProjectItemsEventsContainer` rappresenta l'oggetto di origine per BscProjectItemsEvents.  
  
 Nella maggior parte dei casi, è necessario restituire un nuovo oggetto per ogni richiesta perché la maggior parte degli oggetti evento che accettano un oggetto filtro. Quando si attiva l'evento, controllare il filtro per verificare che il gestore eventi viene chiamato.  
  
 AutomationEvents.h e AutomationEvents.cpp contengono le dichiarazioni e implementazioni delle classi nella tabella seguente.  
  
|Classe|Descrizione|  
|-----------|-----------------|  
|`CAutomationEvents`|Implementa un oggetto radice eventi recuperato il `DTE.Events` oggetto.|  
|`CProjectsEventsContainer` e `CProjectItemsEventsContainer`|Implementare gli oggetti di origine di eventi che attivano eventi corrispondenti.|  
  
 Esempio di codice seguente viene illustrato come rispondere a una richiesta per un oggetto evento.  
  
```cpp  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 Nel codice precedente, `g_wszAutomationProjects` è il nome della raccolta di progetti ("FigProjects"), `g_wszAutomationProjectsEvents` ("FigProjectsEvents") e `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") sono i nomi degli eventi nei progetti e gli eventi originati da elementi di progetto del Implementazione di VSPackage.  
  
 Gli oggetti evento vengono recuperati dalla stessa posizione centrale, il `DTE.Events` oggetto. In questo modo, tutti gli oggetti evento vengono raggruppati in modo che un utente finale non è necessario selezionare l'intero modello a oggetti per trovare un evento specifico. Ciò consente inoltre di fornire oggetti VSPackage specifici, invece di dover implementare il codice personalizzato per gli eventi a livello di sistema. Tuttavia, per l'utente finale, che deve trovare un evento per il `ProjectItem` interfaccia, non è immediatamente chiaro da in cui viene recuperato l'oggetto evento.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Esempi di VSSDK](http://aka.ms/vs2015sdksamples)