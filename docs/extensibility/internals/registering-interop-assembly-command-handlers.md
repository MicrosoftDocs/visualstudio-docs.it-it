---
title: "Registrazione di gestori di comando di Assembly di interoperabilità | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a25f8adc91efe9d9e8b96079b4fe2e35145abf25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrazione di gestori di comando di Assembly di interoperabilità
Un VSPackage è necessario registrare con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modo che l'ambiente di sviluppo integrato (IDE) consente di indirizzare i relativi comandi correttamente.  
  
 Il Registro di sistema può essere aggiornato mediante la modifica manuale o tramite un file di registrazione (con estensione RGS). Per ulteriori informazioni, vedere [la creazione di script di registrazione](/cpp/atl/creating-registrar-scripts).  
  
 Il Framework di pacchetto gestito (MPF) fornisce questa funzionalità tramite la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.  
  
 [Riferimento alla tabella formato comando](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f) risorse si trovano in non gestite satellite DLL dell'interfaccia utente.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Registrazione del gestore del comando di un VSPackage  
 Un VSPackage che agisce come un gestore per l'interfaccia utente (UI)-i comandi di base richiede una voce del Registro di sistema denominata dopo il pacchetto VSPackage `GUID`. Questa voce del Registro di sistema specifica il percorso del file di risorse di VSPackage dell'interfaccia utente e la risorsa di menu all'interno del file. La voce del Registro di sistema stesso si trova in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<versione >*\Menus, in cui  *\<versione >* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ad esempio 9.0.  
  
> [!NOTE]
>  Il percorso radice dell'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >* può essere sostituito con un'alternativa radice quando il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell viene inizializzata. Per ulteriori informazioni sul percorso radice, vedere [l'installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>La voce del Registro di sistema di risorse CTMENU  
 La struttura della voce del Registro di sistema è:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> è il `GUID` del pacchetto VSPackage nel formato {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Informazioni sulle risorse >* è costituito da tre elementi, separati da virgole. Questi elementi sono, in ordine:  
  
 \<*Percorso DLL risorsa*>, \< *ID risorsa Menu*>, \< *versione Menu*>  
  
 Nella tabella seguente vengono descritti i campi di \< *informazioni sulle risorse*>.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|\<*Percorso DLL di risorse*>|Si tratta del percorso completo per la DLL che contiene la risorsa menu risorse o questo viene lasciato vuoto, che indica che la risorsa del VSPackage DLL da utilizzare (come specificato nella sottochiave pacchetti in cui è stato registrato il pacchetto VSPackage stesso).<br /><br /> È facoltativa per lasciare vuoto questo campo.|  
|\<*ID di risorsa di menu*>|Questo è l'ID della risorsa di `CTMENU` risorsa che contiene tutti gli elementi dell'interfaccia utente per il pacchetto VSPackage come compilato da un [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) file.|  
|\<*Versione di menu*>|Si tratta di un numero utilizzato come una versione per il `CTMENU` risorse. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Questo valore viene utilizzato per determinare se è necessario unire di nuovo il contenuto del `CTMENU` risorsa con la cache di tutti `CTMENU` risorse. Un unire di nuovo viene attivata eseguendo il comando di devenv il programma di installazione.<br /><br /> Questo valore deve essere inizialmente impostato su 1 e incrementato dopo ogni modifica nel `CTMENU` risorse e prima di unire di nuovo.|  
  
### <a name="example"></a>Esempio  
 Di seguito è riportato un esempio di un paio di voci di risorsa:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)