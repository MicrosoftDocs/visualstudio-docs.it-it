---
title: Imposta processo corrente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ea3028be32fdccffd70f7b3d0aa9d3b4eba172c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-current-process"></a>Imposta processo corrente
Imposta il processo specificato come processo attivo nel debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Obbligatorio. L'indice del processo.  
  
## <a name="remarks"></a>Note  
 Sebbene sia possibile connettersi a più processi durante il debug, nel debugger è attivo un solo processo alla volta. Per impostare il processo attivo, è possibile usare il comando `SetCurrentProcess`.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)