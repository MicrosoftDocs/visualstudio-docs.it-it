---
title: Visualizzare i valori di registro nel Debugger di Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7aa89b6e8d36c3eb47168c8672fb7eea1e3507db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger"></a>Visualizzare i valori di registrare e utilizzare la finestra registri nel Debugger di Visual Studio
La finestra Registri è disponibile solo se il debug a livello di indirizzo è abilitato nel **opzioni** nella finestra di dialogo **debug** nodo **generale** categoria.  
  
 Il **registra** finestra Visualizza il contenuto del Registra. Se si mantengono le **registra** aperto durante l'esecuzione del programma, è possibile visualizzare le modifiche dei valori durante l'esecuzione del codice. I valori modificati di recente sono visualizzati in rosso. È possibile modificare i valori dei registri. Per ulteriori informazioni, vedere [procedura: modificare un valore di registro](../debugger/how-to-edit-a-register-value.md).  
  
 Per evitare confusione, il **registra** finestra i registri sono organizzati in gruppi che variano in base alla piattaforma e del processore tipo. È possibile visualizzare o nascondere i gruppi desiderati. Per ulteriori informazioni, vedere [procedura: visualizzare e nascondere gruppi di registri](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Per un'introduzione generale a concetti di base registri e la finestra registri, vedere [nozioni fondamentali di debug: finestra Registri](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Per visualizzare la finestra Registri  
  
-   Nel **Debug** menu, scegliere **Windows**, quindi scegliere **registra**.  
  
     Il debugger deve essere in esecuzione o in modalità di interruzione.  
  
    > [!NOTE]
    >  Le informazioni relative ai registri non sono disponibili per le applicazioni SQL o script.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali di debug: finestra Registri](../debugger/debugging-basics-registers-window.md)   
 [Visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Nozioni fondamentali di debug: finestra Registri](../debugger/debugging-basics-registers-window.md)