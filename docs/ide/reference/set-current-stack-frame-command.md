---
title: Comando Imposta stack frame corrente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8851530dec3e5e1a2c3e829c1508155a2dbda8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-current-stack-frame-command"></a>Comando Imposta stack frame corrente
Consente di impostare uno stack frame specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Obbligatorio. Seleziona uno stack frame in base all'indice.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)