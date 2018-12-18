---
title: 'Procedura: individuare la DLL del programma di arresto anomalo | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95ad4f9c028b9b40bf5104539a608453c9d6f9dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Procedura: individuare la DLL che ha causato l'arresto anomalo del programma
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Se l'applicazione si arresta in modo anomalo durante la chiamata a una DLL di sistema o al codice di un altro utente, è necessario identificare la DLL attiva al momento dell'arresto. Se si verifica un arresto anomalo in una DLL esterna al programma, è possibile identificare la posizione utilizzando il **moduli** finestra.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Per stabilire la posizione in cui si è verificato un arresto anomalo mediante la finestra Moduli  
  
1.  Annotare l'indirizzo in cui si è verificato l'arresto.  
  
2.  Nel **Debug** menu, scegliere **Windows**, fare clic su **moduli**.  
  
3.  Nel **moduli** finestra, trovare il **indirizzo** colonna. Per visualizzarla potrebbe essere necessario utilizzare la barra di scorrimento.  
  
4.  Fare clic su di **indirizzo** pulsante nella parte superiore della colonna per ordinare le DLL in base all'indirizzo.  
  
5.  Cercare nell'elenco ordinato la DLL il cui intervallo di indirizzi contenga la posizione in cui si è verificato l'arresto anomalo.  
  
6.  Esaminare il **nome** e **percorso** colonne per visualizzare il nome della DLL e il percorso.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di progetti di DLL](../debugger/debugging-dll-projects.md)   
 [Procedura: Usare la finestra Moduli](../debugger/how-to-use-the-modules-window.md)