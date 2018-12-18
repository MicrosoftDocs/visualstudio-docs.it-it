---
title: -ProjectConfig (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26883d4149047df980763da8bdda764f8ad802b5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
Specifica la configurazione di compilazione di un progetto da applicare quando si compila, si pulisce, si ricompila o si distribuisce il progetto indicato nell'argomento `/project`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>Argomenti  
 /build  
 Compila il progetto specificato da `/project` `ProjName`.  
  
 /clean  
 Pulisce tutti i file intermedi e le directory di output creati durante una compilazione.  
  
 /rebuild  
 Pulisce e ricompila il progetto specificato da `/project` `ProjName`.  
  
 /deploy  
 Specifica che il progetto deve essere distribuito dopo una compilazione o una ricompilazione.  
  
 `SolnConfigName`  
 Obbligatorio. Il nome della configurazione di soluzione da applicare alla soluzione indicata in `SolutionName`.  
  
 `SolutionName`  
 Obbligatorio. Il percorso completo e il nome del file della soluzione.  
  
 /project `ProjName`  
 Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 /projectconfig `ProjConfigName`  
 Facoltativo. Il nome della configurazione della build di un progetto da applicare al `/project` denominato.  
  
## <a name="remarks"></a>Note  
  
-   Deve essere usato specificando l'opzione `/project` come parte di un comando `devenv /build`, /`clean`, `/rebuild` o `/deploy`.  
  
-   Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
-   Le informazioni di riepilogo per le compilazioni, compresi gli errori, vengono visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## <a name="example"></a>Esempio  
 Questo esempio compila il progetto `CSharpConsoleApp` usando la configurazione di compilazione del progetto `Debug` all'interno della configurazione della soluzione `Debug` di `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)