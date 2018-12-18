---
title: Comando Imposta thread corrente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3a3ccd860088c38b84b805a54ee17d50240b2e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-current-thread-command"></a>Comando Imposta thread corrente
Imposta il thread specificato come thread corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Obbligatorio. Seleziona un thread in base al relativo indice.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)