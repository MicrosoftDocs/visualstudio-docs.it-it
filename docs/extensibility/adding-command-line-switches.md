---
title: Aggiunta della riga di comando | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d686e7b68e790c419679bf495bf08ad4cd4807e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="adding-command-line-switches"></a>Aggiunta della riga di comando
È possibile aggiungere opzioni della riga di comando che si applicano a VSPackage durante l'esecuzione di devenv.exe. Utilizzare <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> per dichiarare il nome dell'opzione e le relative proprietà. In questo esempio viene aggiunto il commutatore MySwitch per una sottoclasse di VSPackage denominato **AddCommandSwitchPackage** senza argomenti e con il pacchetto VSPackage caricati automaticamente.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 I parametri denominati vengono visualizzati nella tabella seguente  
  
 Argomenti  
 Il numero di argomenti per il commutatore. Può essere "*", o un elenco di argomenti.  
  
 DemandLoad  
 Caricare il pacchetto VSPackage automaticamente se è impostato su 1, altrimenti è impostato su 0.  
  
 HelpString  
 L'ID della Guida stringa o una risorsa della stringa da visualizzare con **devenv /?**.  
  
 nome  
 Il commutatore.  
  
 PackageGuid  
 Il GUID del pacchetto.  
  
 Il primo valore degli argomenti è in genere 0 o 1. Un valore speciale "*" può essere utilizzato per indicare che tutto il resto della riga di comando è costituito dall'argomento. Questo può essere utile per scenari in cui un utente deve passare una stringa di comando del debugger di debug.  
  
 Il valore DemandLoad sarà `true` (1) o `false` (0) indica che il pacchetto VSPackage deve essere caricato automaticamente.  
  
 Il valore HelpString è l'ID risorsa della stringa che viene visualizzato nella finestra di devenv /? Visualizzazione della Guida. Questo valore deve essere nel formato "#nnn" dove nnn è un numero intero. Il valore di stringa nel file di risorse deve terminare con un carattere di nuova riga.  
  
 Il valore del nome è il nome del commutatore.  
  
 Il valore PackageGuid è il GUID del pacchetto che implementa questa opzione è attivata. L'IDE utilizza questo GUID per trovare il pacchetto VSPackage nel Registro di sistema a cui si applica l'opzione della riga di comando.  
  
## <a name="retrieving-command-line-switches"></a>Il recupero della riga di comando  
 Quando viene caricato il pacchetto, è possibile recuperare le opzioni della riga di comando, completare i passaggi seguenti.  
  
1.  Nel pacchetto VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione, chiamare `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> per ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaccia.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> per recuperare le opzioni della riga di comando immessi dall'utente.  
  
 Il codice seguente viene illustrato come determinare se l'opzione della riga di comando MySwitch è stato immesso dall'utente:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 È responsabilità dell'utente per verificare la presenza delle opzioni della riga di comando ogni volta che viene caricato il pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv Command Line Switches](../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [Utilità CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. File pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)