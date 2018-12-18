---
title: Aggiungere controlli personalizzati alla finestra Origini dati
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5961498518d8f2a1137134f88f7961f1c9395937
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Aggiungere controlli personalizzati alla finestra Origini dati
Quando si trascina un elemento di **origini dati** finestra all'area di progettazione per creare un controllo con associazione a dati, è possibile selezionare il tipo di controllo da creare. Un elenco di riepilogo a discesa che visualizza i controlli che è possibile scegliere tra ogni elemento nella finestra. Il set di controlli associati a ogni elemento è determinato dal tipo di dati dell'elemento. Se il controllo che si desidera creare non viene visualizzato nell'elenco, è possibile seguire le istruzioni in questo argomento per aggiungere il controllo all'elenco.

 Per ulteriori informazioni sulla selezione di controlli con associazione a dati da creare per gli elementi di **origini dati** finestra, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere il **strumenti** dal menu **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

##  <a name="customizinglist"></a> Personalizzare l'elenco dei controlli associabili per un tipo di dati
 Per aggiungere o rimuovere controlli dall'elenco dei controlli disponibili per gli elementi di **origini dati** finestra che hanno un tipo di dati specifico, eseguire la procedura seguente.

#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Per selezionare i controlli devono essere elencati per un tipo di dati

1.  Assicurarsi che sia aperto la finestra di progettazione WPF o Progettazione Windows Form.

2.  Nel **origini dati** finestra, fare clic su un elemento che fa parte di un'origine dati è stato aggiunto alla finestra e quindi fare clic sul menu di riepilogo a discesa per l'elemento.

3.  Nel menu a discesa, fare clic su **Personalizza**. Consente di aprire una delle finestre di dialogo seguenti:

    -   Se Progettazione Windows Form è aperto, il **personalizzazione dell'interfaccia utente dati** pagina del **opzioni** verrà visualizzata la finestra di dialogo.

    -   Se la finestra di progettazione WPF è aperto, il **Personalizza associazione controllo** verrà visualizzata la finestra di dialogo.

4.  Nella finestra di dialogo, selezionare un tipo di dati dal **tipo di dati** elenco a discesa.

    -   Per personalizzare l'elenco dei controlli per una tabella o oggetto, selezionare **[elenco]**.

    -   Per personalizzare l'elenco dei controlli per una colonna di una tabella o una proprietà di un oggetto, selezionare il tipo di dati della colonna o proprietà nell'archivio dati sottostante.

    -   Per personalizzare l'elenco dei controlli per visualizzare gli oggetti dati che dispongono di forme definite dall'utente, selezionare **[altro]**. Ad esempio, selezionare **[altro]** se l'applicazione dispone di un controllo personalizzato che consente di visualizzare dati da più di una proprietà di un oggetto specifico.

5.  Nel **relativi controlli** selezionare ogni controllo che si desidera rendere disponibili per il tipo di dati selezionato o cancellare la selezione di tutti i controlli che si desidera rimuovere dall'elenco.

    > [!NOTE]
    >  Se il controllo che si desidera selezionare non viene visualizzato nel **relativi controlli** casella, è necessario aggiungere il controllo all'elenco. Per ulteriori informazioni, vedere [aggiunta di controlli all'elenco di controlli associati a un tipo di dati](#addingcontrols).

6.  Fare clic su **OK**.

7.  Nel **origini dati** finestra, fare clic su un elemento di dati che sono stati appena associati uno o più controlli di tipo, quindi il menu a discesa per l'elemento.

     I controlli selezionati nel **relativi controlli** ora visualizzata nella casella a discesa per l'elemento.

##  <a name="addingcontrols"></a> Aggiungere controlli all'elenco dei controlli associati per un tipo di dati
 Se si desidera associare un controllo a un tipo di dati, ma il controllo non viene visualizzato nel **relativi controlli** casella, è necessario aggiungere il controllo all'elenco. Il controllo deve essere posizionato nella soluzione corrente o in un assembly di riferimento. Deve inoltre essere disponibile nel **della casella degli strumenti**, e ha un attributo che specifica il comportamento di associazione di dati del controllo.

#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Per aggiungere controlli all'elenco di controlli associati

1.  Aggiungere il controllo desiderato per il **della casella degli strumenti** facendo clic con il **della casella degli strumenti** e selezionando **Scegli elementi**.

     Il controllo deve avere uno dei seguenti attributi.

    |Attributo|Descrizione|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementare questo attributo su controlli semplici che consentono di visualizzare una singola colonna o proprietà, dei dati, ad esempio un <xref:System.Windows.Forms.TextBox>.|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementare questo attributo sui controlli che visualizzano elenchi o tabelle di dati, ad esempio un <xref:System.Windows.Forms.DataGridView>.|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementare questo attributo sui controlli che visualizzano elenchi o tabelle di dati, ma anche presentare una singola colonna o proprietà, è necessario, ad esempio un <xref:System.Windows.Forms.ComboBox>.|

2.  Per Windows Form, nel **opzioni** la finestra di dialogo, aprire il **personalizzazione dell'interfaccia utente dati** pagina. In alternativa, per WPF, aprire il **Personalizza associazione controllo** la finestra di dialogo. Per ulteriori informazioni, vedere [personalizzazione dell'elenco di controlli associabili per un tipo di dati](#customizinglist).

3.  Nel **relativi controlli** casella, il controllo appena aggiunto per il **della casella degli strumenti** dovrebbe ora essere visualizzato.

    > [!NOTE]
    >  Solo i controlli che si trovano all'interno della soluzione corrente o in un assembly di riferimento possono essere aggiunti all'elenco di controlli associati. (I controlli devono inoltre implementare uno degli attributi di associazione di dati nella tabella precedente.) Per associare dati a un controllo personalizzato che non è disponibile nel **origini dati** finestra, trascinare il controllo dal **della casella degli strumenti** nell'area di progettazione e quindi trascinare l'elemento da associare dal **dati Origini** finestra al controllo.

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)