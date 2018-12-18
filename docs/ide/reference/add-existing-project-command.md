---
title: Comando Aggiungi progetto esistente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 278ed3e13f29746aab963129418dc07f1dcf5234
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="add-existing-project-command"></a>Comando Aggiungi progetto esistente
Aggiunge un progetto esistente alla soluzione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 Facoltativo. Percorso completo e nome del progetto comprensivo di estensione da aggiungere alla soluzione.  
  
 Se l'argomento `filename` include spazi, deve essere racchiuso tra virgolette.  
  
 Se non viene specificato un nome file, il comando aprirà la finestra di dialogo in cui l'utente potrà selezionare un progetto.  
  
## <a name="remarks"></a>Note  
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene aggiunto il progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] TestProject1 alla soluzione corrente.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)