---
title: Comando Stampa | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bba20817c03b7ff542c3af11a440ad8e619f5567
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="print-command"></a>Comando Print
Valuta un'espressione o visualizza il testo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 Obbligatorio. Espressione da valutare o testo da visualizzare.  
  
## <a name="remarks"></a>Note  
 È possibile usare il punto interrogativo (?) come alias per questo comando. Il comando  
  
```  
>Debug.Print expA  
```  
  
 può anche essere scritto  
  
```  
>? expA  
```  
  
 Entrambe le versioni di questo comando restituiscono il valore corrente dell'espressione `expA`.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Valuta istruzione](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)