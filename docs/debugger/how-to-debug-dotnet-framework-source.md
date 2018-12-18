---
title: 'Procedura: eseguire il Debug di .NET Framework origine | Documenti Microsoft'
ms.custom: ''
ms.date: 02/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8377ed73479441272b2f1910767fa7e2a4ff0196
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-net-framework-source"></a>Procedura: debug del codice sorgente di .NET Framework
Per eseguire il debug di origine di .NET Framework, è necessario avere accesso ai simboli per il codice di debug. È anche necessario abilitare l'esecuzione di istruzioni origine .NET Framework.  
  
 È possibile abilitare .NET Framework il download di simboli e l'esecuzione di **opzioni** la finestra di dialogo. Quando si attiva il download dei simboli, è possibile scegliere di scaricarli immediatamente o attivare solo l'opzione per eseguire il download successivamente. Se non si esegue immediatamente il download, i simboli verranno scaricati la volta successiva che si avvia il debug dell'applicazione. È anche possibile eseguire il download manuale di **moduli** finestra o **Stack di chiamate** finestra.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Per attivare il debug di origine di .NET Framework   
  
1.  Nel **strumenti** menu, fare clic su **opzione**s.  
  
2.  Nel **opzioni** la finestra di dialogo, fare clic su di **debug** categoria.  
  
3.  Nel **generale** impostare **origine .NET Framework consentono l'esecuzione di istruzioni.**  
  
    1.  Se Just My Code è attivato, viene visualizzata una finestra di dialogo con un avviso indicante che Just My Code è stato disabilitato. Fare clic su **OK**.  
  
    2.  Se il percorso della cache dei simboli non è impostato, viene visualizzata un'altra finestra di dialogo con un avviso indicante che è stato impostato il percorso predefinito della cache dei simboli. Fare clic su **OK**.  
  
4.  Sotto il **debug** categoria, fare clic su **simboli**.  
  
5.  Se si desidera modificare il percorso della cache di simboli, modificare il percorso in **memorizzare nella Cache i simboli in questa directory** oppure fare clic su **Sfoglia** per scegliere un percorso.  
  
6.  Se si desidera scaricare immediatamente simboli, fare clic su **carica i simboli utilizzando percorsi indicati sopra**.  
  
     Questo pulsante non è disponibile in modalità progettazione, ma è disponibile durante il debug.  
  
     Se non si sceglie di scaricare ora i simboli, questi ultimi verranno scaricati automaticamente al successivo avvio del debug del programma.  
  
7.  Fare clic su **OK** per chiudere la finestra di dialogo **Opzioni**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Per caricare simboli di Framework utilizzando la finestra Moduli  
  
1.  Nel **moduli** finestra (durante il debug, scegliere **Debug** > **Windows** > **moduli**), Fare doppio clic su un modulo per cui non sono stati caricati i simboli. È possibile indicare se i simboli siano caricati o meno, esaminando la **stato simboli** colonna.  
  
2.  Scegliere **impostazioni simboli** e fare clic su **server dei simboli Microsoft** per scaricare i simboli dai server dei simboli pubblici Microsoft. Oppure, il modulo di mouse e scegliere **Carica simboli** caricare da una directory in cui è stata precedentemente memorizzata simboli.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Per caricare simboli di Framework utilizzando la finestra Stack di chiamate  
  
1.  Nel **Stack di chiamate** , il pulsante destro finestra frame per il quale non sono stati caricati i simboli. Il frame verrà disattivato (rappresentato in grigio).  
  
2.  Scegliere **impostazioni simboli** e fare clic su **server dei simboli Microsoft**, o il modulo e scegliere **percorso dei simboli**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)