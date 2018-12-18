---
title: Finestra Elenco errori | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1c6182bff342204e5f56fe705911ba5ff5f3e57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="error-list-window"></a>Finestra Elenco errori
> [!NOTE]
>  L'elenco degli errori consente di visualizzare informazioni su un messaggio di errore specifico. È possibile copiare il testo della stringa di errore o il numero di errore nella finestra di output. Per visualizzare la finestra di output, selezionare i tasti Ctrl+Alt+O. Vedere [Finestra di output](../../ide/reference/output-window.md).  
  
 È possibile sviluppare applicazioni più velocemente usando la finestra **Elenco errori**. Ad esempio, è possibile effettuare le attività seguenti:  
  
-   Visualizzare gli errori, gli avvisi e i messaggi generati durante scrittura di codice.  
  
-   Individuare gli errori di sintassi indicati da IntelliSense.  
  
-   Individuare errori di distribuzione, alcuni errori di analisi statica, nonché gli errori rilevati durante l'applicazione dei criteri di Modello Enterprise.  
  
-   Fare doppio clic su un messaggio di errore per aprire il file in cui è stato rilevato il problema e visualizzare il punto in cui si è verificato l'errore.  
  
-   Filtrare le voci e le colonne di informazioni visualizzate per ciascuna voce.  
  
-   Cercare i termini specifici e l'ambito della ricerca solo nel progetto corrente o nel documento.  
  
Per visualizzare l'**Elenco errori**, fare clic su**Visualizza/Elenco errori** o premere **CTRL+\\+E**.  
  
È possibile scegliere le schede **Errori**, **Avvisi** e **Messaggi** per visualizzare diversi livelli di informazioni.  
  
Per ordinare l'elenco, fare clic sull'intestazione di una colonna. Per ordinare nuovamente l'elenco in base a una colonna aggiuntiva, fare clic sull'intestazione di un'altra colonna tenendo premuto il tasto MAIUSC. Per selezionare le colonne da visualizzare e quelle da nascondere, scegliere **Mostra colonne** dal menu di scelta rapida. Per modificare l'ordine di visualizzazione delle colonne, trascinare l'intestazione di una colonna verso sinistra o verso destra.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella presente Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, fare clic su **Strumenti/Importa/Esporta impostazioni**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="error-list-filters"></a>Filtri Elenco errori  
 Esistono due tipi di filtro in due caselle a discesa, una sul lato destro della barra degli strumenti e una a sinistra della barra degli strumenti. Nell'elenco a discesa sul lato sinistro della barra degli strumenti viene specificato il set di file di codice da usare (**Intera soluzione**, **Documenti aperti**, **Progetto corrente**, **Documento corrente**).  
  
 È possibile limitare l'ambito di ricerca per analizzare e agire sui gruppi di errori. Ad esempio, è possibile concentrarsi sugli errori principali che impediscono la compilazione di un progetto. Le opzioni di ambito includono:  
  
1.  **Documenti aperti**: visualizza errori, avvisi e messaggi per i documenti aperti.  
  
2.  **Progetto corrente**: visualizza errori, avvisi e messaggi presenti nel progetto del documento attualmente selezionato in **Editor** o nel progetto selezionato in **Esplora soluzioni**.  
  
    > [!NOTE]
    >  L'elenco filtrato di errori, avvisi e messaggi verrà modificato se il progetto del documento attualmente selezionato è diverso dal progetto selezionato in **Esplora soluzioni**.  
  
3.  **Documento corrente**: visualizza errori, avvisi e messaggi per il documento attualmente selezionato in **Editor** o in **Esplora soluzioni**.  
  
Se ai risultati della ricerca è applicato un filtro, il nome del filtro viene visualizzato nella barra del titolo **Elenco errori**. I pulsanti **Errori**, **Avvisi** e **Messaggi** visualizzano il numero di elementi filtrati insieme al numero totale di elementi; ad esempio, i pulsanti visualizzano x di y errori. Se nessun filtro viene applicato, la barra del titolo indica solo "Elenco errori".  
  
L'elenco sul lato destro della barra degli strumenti specifica se visualizzare errori di compilazione (errori risultanti da un'operazione di compilazione) o di IntelliSense (errori rilevati prima di eseguire una compilazione) o di entrambi.  
  
## <a name="search"></a>Cerca  
 Usare la casella di testo **Elenco errori di ricerca** sul lato destro della barra degli strumenti **Elenco errori** per trovare errori specifici nell'elenco errori. È possibile cercare una colonna visibile nell'elenco errori e i risultati di ricerca vengono sempre ordinati in base alla colonna con priorità di ordinamento anziché alla query o al filtro applicato. Se si sceglie il tasto **Esc** mentre è attivo l'**Elenco errori**, è possibile cancellare il termine di ricerca e i risultati di ricerca filtrati. È anche possibile fare clic sulla **X** sul lato destro della casella di testo per cancellare il contenuto.  
  
## <a name="save"></a>Salva  
 È possibile copiare l'elenco errori e salvarlo in un file. Selezionare gli errori da copiare e fare clic con il pulsante destro del mouse sulla selezione, quindi nel menu di scelta rapida selezionare **Copia**. È quindi possibile incollare gli errori in un file. Se si incollano gli errori in un foglio di calcolo di Excel, i campi vengono visualizzati come diverse colonne.  
  
## <a name="ui-element-list"></a>Elenco degli elementi dell'interfaccia utente  
 Gravità  
 Consente di visualizzare i diversi tipi di voci dell'**Elenco errori** (**Errore**, **Messaggio**, **Avviso**, **Avviso (attivo)**, **Avviso (inattivo)**.  
  
 Codice  
 Restituisce il codice di errore.  
  
 Descrizione  
 Visualizza il testo della voce.  
  
 Progetto  
 Visualizza il nome del progetto corrente.  
  
 File  
 Visualizza il nome del file.  
  
 Linea  
 Visualizza la riga in cui si è verificato l'errore.