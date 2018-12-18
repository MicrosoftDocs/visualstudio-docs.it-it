---
title: Esposizione di tipi di finestre di progettazione visiva | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a85648a95a6651ff62f50b2361b07feba9a58b47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-types-to-visual-designers"></a>Esposizione di tipi di finestre di progettazione visiva
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deve avere accesso alle definizioni di classe e il tipo in fase di progettazione per visualizzare una finestra di progettazione. Le classi vengono caricate da un set predefinito di assembly che includono il set completo di dipendenze del progetto corrente (riferimenti e le relative dipendenze). È inoltre necessario per finestre di progettazione visiva per accedere alle classi e tipi definiti nei file generati da strumenti personalizzati.  
  
 Il [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemi di progetto forniscono supporto per l'accesso alle classi generate e tipi tramite temporaneo portabile file eseguibili (file PE temporanei). Qualsiasi file generato da uno strumento personalizzato può essere compilato in un assembly temporaneo in modo che i tipi possono essere caricati da tali assembly ed esposti alle finestre di progettazione. L'output di ogni strumento personalizzato viene compilato in un file PE temporaneo separato e l'esito positivo o negativo della compilazione temporanea dipende solo se il file generato può essere compilato. Anche se un progetto non venga compilato nel suo complesso, singoli file PE temporanei può essere ancora disponibili nelle finestre di progettazione.  
  
 Il sistema di progetto fornisce supporto completo per il rilevamento delle modifiche al file di output di uno strumento personalizzato, purché queste modifiche sono il risultato dell'esecuzione dello strumento personalizzato. Ogni volta che viene eseguito lo strumento personalizzato, viene generato un nuovo file PE temporaneo e vengono inviate le notifiche appropriate per le finestre di progettazione.  
  
> [!NOTE]
>  Poiché il file eseguibile generazione programma temporaneo avviene in background, errori non vengono segnalati all'utente se la compilazione ha esito negativo.  
  
 Strumenti personalizzati in grado di sfruttano i vantaggi del supporto PE temporaneo devono rispettare le regole seguenti:  
  
-   `GeneratesDesignTimeSource`deve essere impostato su 1 nel Registro di sistema.  
  
     Alcuna compilazione di file eseguibile del programma non viene eseguito senza questa impostazione.  
  
-   Il codice generato deve essere nella stessa lingua, come l'impostazione di progetti globale.  
  
     Il file PE temporaneo viene compilato indipendentemente dal report che lo strumento personalizzato come estensione nella richiesta <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> purché `GeneratesDesignTimeSource` è impostato su 1 nel Registro di sistema. L'estensione non è necessario essere jsl; con estensione cs o vb può essere qualsiasi estensione.  
  
-   Il codice generato dallo strumento personalizzato deve essere valido e deve essere compilato in proprio utilizzando solo il set di riferimenti presenti nel progetto al momento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> al termine dell'esecuzione.  
  
     Quando viene compilato un file PE temporaneo, l'unico file di origine fornito al compilatore è l'output dello strumento personalizzato. Pertanto, uno strumento personalizzato che utilizza un file PE temporaneo necessario generare i file di output che possono essere compilati in modo indipendente da altri file nel progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione all'oggetto BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementazione di generatori di File singolo](../../extensibility/internals/implementing-single-file-generators.md)   
 [Registrazione di generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)