---
title: Visualizza le DLL e file eseguibili nel Debugger | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: "36"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 772c252265e15c3c928fbcc47c756ceafd9e1362
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Visualizzare le DLL e file eseguibili utilizzando la finestra moduli nel Debugger di Visual Studio
 
Il **moduli** finestra sono elencate le DLL e file eseguibili (EXE) che vengono utilizzati dal programma e Mostra le informazioni rilevanti per ognuno. 

> [!NOTE]
>  Questa funzionalità non è disponibile per il debug di script o SQL. 
  
### <a name="to-display-the-modules-window"></a>Per visualizzare la finestra moduli  
  
-   Durante il debug, selezionare **Debug > Windows** e quindi fare clic su **moduli**.  
  
     Per impostazione predefinita, il **moduli** finestra sono ordinati in base all'ordine di caricamento. È tuttavia possibile ordinare i moduli in base a qualsiasi colonna.  
  
### <a name="to-sort-by-any-column"></a>Per eseguire l'ordinamento in base a una colonna  
  
-   Fare clic sul pulsante nella parte superiore della colonna.  
  
     È possibile caricare simboli o specificare un percorso simboli dal **moduli** finestra usando il menu di scelta rapida.  
  
## <a name="loading-symbols"></a>Caricamento dei simboli  
 Nel **moduli** finestra, è possibile visualizzare i moduli di caricati simboli di debug. Queste informazioni sono visualizzate le **stato simboli** colonna. Se viene visualizzato lo stato **loadingCannot ignorati trovare o aprire il file PDB**, o **caricamento disabilitato dall'impostazione include/exclude**, è possibile utilizzare il debugger per scaricare i simboli di simboli pubblici Microsoft Server o per caricare i simboli da una directory del simbolo sul computer. Per ulteriori informazioni, vedere [specificare simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Per caricare i simboli manualmente  
  
1.  Nel **moduli** , il pulsante destro finestra un modulo per cui non sono stati caricati i simboli.  
  
2.  Scegliere **Carica simboli da** e quindi fare clic su **server dei simboli Microsoft** o **percorso dei simboli**.  
  
#### <a name="to-change-symbol-load-settings"></a>Per modificare le impostazioni di caricamento dei simboli  
  
1.  Nel **moduli** finestra, fare doppio clic su qualsiasi modulo.  
  
2.  Fare clic su **le impostazioni dei simboli**.  
  
     È ora possibile modificare le impostazioni di caricamento dei simboli, come descritto in [specificare percorsi dei simboli e il comportamento di caricamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Riavviare la sessione di debug per rendere effettive le modifiche.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Per modificare il comportamento di caricamento dei simboli per un modulo specifico  
  
1.  Nel **moduli** finestra, fare doppio clic sul modulo.  
  
2.  Scegliere **impostazioni caricamento automatico simboli** e quindi fare clic su **Carica sempre manualmente** o **predefinito**. Riavviare la sessione di debug per rendere effettive le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Interruzione dell'esecuzione](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)