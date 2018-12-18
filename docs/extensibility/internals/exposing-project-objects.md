---
title: Esposizione di oggetti di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4eaa2a5e8c5c153698069084b9f0cfe406cad7db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="exposing-project-objects"></a>Esposizione di oggetti di progetto
Tipi di progetto personalizzato è possono fornire oggetti di automazione per consentire l'accesso al progetto utilizzando le interfacce di automazione. Ogni tipo di progetto deve fornire lo standard <xref:EnvDTE.Project> oggetto di automazione che è accessibile da <xref:EnvDTE.Solution>, che contiene una raccolta di tutti i progetti aperti nell'IDE. È previsto che ogni elemento del progetto devono essere esposte da un <xref:EnvDTE.ProjectItem> oggetto cui si accede con `Project.ProjectItems`. Oltre a questi oggetti di automazione standard, i progetti è possono scegliere di oggetti di automazione specifico.  
  
 È possibile creare oggetti di automazione a livello di radice personalizzati che è possibile accedere ad associazione tardiva dall'oggetto DTE radice utilizzando `DTE.<customeObjectName>` o `DTE.GetObject("<customObjectName>")`. Ad esempio, Visual C++ Crea raccolta di progetti specifici del progetto di C++ denominato "VCProjects" che è possibile accedere utilizzando DTE. VCProjects oppure DTE. GetObject("VCProjects"). È inoltre possibile creare un Project. Object, che è univoco per il tipo di progetto, un CodeModel, che è possibile eseguire query per l'oggetto più derivato, un oggetto ProjectItem, che espone un FileCodeModel e ProjectItem. Object.  
  
 È una convenzione comune per i progetti per esporre una raccolta di progetti personalizzati, specifici del progetto. Ad esempio, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] crea una raccolta di progetti specifici di C++ che è quindi possibile accedere utilizzando `DTE.VCProjects` o `DTE.GetObject("VCProjects")`. È inoltre possibile creare un `Project.Object`, che è univoco per il tipo di progetto, un `Project.CodeModel`, che è possibile eseguire query per un oggetto più derivato, un `ProjectItem`, che espone `ProjectItem.Object`e un `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Per contribuire a un oggetto VSPackage specifico per un progetto  
  
1.  Aggiungere le chiavi appropriate al file. pkgdef di un VSPackage.  
  
     Ad esempio, ecco le impostazioni. pkgdef per il progetto in linguaggio C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementare il codice di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (metodo), come nell'esempio seguente.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     Nel codice, `g_wszAutomationProjects` è il nome della raccolta di progetti. Il `GetAutomationProjects` metodo crea un oggetto che implementa il `Projects` interfaccia e restituisce un `IDispatch` puntatore all'oggetto chiamante, come illustrato nell'esempio di codice seguente.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     È consigliabile scegliere un nome univoco per l'oggetto di automazione. Conflitti di nomi sono imprevedibili e conflitti di causano un nome di oggetto in conflitto essere eliminati in modo arbitrario se più tipi di progetto usano lo stesso nome. È necessario includere il proprio nome azienda o alcuni aspetti del relativo nome di prodotto nel nome dell'oggetto di automazione univoco.  
  
     L'oggetto personalizzato `Projects` oggetto della raccolta è un punto di ingresso pratici per la parte rimanente del modello di automazione del progetto. L'oggetto di progetto è accessibile anche dal <xref:EnvDTE.Solution> raccolta di progetti. Dopo aver creato le voci del Registro di sistema e di codice appropriate che forniscono i consumer con `Projects` raccolta di oggetti, l'implementazione deve fornire rimanenti oggetti standard per il modello di progetto. Per ulteriori informazioni, vedere [progetto di modellazione](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>