---
title: Imposta processo corrente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb673db29a4bb106aa4c9c4d9022293367e8ed4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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