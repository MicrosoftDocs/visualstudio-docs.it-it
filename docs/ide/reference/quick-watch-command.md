---
title: Comando Controllo immediato | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75ac6c430d34dabdba3a6bebcce78c7c5b9817b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quick-watch-command"></a>Comando Controllo immediato
Visualizza il testo selezionato o specificato nel campo Espressione della finestra di dialogo [Controllo immediato](../../debugger/watch-and-quickwatch-windows.md). È possibile usare questa finestra di dialogo per calcolare il valore corrente di una variabile o di un'espressione riconosciuta dal debugger o i contenuti di un registro. È anche possibile modificare il valore di una variabile non costante o i contenuti di un registro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 Facoltativo. Il testo da aggiungere alla finestra di dialogo **Controllo immediato**.  
  
## <a name="remarks"></a>Note  
 Se `text` è omesso, il testo o la parola selezionata in corrispondenza del cursore viene aggiunta alla finestra Espressioni di controllo.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md)  (Impostare un'espressione di controllo per le variabili con le finestre Espressione di controllo e Controllo immediato in Visual Studio)  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)