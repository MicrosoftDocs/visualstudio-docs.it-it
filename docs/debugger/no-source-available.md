---
title: Nessuna origine disponibile | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a11770bc54a7b96aa918b73b34e0028731bf0f9c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="no-source-available"></a>Nessuna origine disponibile
Il progetto non contiene codice sorgente per il codice che si tenta di visualizzare. La causa è facendo doppio clic su un modulo che non dispone di codice sorgente nel **finestra Stack di chiamate** o **finestra thread**. È possibile continuare il debug, ma non è possibile utilizzare la finestra di origine per impostare i punti di interruzione ed eseguire altre operazioni in questa posizione. Se è necessario impostare un punto di interruzione, utilizzare il **finestra Disassembly** invece.  
  
 Nelle pagine delle proprietà della soluzione è possibile modificare le directory in cui il debugger cerca i file di origine e indicare al debugger di ignorare determinati file di origine. Vedere [origine file, proprietà comuni, soluzione dialogo Pagine delle proprietà di Debug](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Sfoglia per trovare il codice sorgente**  
 Fare clic su questo collegamento per aprire una finestra di dialogo in cui è possibile cercare il codice sorgente.  
  
 **Mostra Disassembly**  
 Avvia il **finestra Disassembly**.  
  
 **Mostra sempre disassembly per i file di origine mancanti**  
 Selezionare questa opzione per visualizzare il **finestra Disassembly** automaticamente quando è disponibile alcuna origine. Questa impostazione può essere modificata anche nel **opzioni** nella finestra di dialogo **debug** categoria **generale** pagina, selezionando o deselezionando **Mostra disassembly se origine non è disponibile**.  
  
## <a name="see-also"></a>Vedere anche  
 [Origine dei file, proprietà comuni, soluzione dialogo Pagine delle proprietà di debug](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (estensione del debugger SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)