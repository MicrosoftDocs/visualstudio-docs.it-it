---
title: 'Procedura dettagliata: XSLT Profiler | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: be03e554bbdf55c447437116373cc60b15df391e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-xslt-profiler"></a>Procedura dettagliata: XSLT Profiler
Il Profiler XSLT crea rapporti di prestazioni XSLT dettagliati utili per misurare, valutare e trattare problemi correlati alle prestazioni nel codice XSLT. Il Profiler XSLT include suggerimenti utili per le ottimizzazioni dei fogli di stile XSL e XSLT. Per applicazioni XSLT che richiedono massime prestazioni, questo strumento potrebbe essere essenziale.  
  
## <a name="prerequisites"></a>Prerequisiti  
Le procedure descritte nella seguente procedura dettagliata richiedono Visual Studio e .NET Framework versione 4.0 o versione successiva.
  
### <a name="create-the-performance-report"></a>Creare il rapporto di prestazioni  
  
1.  Aprire un documento XSLT in Visual Studio.  
  
2.  Fare clic su di **profila XSLT** opzione disponibile nel menu XML.  
  
3.  Fornire un documento XML di input. Se non è già aperto un documento XML, verrà richiesto il file.  
  
4.  L'analisi viene avviata e un indicatore di stato visualizza lo stato di avanzamento all'interno dell'editor.  
  
5.  L'output XSLT è visibile nel riquadro di output.  
  
6.  Al termine di una sessione di prestazioni, controllare il rapporto di prestazioni. I dati salvati in un rapporto di prestazioni consentono di visualizzare e analizzare le prestazioni di XSLT.  
  
### <a name="get-all-the-available-views"></a>Ottenere tutte le visualizzazioni disponibili  
  
1.  Fare clic su di **visualizzazione corrente** elenco a discesa per ottenere tutte le visualizzazioni disponibili.  
  
2.  Selezionare il **visualizzazione riepilogo** opzione il **visualizzazione corrente** elenco a discesa. Per impostazione predefinita, viene visualizzato un report di prestazioni nel **visualizzazione riepilogo**. Questa visualizzazione costituisce un punto iniziale per determinare problemi di prestazioni con i documenti XSLT. Il **visualizzazione riepilogo** sono elencati i punti dati seguenti:  
  
    -   Funzioni più chiamate  
  
    -   Funzioni con più lavoro individuale  
  
    -   Funzioni la cui esecuzione richiede più tempo  
  
3.  Per impostazione predefinita, esistono tre colonne per ogni punto dati: il nome della funzione, il numero di chiamate in valore assoluto e un valore percentuale della funzione denominata per sommare le chiamate di funzione. Da ogni punto dati nella **visualizzazione riepilogo**, è possibile passare a visualizzazioni più dettagliate facendo clic su punti dati della funzione.  
  
4.  Selezionare il **visualizzazione funzione** opzione il **visualizzazione corrente** elenco a discesa. Il **visualizzazione funzione** Elenca le funzioni chiamate durante l'analisi. Per ordinare i dati è possibile fare clic sul nome di una colonna. Le colonne visualizzate per impostazione predefinita sono:  
  
    -   **Nome funzione**  
  
    -   **Tempo inclusivo trascorso**  
  
    -   **Tempo esclusivo trascorso**  
  
    -   **Tempo inclusivo applicazione**  
  
    -   **Tempo esclusivo applicazione**  
  
    -   **Numero di chiamate**  
  
5.  Tutte le colonne dell'ora vengono visualizzate sia in valori assoluti che in percentuali. Il termine **esclusivo** si riferisce al tempo totale di una funzione per l'esecuzione, escluso il tempo impiegato da altre funzioni chiamata durante l'esecuzione di questa funzione.  
  
6.  Il termine **inclusivo** si riferisce al tempo totale impiegato da una funzione per l'esecuzione, incluso il tempo di esecuzione di tutte le funzioni chiamate e se una di queste funzioni chiamate ha chiamato altre funzioni.  
  
### <a name="select-callercallee-view"></a>Selezionare la visualizzazione Chiamante/chiamato  
  
1.  Selezionare **chiamante/chiamato** visualizzare il **visualizzazione corrente** elenco a discesa.  
  
2.  Il **chiamante/chiamato** Vista dispone di tre parti distinte seguenti:  
  
    -   **Funzioni che hanno chiamato**: tutte le funzioni che ha chiamato una particolare funzione vengono elencate nella parte superiore della visualizzazione.  
  
    -   **Funzione corrente**: la funzione chiamata è elencata nella parte centrale della visualizzazione.  
  
    -   **Le funzioni chiamate da** : tutte le funzioni che sono state chiamate dalla particolare funzione vengono elencate nella parte inferiore della visualizzazione.  
  
3.  Se una funzione denominata `SyncToNavigator` viene riportata nella parte centrale della visualizzazione, tutte le funzioni che hanno chiamato la funzione `SyncToNavigator` vengono visualizzate nella parte superiore della visualizzazione e tutte le funzioni che sono state chiamate da `SyncToNavigator` vengono elencate nella parte inferiore della visualizzazione.  
  
4.  È possibile modificare la funzione nella parte centrale della visualizzazione facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione. La visualizzazione verrà quindi automaticamente aggiornata in base alle modifiche.  
  
5.  Per ordinare i dati, è anche possibile fare clic sui nomi delle colonne.  
  
### <a name="select-calltree-view"></a>Selezionare la visualizzazione albero delle chiamate  
  
1.  Selezionare **visualizzazione albero delle chiamate** nel **visualizzazione corrente** elenco a discesa. Questa visualizzazione è un albero dell'esecuzione del programma.  
  
2.  Il **visualizzazione albero delle chiamate** viene mostrata la radice dell'albero come nome del processo. Le funzioni sono i nodi dell'albero. Questa visualizzazione consente di esaminare determinate tracce di chiamata e di analizzare quali tracce hanno il maggiore impatto sulle prestazioni. La visualizzazione è simile al **visualizzazione Stack di chiamate** disponibile durante il debug. Oltre alle colonne nel **visualizzazione funzione**, nel **visualizzazione albero delle chiamate**, è una colonna aggiuntiva che visualizza il **nome modulo**.  
  
3.  Selezionare **segni** nel **visualizzazione corrente** elenco a discesa.  
  
4.  Con il Profiler SLT, vengono visualizzati contrassegni nel flusso di raccolta dati con un commento associato. I contrassegni sono parti del codice che dispongono di contatori. Indicando al Profiler XSLT di raccogliere contatori delle prestazioni XSLT, i contatori vengono raccolti ogni volta che viene eseguito uno di questi contrassegni. I dati vengono visualizzati in una tabella che contiene il **ID contrassegno**, **nome contrassegno** (**Avvia programma**, **termina programma**) e  **Data e ora**. I contrassegni non sono aggregati e visualizzati in ordine cronologico nel **visualizzazione contrassegni** di report di prestazioni.  
  
### <a name="select-modules-in-the-current-view"></a>Selezionare i moduli nella visualizzazione corrente  
  
1.  Selezionare **moduli** nel **visualizzazione corrente** elenco a discesa.  
  
2.  La visualizzazione dei moduli è un elenco completo di tutte le funzioni aggregate a livello di modulo. Espandere o comprimere il nome del modulo per visualizzare o chiudere la visualizzazione dei dati relativi alle prestazioni del modulo. Per ordinare i dati è possibile fare clic sul nome di una colonna. Per impostazione predefinita, esistono sia valori assoluti che numeri in percentuale per **tempo inclusivo trascorso**, **tempo esclusivo trascorso**, **tempo inclusivo applicazione**, **Tempo esclusivo applicazione**, e **numero di chiamate**.  
  
3.  Selezionare **processo** nel **visualizzazione corrente** elenco a discesa.  
  
4.  Visualizzazione processo consente di visualizzare una tabella che include il **ID processo**, **nome processo**, **ora di inizio**e **ora di fine**. Per ordinare i dati, è possibile fare clic sui nomi delle colonne.  
  
## <a name="see-also"></a>Vedere anche  
[Procedura dettagliata: uso della gerarchia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)