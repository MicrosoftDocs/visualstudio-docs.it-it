---
title: Glossario di Debugger di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 088f5d5a6b1edfc218b5dbe291d957d903f79702
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-debugger-glossary"></a>Glossario di Debugger di Visual Studio
Di seguito sono termini usati nel [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging SDK.  
  
## <a name="terms"></a>Termini  
 punto di interruzione associato  
 Un'astrazione per un punto di interruzione impostato nel codice. È una relazione uno a uno tra un punto di interruzione associato e un'istruzione del punto di interruzione nel flusso del codice. Quando il codice viene scaricata, possono separare i punti di interruzione associati.  
  
 causalità  
 Fornisce la possibilità di tenere traccia di un thread di esecuzione logico tra più thread fisici, processi e delle macchine e ricostruire lo stack di chiamate del thread logico in qualsiasi punto nel corso della durata del thread.  
  
 contesto del codice  
 Fornisce un'astrazione di una posizione nel codice conosciuto al motore di debug. Per la maggior parte delle architetture in fase di esecuzione, un contesto di codice è un indirizzo nel flusso di istruzioni del programma. Per le lingue utilizzate, in cui codice non può essere rappresentato da istruzioni, un contesto del codice può essere rappresentato con altri mezzi.  
  
 percorso del codice  
 Rappresenta un punto di esecuzione nel codice in cui viene eseguito un ramo o viene eseguita una chiamata di funzione. Una traccia dello stack è essenzialmente un elenco di percorsi di codice della funzione chiamata.  
  
 motore di debug (Germania)  
 Un componente che consente il debug di un'architettura della fase di esecuzione. Un motore di debug funziona in combinazione con il sistema operativo o un interprete e fornisce servizi di debug, ad esempio la valutazione di espressioni, i punti di interruzione e controllo di esecuzione.  
  
 contesto del documento  
 Fornisce un'astrazione di una posizione in un documento di file di origine nota al motore di debug. Per la maggior parte delle lingue, un contesto di documento è una posizione in un file di origine. Per le lingue utilizzate, per cui il file di origine potrebbe non essere testo, un contesto di documento potrebbe essere rappresentato da un altro modo. Vedere anche *posizione documento*.  
  
 posizione di documento  
 Fornisce un'astrazione di una posizione in un file di origine noto all'IDE. Per la maggior parte dei linguaggi, una posizione del documento è una posizione in un file di origine. Per le lingue utilizzate, la posizione di un documento può essere rappresentata in altri modi. Vedere anche *contesto del documento*.  
  
 punto di interruzione di errore  
 Un'astrazione per la descrizione di un errore in un punto di interruzione in sospeso. Un punto di interruzione di errore può descrivere un errore nel percorso del punto di interruzione in sospeso, l'espressione associata con il punto di interruzione in sospeso o altre informazioni che impedisce il punto di interruzione in sospeso dall'associazione in un percorso di codice.  
  
 contesto di valutazione  
 Fornisce un'astrazione di un contesto di programmazione per la valutazione dell'espressione. In genere, un contesto di valutazione è un ambito. Durante la valutazione dell'espressione nel contesto di un'espressione, il contesto di espressione fornisce le regole di ambito che corrispondano il punto di creazione. Ad esempio, il contesto di un'espressione creato in uno stack frame fornirà il contesto per la valutazione di variabili locali, parametri del metodo, i membri di classe (se applicabile) e le variabili globali.  
  
 eccezione intercettata  
 Un'eccezione che viene intercettata da un motore di debug, anche se nessun meccanismo di gestione delle eccezioni nel sia lo stack frame corrente.  
  
 JustMyCode  
 Il concetto di debug solo il codice che appartiene a un utente e l'esclusione di tutto il codice intermedio, ad esempio di codice di sistema, anche se il codice sorgente è disponibile per il codice di sistema.  
  
 punto di interruzione in sospeso  
 Fornisce un'astrazione per i punti di interruzione prima, durante e dopo il codice viene caricato e un modo per virtualizzare i punti di interruzione. Un punto di interruzione:  
  
-   Contiene tutte le informazioni necessarie per associare un punto di interruzione al codice in uno o più programmi.  
  
-   Consente l'associazione in più percorsi di codice in uno o più programmi.  
  
-   Non viene associato al codice.  
  
 Tutti i punti di interruzione in sospeso in un programma vengono controllati per verificare se è possibile associare ogni codice in fase di caricamento. Un punto di interruzione in sospeso si dice che contiene tutti i punti di interruzione associati che viene associato.  
  
 processo  
 Un processo Win32 fisico. Un processo può contenere più programmi. Vedere anche *programma*.  
  
 programma  
 Un singolo spazio dei nomi in esecuzione all'interno di una particolare architettura di runtime. Vedere anche *processo*.  
  
 gestione di debug di sessione (SDM)  
 Gestisce un numero qualsiasi di motori di debug, il debug di un numero qualsiasi di applicazioni in più processi su qualsiasi numero di macchine. A livello di base, il SDM è un multiplexer, di motori di debug. Inoltre, il SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.  
  
 stack frame  
 Rappresenta lo stato di calcolo in un particolare fotogramma e un livello specifico di chiamate di funzione annidata.  
  
 thread  
 La nozione generalizzata di esecuzione basato su stack istruzione in esecuzione in almeno un programma.  
  
 punto di interruzione di avviso  
 Un'astrazione per la descrizione di un avviso in un punto di interruzione in sospeso. Un punto di interruzione di avviso descrive il motivo per cui il punto di interruzione in sospeso non ancora associato a un percorso di codice. È possibile che il codice non è ancora caricato per il percorso descritto dal punto di interruzione in sospeso o per altri motivi.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)