---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8f50bfd0fa5b0f9303bc6256078a30da6e1c0575
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Apre il file eseguibile specificato per il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Argomenti  
 `ExecutableFile`  
 Obbligatorio. Percorso e nome di un file con estensione exe.  
  
 Se il file con estensione exe non viene trovato o non esiste, non viene visualizzato alcun avviso o errore e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene avviato normalmente.  
  
## <a name="remarks"></a>Note  
 Le stringhe che seguono il parametro `ExecutableFile` vengono passate al file come argomenti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il file `MyApplication.exe` viene aperto per il debug.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)