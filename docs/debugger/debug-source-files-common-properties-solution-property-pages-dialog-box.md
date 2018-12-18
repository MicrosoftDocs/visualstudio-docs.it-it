---
title: "Origine dei file, proprietà comuni, soluzione dialogo Pagine delle proprietà debug | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aa83025b15fe3773220a2b27394890318d60c850
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Esegui debug dei file di origine, Proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione
In questa pagina delle proprietà è specificato il punto in cui il debugger cerca i file di origine durante il debug della soluzione.  
  
 Per l'accesso di **Esegui Debug dei file di origine** pagina delle proprietà, pulsante destro del mouse sulla soluzione in **Esplora** e selezionare **proprietà** dal menu di scelta rapida. Espandere il **proprietà comuni** cartella, scegliere il **Esegui Debug dei file di origine** pagina.  
  
 **Directory contenenti codice sorgente**  
 Contiene un elenco di directory in cui il debugger cerca i file di origine durante il debug della soluzione. La ricerca viene eseguita anche nelle sottodirectory delle directory specificate.  
  
 **Non cercare i file di origine**  
 Immettere i nomi dei file che non si desidera vengano letti dal debugger. Se il debugger trova uno di questi file in una delle directory specificate in precedenza, lo ignora. Se il **Trova origine** viene visualizzata la finestra di dialogo mentre si esegue il debug e si fa clic su **Annulla**, il file cercato verrà aggiunto a questo elenco in modo che il debugger non può continuare la ricerca di tale file.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)