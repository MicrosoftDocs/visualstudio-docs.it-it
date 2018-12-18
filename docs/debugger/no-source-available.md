---
title: Nessuna origine disponibile | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aae4b2428470e3e33477cfdb36699c2c1da20c1f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
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
 [Eseguire il debug di finestra di dialogo Pagine proprietà soluzione dei file, proprietà comuni, origine](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (estensione del debugger SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)