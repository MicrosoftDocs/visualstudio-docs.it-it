---
title: Comando Valuta istruzione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe960ec84830ce76095577f7d8ee2f0c9c4ccbe8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="evaluate-statement-command"></a>Comando Valuta istruzione
Valuta e visualizza l'istruzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 Obbligatorio. Istruzione da valutare.  
  
## <a name="remarks"></a>Note  
 La finestra usata per immettere il comando **EvaluateStatement** determina se interpretare un segno di uguale (=) come operatore di confronto o come operatore di assegnazione.  
  
 Nella finestra **Comando** il segno di uguale (=) viene interpretato come operatore di confronto. Pertanto, se ad esempio i valori delle variabili `a` e `b` sono diversi, il comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 restituisce il valore `false`.  
  
 Al contrario, nella finestra **Controllo immediato** il segno di uguale (=) viene interpretato come operatore di assegnazione. Il comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 assegna ad esempio alla variabile `a` il valore della variabile `b`.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Stampa](../../ide/reference/print-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)