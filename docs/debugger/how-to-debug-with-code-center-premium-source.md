---
title: 'Procedura: eseguire il Debug con Code Center Premium origine | Documenti Microsoft'
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
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7405deed95f14314215b869a02bcf8a1afddea2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Procedura: eseguire il debug con codice sorgente di Code Center Premium
Con il debugger di [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] è possibile eseguire il debug di codice sorgente condiviso sicuro disponibile in Microsoft MSDN Code Center Premium.  
  
 In questo argomento viene descritto come impostare Code Center Premium e come eseguire il debug del relativo codice sorgente in Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Per prepararsi all'esecuzione del debug con Code Center Premium  
  
1.  Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2.  Avviare Visual Studio.  
  
3.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
4.  Nel **opzioni** la finestra di dialogo, aprire il **debug** nodo e fare clic su **generale**.  
  
5.  Cancella il **Abilita Just My Code (solo gestito)** casella di controllo.  
  
6.  Selezionare **Abilita il supporto di Server di origine attiva**.  
  
7.  Deselezionare **richiedono file di origine corrispondere esattamente alla versione originale**.  
  
8.  Sotto il **debug** nodo, fare clic su **simboli**.  
  
9. Nel **File di simboli (PDB) percorsi** casella, deseleziona il **Server dei simboli Microsoft** casella di controllo e aggiungere i percorsi seguenti:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Assicurarsi di includere la barra finale **/**  alla fine del percorso.  
  
     Spostare questi percorsi all'inizio dell'elenco per assicurarsi che questi simboli vengano caricati per primi.  
  
    > [!NOTE]
    >  Questi percorsi di Code Center Premium devono essere elencati per primi in modo che vengano caricati per primi. In Visual Studio 2010, è possibile spostare server sopra il **server dei simboli Microsoft** voce, motivo per cui è necessario deselezionare la casella di controllo.  
    >   
    >  Per caricare simboli dai simboli Microsoft durante la sessione di debug, eseguire questa operazione:  
    >   
    >  1.  Nel **Debug** menu, scegliere **Windows** e quindi scegliere **moduli**.  
    > 2.  Selezionare il modulo di cui si desidera caricare simboli, quindi aprire il menu di scelta rapida. Scegliere **Carica simboli da** e quindi scegliere **server dei simboli Microsoft**.  
  
10. Nel **memorizzare nella Cache i simboli dai server di simboli in questa directory** , immettere un percorso, ad esempio `C:\symbols` in Code Center Premium può memorizzare nella cache di simboli. La memorizzazione nella cache dei simboli può contribuire a migliorare le prestazioni durante il debug.  
  
     Se si verificano dei problemi durante il debug del codice sorgente con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dopo avere completato questa procedura, controllare il percorso della cache per i file di simboli non aggiornati e memorizzati nella cache. Rimuovere i file di simboli non aggiornati.  
  
11. Fare clic su **OK**.  
  
12. Riavviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per assicurarsi che le impostazioni siano state salvate in modo permanente.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Per eseguire il debug del codice sorgente utilizzando Connetti a processo  
  
1.  Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2.  Avviare Visual Studio.  
  
3.  Aprire il progetto di Visual Studio.  
  
4.  Nel **strumenti** menu, fare clic su **Connetti a processo**.  
  
5.  Nel **Connetti a processo** la finestra di dialogo, fare clic su **selezionare**.  
  
6.  Nel **Seleziona tipo di codice** nella finestra di dialogo **rilevare questi tipi di codice**selezionare **nativo**, **gestito**, e **gestiti ( v 4.0)**.  
  
7.  Fare clic su **OK** per chiudere la **Seleziona tipo di codice** la finestra di dialogo.  
  
8.  Nel **processi disponibili** , selezionare il processo che si desidera eseguire il debug.  
  
9. Scegliere **Connetti**.  
  
10. Quando viene chiesto di confermare il certificato, fare clic su **OK**. Immettere il PIN. Se richiesto, accettare le condizioni per l'utilizzo di Code Center Premium.  
  
     Il download dei simboli può richiedere molto tempo, a seconda della velocità della rete. Sulla barra di stato verrà indicato quando tutti i simboli sono stati scaricati correttamente.  
  
11. Ripetere i passaggi di connessione per tutti i progetti gestiti nella soluzione.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Per eseguire il debug del codice sorgente da una soluzione esistente  
  
1.  In **Esplora**, aprire il menu di scelta rapida per la soluzione e quindi scegliere **proprietà**.  
  
2.  Nella finestra di dialogo Pagine delle proprietà della soluzione, scegliere **Esegui Debug dei file di origine** nel **proprietà comuni** nodo.  
  
3.  Aggiungere il seguente percorso per il **directory contenenti file di origine** elenco:  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Assicurarsi di includere la barra finale **/**  alla fine del percorso.  
  
4.  Per ogni progetto gestito nella soluzione, eseguire quanto segue:  
  
    1.  In Esplora soluzioni, aprire il menu di scelta rapida per il progetto e quindi scegliere **proprietà**.  
  
    2.  Selezionare **Debug** e quindi scegliere **Abilita debug codice non gestito**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Per eseguire il debug della soluzione con l'origine Code Center Premium  
  
1.  Nella classe `Package` impostare un punto di interruzione nel costruttore del pacchetto.  
  
2.  Nel `Debug` menu, fare clic su **Avvia debug**.  
  
3.  Quando si raggiunge il punto di interruzione nel costruttore del pacchetto, passare al **Stack di chiamate** finestra e pulsante destro del mouse sul frame dello stack dell'assembly che si desidera caricare i simboli, quindi fare clic su **Carica simboli**.  
  
     Fare doppio clic sul frame di chiamata per caricare l'origine.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Per analizzare il codice sorgente in Code Center Premium  
  
1.  Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2.  Avviare Internet Explorer e immettere l'URL `https://codepremium.msdn.microsoft.com`  
  
3.  Cercare il codice sorgente desiderato.  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)