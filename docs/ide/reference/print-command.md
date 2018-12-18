---
title: Comando Stampa | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66175f8aa1d371386793b892c0ead5b4dd1885b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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