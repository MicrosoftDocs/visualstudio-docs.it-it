---
title: Strumento di Windows nel Registro di sistema | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d3277a4e24b12d409654548b5670a4d47fa9539
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="tool-windows-in-the-registry"></a>Finestre degli strumenti nel Registro di sistema
Pacchetti VSPackage che forniscono le finestre degli strumenti è necessario registrare con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] come strumento di provider di finestra. Finestre degli strumenti create utilizzando il modello di pacchetto di Visual Studio per tale scopo, per impostazione predefinita. Provider di finestra di strumento dispone di chiavi di registro di sistema che specificano gli attributi di visibilità, ad esempio dimensione predefinita della finestra dello strumento e la posizione, il GUID della finestra che viene utilizzato come il riquadro della finestra dello strumento e lo stile di ancoraggio.  
  
 Durante lo sviluppo, il provider di finestra degli strumenti gestita registra le finestre degli strumenti aggiungendo attributi al codice sorgente e quindi eseguire l'utility RegPkg.exe sull'assembly risultante. Per ulteriori informazioni, vedere [la registrazione di una finestra degli strumenti](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrazione dei provider di finestra dello strumento non gestito  
 Provider di finestra dello strumento non gestito è necessario registrare con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nella sezione ToolWindows del Registro di sistema. Nel seguente frammento di file con estensione reg Mostra come potrebbe essere registrata una finestra degli strumenti dinamiche:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 La prima chiave nell'esempio precedente, il numero di versione è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ad esempio 7.1 o 8.0, la sottochiave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} è il GUID del riquadro della finestra dello strumento (DynamicWindowPane) e il {di valore predefinito 01069cdd-95ce-4620-ac21-ddff6c57f012} è il GUID del pacchetto VSPackage che fornisce la finestra degli strumenti. Per una spiegazione delle sottochiavi Float e DontForceCreate, vedere [finestra strumento di configurazione](../extensibility/tool-window-display-configuration.md).  
  
 La seconda chiave facoltativa, ToolWindows\Visibility, specifica il GUID di comandi che richiedono la finestra degli strumenti deve essere reso visibile. In questo caso, sono non disponibili i comandi specificati. Per ulteriori informazioni, vedere [finestra strumento di configurazione](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)