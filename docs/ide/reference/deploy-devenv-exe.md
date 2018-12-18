---
title: -Deploy (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dee247f9c948ae5a5d0ac6926679b7849c4c1fbc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
Distribuisce una soluzione dopo una compilazione o ricompilazione. Si applica solo ai progetti di codice gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## <a name="arguments"></a>Argomenti  
 `SolnConfigName`  
 Obbligatorio. Nome della configurazione della soluzione da usare per compilare la soluzione indicata in `SolutionName`.  
  
 `SolutionName`  
 Obbligatorio. Il percorso completo e il nome del file della soluzione.  
  
 /project `ProjName`  
 Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 /projectconfig `ProjConfigName`  
 Facoltativo. Nome della configurazione di compilazione del progetto da usare per la compilazione del `/project` denominato.  
  
## <a name="remarks"></a>Note  
 Il progetto specificato deve essere un progetto di distribuzione. Se non lo è, quando il progetto compilato viene passato per essere distribuito genererà un errore.  
  
 Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
 Le informazioni di riepilogo per le compilazioni, compresi gli errori, vengono visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene distribuito il progetto `CSharpConsoleApp` usando la configurazione della build del progetto `Release` all'interno della configurazione della soluzione `Release` di `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)