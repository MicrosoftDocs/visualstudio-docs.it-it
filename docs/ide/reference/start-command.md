---
title: Comando Avvia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a4c372d3f384eeaa0ac137188e325ccde777cd4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="start-command"></a>Comando Avvia
Inizia il debug del progetto di avvio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Argomenti  
 `address`  
 Facoltativo. Indirizzo in corrispondenza del quale il programma sospende l'esecuzione, simile a un punto di interruzione nel codice sorgente. Questo argomento è valido solo in modalità di debug.  
  
## <a name="remarks"></a>Note  
 Il comando **Avvia**, quando eseguito, esegue un'operazione RunToCursor sull'indirizzo specificato.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene avviato il debugger e le eccezioni vengono ignorate.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)