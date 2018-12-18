---
title: Comando Apri file | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e6a4d05a7cfc19e66253331f6c302d9e7476797
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="open-file-command"></a>Comando Apri file
Apre un file esistente e consente di specificare un editor.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 Obbligatorio. Percorso completo o parziale e nome file del file da aprire. I percorsi contenenti spazi devo devono essere racchiusi tra virgolette.  
  
## <a name="switches"></a>Opzioni  
 /e:`editorname`  
 Facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.  
  
 La sintassi dell'argomento /e:`editorname` usa i nomi degli editor così come visualizzati nella finestra di dialogo Apri con, racchiusi tra virgolette.  
  
 Ad esempio, per aprire un file nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Note  
 Quando si immette un percorso, il completamento automatico tenta di individuare il percorso e il nome file corretti.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene aperto il file di stile "Test1.css" nell'editor del codice sorgente.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Finestra di controllo immediato](../../ide/reference/immediate-window.md)   
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)