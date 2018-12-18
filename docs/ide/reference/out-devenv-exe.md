---
title: -Out (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af8d41a8a401e3087845e6d698163626f120a52e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Specifica un file per archiviare e visualizzare gli errori quando si esegue, compila, ricompila o distribuisce una soluzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Argomenti  
 `FileName`  
 Obbligatorio. Percorso e nome del file per ricevere errori quando si compila un eseguibile.  
  
## <a name="remarks"></a>Note  
 Se viene specificato un nome file che non esiste, il file viene creato automaticamente. Se il file esiste già, i risultati vengono aggiunti al contenuto del file già esistente.  
  
 Gli errori di compilazione della riga di comando vengono visualizzati nella finestra **Comando** e nella vista del generatore di soluzioni della finestra **Output**. Questa opzione è utile se si eseguono compilazioni automatiche ed è necessario visualizzare i risultati.  
  
## <a name="example"></a>Esempio  
 Questo esempio esegue `MySolution` e gli errori vengono scritti nel file `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)