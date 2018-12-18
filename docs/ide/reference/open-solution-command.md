---
title: Comando Apri soluzione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e97fa5265550222b4df9143a900419a0994f9129
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="open-solution-command"></a>Comando Apri soluzione
Apre una soluzione esistente, chiudendo tutte le altre soluzioni aperte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Argomenti  
 `Filename`  
 Obbligatorio. Il percorso completo e nome file della soluzione da aprire.  
  
 La sintassi per l'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.  
  
## <a name="remarks"></a>Note  
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene aperta la soluzione Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)