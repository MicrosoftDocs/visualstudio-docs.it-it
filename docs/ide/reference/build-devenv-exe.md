---
title: -Build (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1cc01dac34723f2a587e76461d41a60361a72091
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
Consente di compilare una soluzione con un file di configurazione della soluzione specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>Argomenti  
 `SolutionName`  
 Obbligatorio. Percorso completo e nome del file della soluzione.  
  
 `SolnConfigName`  
 Obbligatorio. Nome della configurazione della soluzione da usare per compilare la soluzione indicata in `SolutionName`.  
  
 /project `ProjName`  
 Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 /projectconfig `ProjConfigName`  
 Facoltativo. Nome della configurazione di compilazione del progetto da usare per la compilazione del `/project` denominato.  
  
## <a name="remarks"></a>Note  
 Questa opzione esegue la stessa funzione del comando di menu **Compila soluzione** nell'ambiente di sviluppo integrato (IDE).  
  
 Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
 Le informazioni di riepilogo sulle compilazioni, compresi gli errori, possono essere visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
 Questo comando esegue la compilazione dei soli progetti modificati dopo l'ultima compilazione. Per compilare tutti i progetti in una soluzione, usare [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).  
  
## <a name="example"></a>Esempio  
 Questo esempio compila il progetto `CSharpConsoleApp` usando la configurazione di compilazione del progetto `Debug` all'interno della configurazione della soluzione `Debug` di `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)