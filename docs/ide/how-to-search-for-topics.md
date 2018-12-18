---
title: 'Procedura: Eseguire la ricerca di argomenti | Microsoft Docs'
ms.custom: 
ms.date: 11/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e93a3ca0c6cf7446b4b943c2e6a19018f1a16c7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-topics"></a>Procedura: Eseguire la ricerca di argomenti
È possibile usare la funzionalità di ricerca full-text per individuare tutti gli argomenti che contengono una parola specifica. È anche possibile perfezionare e personalizzare la ricerca usando espressioni con caratteri jolly, operatori logici e operatori di ricerca avanzata.  
  
Per aprire la scheda Cerca, scegliere la scheda **Cerca** scheda nella finestra Help Viewer oppure se si usa la tastiera, scegliere **CTRL+E**.  
  
## <a name="to-perform-a-full-text-search"></a>Per eseguire una ricerca full-text 
1.  Nella casella di ricerca digitare la parola che si vuole trovare.  
  
2.  Nella query di ricerca specificare eventuali operatori logici o di ricerca avanzata da applicare alla ricerca. Per eseguire la ricerca in tutte le informazioni della Guida disponibili, non usare gli operatori.  
  
    > [!NOTE]
    >  Nella finestra di dialogo **Opzioni Help Viewer** è possibile specificare altre preferenze, ad esempio il numero massimo di risultati da visualizzare contemporaneamente e se includere i contenuti in lingua inglese quando le impostazioni locali sono diverse dall'inglese.  
  
3.  Premere il tasto **INVIO**.  
  
     Per impostazione predefinita, una ricerca restituisce un massimo di 200 risultati che vengono visualizzati nell'area corrispondente. È possibile che vengano visualizzate informazioni aggiuntive sulla versione per ogni risultato, a seconda del contenuto.  
  
4.  Per visualizzare un argomento, scegliere il titolo dall'elenco dei risultati.

## <a name="full-text-search-tips"></a>Suggerimenti per la ricerca full-text
Se si comprendono gli effetti della sintassi sulle query, è possibile creare ricerche più mirate che restituiscano solo gli argomenti di interesse. La sintassi include caratteri speciali, parole riservate e filtri. In questo argomento vengono illustrati suggerimenti, procedure e informazioni dettagliate sulla sintassi che aiutano a creare le query correttamente.
  
### <a name="general-guidelines"></a>Indicazioni generali  
Nella tabella seguente sono elencate alcune regole di base e linee guida per lo sviluppo di query di ricerca nella Guida.  
  
|Sintassi|Descrizione|  
|------------|-----------------|  
|Distinzione fra maiuscole e minuscole|Le ricerche non distinguono tra maiuscole e minuscole. Sviluppare i criteri di ricerca usando indifferentemente caratteri maiuscoli o minuscoli. Ad esempio, "OLE" e "ole" restituiscono gli stessi risultati.|  
|Combinazioni di caratteri|Non è possibile cercare solo singole lettere (a-z) o singoli numeri (0-9). Se si tenta di cercare determinate parole riservate, ad esempio "e", "da" e "con", queste vengono ignorate. Per altre informazioni, vedere [Parole ignorate nelle ricerche](#stopwords) più avanti in questo argomento.|  
|Ordine di valutazione|Le query di ricerca vengono valutate da sinistra a destra.|  
  
### <a name="search-syntax"></a>Sintassi di ricerca  
Se si specifica una stringa di ricerca che include più parole, ad esempio "parola1 parola2", tale stringa equivale all'immissione di "parola1 AND parola2", che restituisce solo gli argomenti che contengono tutte le singole parole nella stringa di ricerca.  
  
> [!IMPORTANT]
> - La ricerca di frasi non è supportata. Se si specifica più di una parola in una stringa di ricerca, gli argomenti restituiti conterranno tutte le parole che sono state specificate ma non necessariamente la frase esatta.  
> - Usare gli operatori logici per specificare la relazione tra le parole nella frase di ricerca. È possibile includere operatori logici, come ad esempio AND, OR, NOT e NEAR, per limitare la ricerca. Ad esempio, se si cerca "dichiarazione NEAR unione", i risultati della ricerca includeranno argomenti contenenti le parole "dichiarazione" e "unione" distanti non più di alcune parole una dall'altra. Per altre informazioni, vedere [Logical Operators in Search Expressions](../ide/logical-operators-in-search-expressions.md) (Operatori logici nelle espressioni di ricerca).  
  
### <a name="filters"></a>Filtri  
È possibile limitare ulteriormente i risultati di ricerca usando gli operatori di ricerca avanzata. La Guida include tre categorie che è possibile usare per filtrare i risultati della ricerca full-text: titolo, codice e parola chiave.
  
### <a name="ranking-of-search-results"></a>Classificazione dei risultati di ricerca  
L'algoritmo di ricerca applica determinati criteri per consentire la classificazione superiore o inferiore dei risultati di ricerca nell'elenco dei risultati. In generale:  
  
1.  I contenuti che includono le parole di ricerca nel titolo sono classificati a un livello superiore rispetto ai contenuti che non le includono.  
  
2.  I contenuti che includono parole molto simili alle parole di ricerca sono classificati a un livello superiore rispetto ai contenuti che non le includono.  
  
3.  I contenuti che contengono una densità maggiore delle parole di ricerca sono classificati a un livello superiore rispetto ai contenuti che hanno una densità inferiore.  
  
### <a name="stopwords"> Parole ignorate nelle ricerche (parole non significative) </a>
Alcune parole o numeri molto comuni, definiti a volte parole non significative, vengono ignorati automaticamente durante la ricerca full-text. Ad esempio, se si cerca la frase "passare a", i risultati visualizzeranno gli argomenti contenenti la parola "passare" ma non "a".  
  
## <a name="see-also"></a>Vedere anche
[Operatori logici e avanzati](../ide/logical-operators-in-search-expressions.md)  
[Procedura: Trovare argomenti nell'indice](../ide/how-to-find-topics-in-the-index.md)  
[Procedura: Trovare argomenti nel sommario](../ide/how-to-find-topics-in-the-table-of-contents.md)  
[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)