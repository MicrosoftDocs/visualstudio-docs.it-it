---
title: Verifica i sottotipi di un progetto in fase di esecuzione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 18049c034286c33247aec11aba77071daa93ef5c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Sottotipi di verifica della presenza di un progetto in fase di esecuzione
Un VSPackage che dipende da un sottotipo di progetto personalizzato deve includere logica per cercare in modo che sia possibile continuare normalmente se non è presente il sottotipo di sottotipo. La procedura seguente viene illustrato come verificare la presenza di un sottotipo specificato.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Per verificare la presenza di un sottotipo  
  
1.  Ottenere la gerarchia del progetto dagli oggetti di progetto e soluzione come un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto aggiungendo il codice seguente per il pacchetto VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Eseguire il cast della gerarchia per il <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfaccia.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Ottenere l'elenco di GUID del tipo di progetto richiamando il <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Controllare l'elenco per il GUID del sottotipo specificato.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Sottotipi di progetto](../extensibility/internals/project-subtypes.md)   
 [Sottotipi di progetto](../extensibility/internals/project-subtypes-design.md)   
 [Proprietà e metodi estesi dai sottotipi di progetto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)