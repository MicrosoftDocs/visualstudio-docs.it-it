---
title: Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6d898260d14b92bbc740023e01f521f98927b160
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati
È possibile creare controlli associati a dati trascinando elementi dal **origini dati** finestra in Progettazione Windows Form o finestra di progettazione WPF. Ogni elemento di **origini dati** finestra dispone di un controllo predefinito che viene creato quando si trascina la finestra di progettazione. Tuttavia, è possibile scegliere di creare un controllo diverso.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Impostare i controlli da creare per gli oggetti o le tabelle di dati
Prima di trascinare gli elementi che rappresentano le tabelle di dati o oggetti dal **origini dati** finestra, è possibile scegliere di visualizzare tutti i dati in un controllo o per visualizzare ogni colonna o proprietà in un controllo separato.

In questo contesto, il termine *oggetto* fa riferimento a un oggetto business personalizzato, un'entità (in un Entity Data Model) o un oggetto restituito da un servizio.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Per impostare i controlli da creare per gli oggetti o le tabelle di dati

1.  Assicurarsi che sia aperto la finestra di progettazione WPF o in Progettazione Windows Form.

2.  Nel **origini dati** finestra, selezionare l'elemento che rappresenta la tabella di dati o l'oggetto da impostare.

3.  Fare clic sul menu a discesa per l'elemento e quindi fare clic su uno dei seguenti elementi nel menu:

    -   Per visualizzare ogni campo dati in un controllo separato, fare clic su **dettagli**. Quando si trascina l'elemento di dati nella finestra di progettazione, questa azione verrà creato un controllo con associazione a dati diversi per ogni colonna o proprietà della tabella di dati padre o dell'oggetto, insieme alle etichette per ogni controllo.

    -   Per visualizzare tutti i dati in un singolo controllo, selezionare un controllo diverso nell'elenco, ad esempio **DataGrid** o **elenco** in un'applicazione WPF o **DataGridView** in un Windows Form applicazione.

    Se aggiunta di controlli personalizzati che supportano l'associazione a dati e l'elenco dei controlli disponibili dipende dalla progettazione aperta, la versione di .NET Framework il progetto è destinato il **della casella degli strumenti**. Se il controllo che si desidera creare non è presente nell'elenco dei controlli disponibili, è possibile aggiungere il controllo all'elenco. Per ulteriori informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Per informazioni su come creare un controllo Windows Form personalizzato che può essere aggiunto all'elenco di controlli per le tabelle di dati o oggetti nel **origini dati** finestra, vedere [creare un controllo utente Windows Form che supporta dati complessi associazione](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Impostare i controlli da creare per colonne di dati o di proprietà
Prima di trascinare un elemento che rappresenta una colonna o una proprietà di un oggetto di **origini dati** finestra alla finestra di progettazione, è possibile impostare il controllo da creare.

#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Per impostare i controlli da creare per colonne o proprietà

1.  Assicurarsi che sia aperto la finestra di progettazione WPF o in Progettazione Windows Form.

2.  Nel **origini dati** finestra, espandere la tabella desiderata o per visualizzare le colonne o proprietà dell'oggetto.

3.  Selezionare ogni colonna o proprietà per il quale si desidera impostare il controllo da creare.

4.  Fare clic sul menu a discesa per la colonna o proprietà e quindi selezionare il controllo da creare quando l'elemento viene trascinato nella finestra di progettazione.

     L'elenco dei controlli disponibili dipende dalla progettazione aperta, la versione di .NET Framework destinato il progetto e dai controlli personalizzati che supportano l'associazione di dati aggiunti per il **della casella degli strumenti**. Se il controllo da creare nell'elenco dei controlli disponibili, è possibile aggiungere il controllo all'elenco. Per ulteriori informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Per informazioni su come creare un controllo personalizzato che può essere aggiunto all'elenco di controlli per le colonne di dati o le proprietà nel **origini dati** finestra, vedere [creare un controllo utente Windows Form che supporta l'associazione dati semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Se non si desidera creare un controllo per la colonna o proprietà, selezionare **Nessuno** nel menu a discesa. Ciò è utile se si vuole trascinare la tabella padre o l'oggetto nella finestra di progettazione, ma non si desidera includere la colonna specifica o una proprietà.

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)