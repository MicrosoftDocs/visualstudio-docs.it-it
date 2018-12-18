---
title: 'Procedura: eseguire il Debug di .NET Framework origine | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 46c030a3c81f4b49fc66a06ee55d797dfe9119dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-net-framework-source"></a>Procedura: debug del codice sorgente di .NET Framework
La versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornisce nuove funzionalità per [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] il debug. Per eseguire il debug [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] origine, è necessario avere accesso ai simboli per il codice di debug. È inoltre necessario attivare l'esecuzione [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] origine.  
  
 È possibile abilitare [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] il download di simboli e l'esecuzione di **opzioni** la finestra di dialogo. Quando si attiva il download dei simboli, è possibile scegliere di scaricarli immediatamente o attivare solo l'opzione per eseguire il download successivamente. Se non si esegue immediatamente il download, i simboli verranno scaricati la volta successiva che si avvia il debug dell'applicazione. È anche possibile eseguire il download manuale di **moduli** finestra o **Stack di chiamate** finestra.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Per attivare il debug di origine di .NET Framework   
  
1.  Nel **strumenti** menu, fare clic su **opzione**s.  
  
2.  Nel **opzioni** la finestra di dialogo, fare clic su di **debug** categoria.  
  
3.  Nel **generale** impostare **abilitare .NET Framework** esecuzione di istruzioni origine.  
  
    1.  Se Just My Code è attivato, viene visualizzata una finestra di dialogo con un avviso indicante che Just My Code è stato disabilitato. Fare clic su **OK**.  
  
    2.  Se il percorso della cache dei simboli non è impostato, viene visualizzata un'altra finestra di dialogo con un avviso indicante che è stato impostato il percorso predefinito della cache dei simboli. Fare clic su **OK**.  
  
4.  Sotto il **debug** categoria, fare clic su **simboli**.  
  
5.  Se si desidera modificare il percorso della cache dei simboli:  
  
    1.  Aprire il **debug** nodo nella casella a sinistra.  
  
    2.  Sotto il **debug** nodo, fare clic su **simboli**.  
  
    3.  Modificare il percorso in **memorizzare nella Cache i simboli dai server dei simboli in questa directory** oppure fare clic su **Sfoglia** per scegliere un percorso.  
  
6.  Se si desidera scaricare immediatamente simboli, fare clic su **carica i simboli utilizzando percorsi indicati sopra**.  
  
     Questo pulsante non è disponibile nella modalità progettazione.  
  
     Se non si sceglie di scaricare ora i simboli, questi ultimi verranno scaricati automaticamente al successivo avvio del debug del programma.  
  
7.  Fare clic su **OK** per chiudere la finestra di dialogo **Opzioni**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Per caricare simboli di Framework utilizzando la finestra Moduli  
  
1.  Nel **moduli** , il pulsante destro finestra un modulo per cui non sono stati caricati i simboli. È possibile indicare se i simboli siano caricati o meno, esaminando la **stato simboli** colonna.  
  
2.  Scegliere **Carica simboli da** e fare clic su **server dei simboli Microsoft** per scaricare i simboli dai server dei simboli pubblici Microsoft o **percorso dei simboli** caricare da una directory in cui è stata precedentemente memorizzata simboli.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Per caricare simboli di Framework utilizzando la finestra Stack di chiamate  
  
1.  Nel **Stack di chiamate** , il pulsante destro finestra frame per il quale non sono stati caricati i simboli. Il frame verrà disattivato (rappresentato in grigio).  
  
2.  Scegliere **Carica simboli da** e fare clic su **server dei simboli Microsoft** o **percorso dei simboli**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)