---
title: Comando Apri progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ba474de9c422031562e97d871cc070365f993cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="open-project-command"></a>Comando Apri progetto
Apre un progetto esistente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 Obbligatorio. Percorso completo e nome del file di progetto da aprire.  
  
 La sintassi per l'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.  
  
## <a name="remarks"></a>Note  
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.  
  
 Questo comando non è disponibile durante il debug.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene aperto il progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)