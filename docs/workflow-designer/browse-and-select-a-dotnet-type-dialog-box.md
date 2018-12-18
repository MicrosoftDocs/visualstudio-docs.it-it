---
title: Individuare e selezionare una finestra di dialogo di tipo .NET | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 04aba24d3dffc96fb8e5288d74322258fa77ce19
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Finestra di dialogo Cerca e seleziona un tipo .NET

Nel **proprietà** finestra o finestre di dialogo, finestre di progettazione, ad esempio la finestra di progettazione variabile, quando si seleziona **Cerca tipi...**  da un elenco di tipi di dati, è il **Cerca e seleziona un tipo .NET** la finestra di dialogo (denominata in una forma abbreviata come "browser tipi"). In questa finestra di dialogo è possibile scegliere un tipo dalla visualizzazione albero di assembly e progetti.

 È possibile usare questa finestra di dialogo in numerosi scenari utente, ad esempio:

-   Quando si imposta un tipo di variabile o argomento.

-   Quando si seleziona un tipo per un'attività generica.

-   Quando si aggiunge un oggetto catch all'attività <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> Il browser del tipo può visualizzare i tipi di matrice irregolari, ma non i tipi di matrice multidimensionale. Vedere [matrici irregolari](http://go.microsoft.com/fwlink/?LinkId=195226) e [le matrici multidimensionali](http://go.microsoft.com/fwlink/?LinkId=195227) per informazioni dettagliate.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selezione di un tipo di riferimento o di valore da Browser tipi.

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Per selezionare un tipo di riferimento o di valore dal browser dei tipi

1.  Nel **nome del tipo** , immettere il nome del tipo che si desidera utilizzare.

2.  Eseguire una delle operazioni seguenti:

    -   Quando viene visualizzato il nome del tipo che si desidera utilizzare nella struttura del **nome del tipo** fare doppio clic per selezionare il tipo.

    -   Digitare un numero di caratteri sufficiente nel **nome del tipo** casella per identificare in modo univoco il tipo che si desidera utilizzare e quindi premere INVIO per selezionare il tipo

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Per selezionare un tipo generico dal browser dei tipi

1.  Nel **nome del tipo** casella, digitare il nome di tipo che si desidera utilizzare.

2.  Quando viene visualizzato il nome del tipo che si desidera utilizzare nella struttura del **nome del tipo** casella, fare clic su di esso per selezionarlo e caselle di riepilogo a discesa visualizzare.

     Selezionare il tipo che si desidera utilizzare per chiudere il tipo generico dalle caselle a discesa e quindi fare clic su **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Tipi visualizzati nel browser dei tipi
 I tipi visualizzati nel browser dei tipi possono variare in base alla modalità di avvio di tale browser. Se il browser dei tipi è stato avviato da un progetto flusso di lavoro all'interno di **vs2010**, per impostazione predefinita tutti i tipi negli assembly di riferimento e vengono visualizzati i progetti di riferimento. Se è stato avviato il browser dei tipi all'esterno di un **vs2010** progetto sistema (ad esempio in un'applicazione flusso di lavoro riallocata o in un file di flusso di lavoro autonomo), quindi per impostazione predefinita vengono visualizzati i tipi di tutti gli assembly caricati nel dominio dell'applicazione .

 I tipi del browser dei tipi possono essere filtrati in base agli sviluppatori di ActivityDesigner. Per qualsiasi attività specificata, è possibile visualizzare solo un subset dei tipi. Per l'attività <xref:System.Activities.Statements.TryCatch>, ad esempio, nel browser dei tipi sono visualizzati solo i tipi derivati da <xref:System.Exception>.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtraggio dei risultati della ricerca nel browser dei tipi
 L'elenco di tipi di **nome del tipo** casella diventa più corto durante la digitazione di più caratteri per trovare una corrispondenza. Nell'elenco filtrato vengono visualizzati solo i tipi il cui nome completo inizia con la stringa digitata oppure i tipi il cui nome breve inizia con la stringa digitata.

 Ad esempio:

1.  Digitare **operazione** corrisponde <xref:System.OperationCanceledException> ma non <xref:System.InvalidOperationException>. Per trovare la corrispondenza con <xref:System.InvalidOperationException>, cominciare a digitare System.I o Invalid.

2.  Digitare **generico** corrisponde <xref:System.GenericUriParser> ma non con i tipi di <xref:System.Collections.Generic> dello spazio dei nomi. Per cercare i tipi nello spazio dei nomi <xref:System.Collections.Generic>, digitare il nome completo dello spazio dei nomi.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selezionare un contratto di servizio tramite la finestra di dialogo del browser dei tipi
 Quando si seleziona un tipo di contratto di servizio, il browser del tipo visualizza solo i tipi che dispongono di un attributo di <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Vedere anche

- [Uso degli Activity Designer](../workflow-designer/using-the-activity-designers.md)