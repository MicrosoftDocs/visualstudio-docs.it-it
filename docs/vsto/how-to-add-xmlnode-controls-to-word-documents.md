---
title: 'Procedura: aggiungere controlli XMLNode ai documenti di Word | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4dd214262f66bfa21cdb168e948c70437487761e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Procedura: aggiungere controlli XMLNode ai documenti di Word
  **Importante** le informazioni in questo argomento relative a Microsoft Word sono presentato in modo esclusivo per il vantaggio e uso di singoli utenti e organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che utilizzano o lo sviluppo programmi che vengono eseguiti in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio 2010, quando Microsoft ha rimosso un'implementazione di una funzionalità specifica relativi a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word potrebbero non essere lette o utilizzate dal singoli individui o organizzazioni negli Stati Uniti o relativi territori, che utilizza o lo sviluppo di programmi eseguibili in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti con licenza prima di tale data o acquistati e concesso in licenza di fuori degli Stati Uniti.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Quando si esegue il mapping di un elemento XML schema non ripetuto a un documento di Microsoft Office Word, Visual Studio aggiunge automaticamente un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo al documento. Per informazioni sul mapping di elementi ripetuti di XML schema, vedere [procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo non è disponibile il **della casella degli strumenti** o **origini dati** finestra e non è possibile creare a livello di codice.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>Per aggiungere un controllo XMLNode a un documento  
  
1.  Nel documento nella finestra di progettazione di Visual Studio, sulla barra multifunzione, fare clic su di **Developer** scheda.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  Nel **XML** gruppo, fare clic su **Schema**.  
  
     Il **modelli e componenti aggiuntivi** verrà visualizzata la finestra di dialogo.  
  
3.  Fare clic su di **XML Schema** scheda.  
  
4.  Fare clic su **aggiungere Schema**.  
  
     Il **Aggiungi Schema** verrà visualizzata la finestra di dialogo.  
  
5.  Selezionare uno schema XML che contiene gli elementi di schema non ripetuto dal **Aggiungi Schema** la finestra di dialogo e fare clic su **aprire**.  
  
     Il **impostazioni Schema** viene visualizzata la finestra di dialogo.  
  
6.  Assegnare un alias o fare clic su **OK** per aggiungere lo schema senza un alias.  
  
     Lo schema viene aggiunto per il **Aggiungi Schema** la finestra di dialogo.  
  
7.  Nel **Aggiungi Schema** la finestra di dialogo, fare clic su **OK**.  
  
8.  Il **struttura XML** Visualizza il riquadro attività.  
  
9. Scegliere l'elemento dello schema non ripetuto il **struttura XML** riquadro attività per aggiungerlo al documento.  
  
     Un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo viene creato e aggiunto al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [XMLNode (controllo)](../vsto/xmlnode-control.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  