---
title: 'Procedura dettagliata: Creazione di un oggetto DataTable in Progettazione Dataset | Documenti Microsoft'
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 7df2579f5556e0e35b4203c700ca3f96f46a7d2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Procedura dettagliata: creazione di una DataTable in Progettazione DataSet

Questa procedura dettagliata viene illustrato come creare un <xref:System.Data.DataTable> (senza un TableAdapter) utilizzando il **Progettazione Dataset**. Per informazioni sulla creazione di tabelle di dati che includono gli oggetti TableAdapter, vedere [creare e configurare gli oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  

Le attività illustrate nella procedura dettagliata sono le seguenti:  

-   Crea un nuovo progetto applicazione Windows Form  

-   Aggiunta di un nuovo set di dati all'applicazione  

-   Aggiunta di una nuova tabella di dati al set di dati  

-   Aggiunta di colonne alla tabella di dati  

-   Impostazione della chiave primaria per la tabella  

## <a name="creating-a-new-windows-forms-application"></a>Crea una nuova applicazione Windows Form

### <a name="to-create-a-new-windows-forms-application-project"></a>Per creare un nuovo progetto di applicazione Windows Forms  
  
1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .  
  
2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.  

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.  

4. Denominare il progetto **nome DataTableWalkthrough**, quindi scegliere **OK**. 
  
     Il **nome DataTableWalkthrough** progetto viene creato e aggiunto a **Esplora**.  

## <a name="adding-a-new-dataset-to-the-application"></a>Aggiunta di un nuovo set di dati all'applicazione

### <a name="to-add-a-new-dataset-item-to-the-project"></a>Per aggiungere un nuovo elemento di set di dati al progetto  
  
1.  Nel **progetto** dal menu **Aggiungi nuovo elemento...** .  
  
     Verrà visualizzata la finestra di dialogo Aggiungi nuovo elemento.  
  
2.  Nel riquadro a sinistra, selezionare **dati**, quindi selezionare **DataSet** nel riquadro centrale.  
  
3.  Scegliere **Aggiungi**.  
  
     Visual Studio aggiunge un file denominato **DataSet1.xsd** al progetto e aprirlo nel **Progettazione Dataset**.  

## <a name="adding-a-new-datatable-to-the-dataset"></a>Aggiunta di un nuovo DataTable al set di dati  

### <a name="to-add-a-new-data-table-to-the-dataset"></a>Per aggiungere una nuova tabella di dati al set di dati  
  
1.  Trascinare un **DataTable** dal **set di dati** scheda della finestra il **della casella degli strumenti** sul **Progettazione Dataset**.  
  
     Una tabella denominata **DataTable1** viene aggiunto al set di dati.  
   
2.  Fare clic sulla barra del titolo di **DataTable1** e rinominarlo `Music`.  

## <a name="adding-columns-to-the-datatable"></a>Aggiunta di colonne alla tabella di dati

### <a name="to-add-columns-to-the-datatable"></a>Per aggiungere colonne alla tabella di dati  
  
1.  Fare doppio clic su di **musica** tabella. Scegliere **Aggiungi**, quindi fare clic su **colonna**.  
  
2.  Nome della colonna `SongID`.  
  
3.  Nel **proprietà** finestra, impostare il <xref:System.Data.DataColumn.DataType%2A> proprietà <xref:System.Int16?displayProperty=fullName>.  
  
4.  Ripetere questo processo e aggiungere le colonne seguenti:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Impostazione della chiave primaria per la tabella

Tutte le tabelle di dati devono avere una chiave primaria. Una chiave primaria identifica in modo univoco un record specifico in una tabella dati.  
  
### <a name="to-set-the-primary-key-of-the-data-table"></a>Per impostare la chiave primaria della tabella di dati
  
-   Fare doppio clic su di **SongID** colonna e quindi fare clic su **Imposta chiave primaria**.  
  
     Icona di una chiave viene visualizzato accanto al **SongID** colonna.  
  
## <a name="saving-your-project"></a>Salvare il progetto  
  
### <a name="to-save-the-datatablewalkthrough-project"></a>Per salvare il progetto DataTableWalkthrough  
  
-   Nel **File** menu, fare clic su **Salva tutto**.  

## <a name="see-also"></a>Vedere anche

[Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
[Convalida dei dati](../data-tools/validate-data-in-datasets.md)  
[Salvataggio di dati](../data-tools/saving-data.md)