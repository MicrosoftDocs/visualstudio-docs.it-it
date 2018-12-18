---
title: Creare query TableAdapter con parametri
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e65809d479c9cac40d7d4c79066e8becd81b09b6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="create-parameterized-tableadapter-queries"></a>Creare query TableAdapter con parametri
Una query con parametri restituisce dati che soddisfano le condizioni di una clausola WHERE all'interno della query. Ad esempio, è possibile aggiungere un parametro a un elenco di clienti in modo da visualizzare solo i clienti di una determinata città aggiungendo `WHERE City = @City` alla fine dell'istruzione SQL che restituisce un elenco di clienti.

 Creare query TableAdapter con parametri in di **Progettazione Dataset**. È anche possibile crearli in un'applicazione di Windows con il **origine dati con parametri** comando il **dati** menu. Il **origine dati con parametri** comando consente di creare controlli nel form in cui è possibile i valori dei parametri di input ed eseguire la query.

> [!NOTE]
> Quando si crea una query con parametri, utilizzare la notazione di parametro che specifica per il database a cui per che desidera scrivere codice. Ad esempio, nelle origini dati Access e OleDb viene usato il punto interrogativo (?) per indicare i parametri, quindi la clausola WHERE risulterebbe simile a `WHERE City = ?`.

> [!NOTE]
> Finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione in uso. Per modificare le impostazioni, utilizzare il **strumenti** dal menu **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-parameterized-tableadapter-query"></a>Creare una query TableAdapter con parametri

#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Per creare una query con parametri in Progettazione DataSet

-   Creare un nuovo oggetto TableAdapter aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati. Per ulteriori informazioni, vedere [creare e configurare gli oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).

     oppure

-   Aggiungere una query a un oggetto TableAdapter esistente aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.

#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Per creare una query con parametri durante la progettazione di un form associato a dati

1.  Selezionare un controllo nel form che sia già associato a un dataset. Per ulteriori informazioni, vedere [controlli binding di Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  Nel **dati** dal menu **Aggiungi Query**.

3.  Completare il **generatore di criteri di ricerca** nella finestra di dialogo aggiungendo una clausola WHERE con i parametri desiderati per l'istruzione SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Per aggiungere una query a un form associato a dati esistente

1.  Aprire il form nel **Progettazione Windows Form**.

2.  Nel **dati** dal menu **Aggiungi Query** o **Smart tag dati**.

    > [!NOTE]
    >  Se **Aggiungi Query** non è disponibile per il **dati** menu, selezionare un controllo nel form che consente di visualizzare i dati di origine si desidera aggiungere la parametrizzazione. Ad esempio, se nel form i dati sono visualizzati in un controllo <xref:System.Windows.Forms.DataGridView>, selezionarlo. Se i dati del form sono visualizzati in controlli singoli, selezionare qualsiasi controllo associato a dati.

3.  Nel **tabella dell'origine dati selezionare** area, selezionare la tabella che si desidera aggiungere parametrizzazione.

4.  Digitare un nome nella **nuovo nome query** casella se si sta creando una nuova query.

     oppure

     Selezionare una query di **nome query esistente** casella.

5.  Nel **testo della Query** , digitare una query che accetta parametri.

6.  Scegliere **OK**.

     Un controllo per il parametro di input e un **carico** pulsante vengono aggiunti al modulo in un <xref:System.Windows.Forms.ToolStrip> controllo.

#### <a name="querying-for-null-values"></a>L'esecuzione di query per i valori null
Parametri TableAdapter possono assegnare valori null quando si desidera eseguire una query per i record che non hanno alcun valore corrente. Ad esempio, si consideri la query seguente è un `ShippedDate` parametro nel relativo `WHERE` clausola:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

 Se si trattasse di una query su un oggetto TableAdapter, è possibile eseguire una query per tutti gli ordini che non sono stati spediti con il codice seguente:

 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

 Per abilitare una query di accettare i valori null:

1.  Nel **Progettazione Dataset**, selezionare la query TableAdapter che deve accettare valori di parametro null.

2.  Nel **proprietà** selezionare **parametri**, quindi fare clic sui puntini di sospensione (**...** ) per aprire la **Editor della raccolta Parameters**.

3.  Selezionare il parametro che ammette valori null e impostare il **AllowDbNull** proprietà `true`.

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)