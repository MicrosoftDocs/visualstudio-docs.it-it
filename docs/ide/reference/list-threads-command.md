---
title: Comando Elenca thread | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 094ba1b16f208d1af0ba9426daba67aed604f0c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="list-threads-command"></a>Comando Elenca thread
Visualizza un elenco dei thread del programma corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Facoltativo. Seleziona un thread in base al relativo indice e lo contrassegna come thread corrente.  
  
## <a name="remarks"></a>Note  
 Quando specificato, l'argomento `index` contrassegna il thread indicato come thread corrente. Nell'elenco viene visualizzato un asterisco (*) accanto al thread corrente.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca disassembly](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)