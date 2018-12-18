---
title: Che contribuiscono a di dialogo Aggiungi nuovo elemento | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 923d95256a3ab0e63bdcf35c7ae38d70a117fa02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Che contribuiscono a di dialogo Aggiungi nuovo elemento
Un sottotipo di progetto può fornire una nuova directory completezza di elementi per il **Aggiungi nuovo elemento** la finestra di dialogo registrando **Aggiungi elemento** modelli sotto il `Projects` sottochiave del Registro di sistema.  
  
## <a name="registering-add-new-item-templates"></a>Registrazione template Aggiungi nuovo elemento  
 In questa sezione si trova in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** nel Registro di sistema. Si supponga che le voci del Registro di sistema sottostanti un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto aggregato da un sottotipo del ipotetica progetto. Le voci per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto sono elencati di seguito.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 Il `AddItemTemplates\TemplateDirs` sottochiave contiene le voci del Registro di sistema con il percorso della directory in cui gli elementi disponibili nel **Aggiungi nuovo elemento** la finestra di dialogo vengono inseriti.  
  
 L'ambiente vengono caricati automaticamente tutti il `AddItemTemplates` dati sotto il `Projects` sottochiave del Registro di sistema. Ciò può includere i dati per le implementazioni di progetto di base e i dati per i tipi di progetto specifico sottotipo. Il sottotipo di ogni progetto è identificato da un tipo di progetto `GUID`. Il sottotipo del progetto è possibile specificare che i set di un'alternativa di `Add Item` modelli devono essere utilizzati per un'istanza particolare del progetto tramite il supporto di `VSHPROPID_ AddItemTemplatesGuid` enumerazione da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementazione per restituire il GUID valore del sottotipo di progetto. Se `VSHPROPID_AddItemTemplatesGuid` proprietà non è specificata, il progetto di base viene utilizzato il GUID.  
  
 È possibile filtrare gli elementi di **Aggiungi nuovo elemento** la finestra di dialogo implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaccia sull'oggetto progetto sottotipo aggregator. Ad esempio, un sottotipo di progetto che implementa un progetto di database mediante l'aggregazione di un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del progetto, puoi filtrare la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementi specifici dal **Aggiungi nuovo elemento** implementando l'applicazione di filtri e nella finestra di dialogo attiva, è possibile aggiungere elementi di progetto specifici del database supportando `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Per ulteriori informazioni sul filtro e l'aggiunta di elementi di **Aggiungi nuovo elemento** la finestra di dialogo, vedere [aggiunta di elementi finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)