---
title: Comando Valuta istruzione | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b3f0d5ecdcf1318490ac0829bb9dd6ded9519872
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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