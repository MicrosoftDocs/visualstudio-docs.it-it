---
title: 'Procedura: creare un ricevitore di eventi | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ead81e01022c8f389ad6010c89d0e433b82c542e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-event-receiver"></a>Procedura: creare un ricevitore di eventi
  Creando *ricevitori di eventi*, è possibile rispondere quando un utente interagisce con gli elementi di SharePoint, ad esempio elenchi o elementi di elenco. Ad esempio, il codice in un ricevitore di eventi può essere attivato quando un utente cambia il calendario o elimina un nome da un elenco di contatti. Seguendo questo argomento, viene illustrato come aggiungere un ricevitore di eventi per un'istanza di elenco.  
  
 Per completare questi passaggi, è necessario avere installato [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e le edizioni supportate di Windows e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md). Poiché in questo esempio richiede un progetto SharePoint, è inoltre necessario avere completato la procedura nell'argomento [procedura dettagliata: creazione di una colonna del sito, tipo di contenuto e l'elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## <a name="adding-an-event-receiver"></a>Aggiunta di un ricevitore di eventi  
 Il progetto creato in [procedura dettagliata: creazione di una colonna del sito, il tipo di contenuto e l'elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) include le colonne del sito, un elenco personalizzato e un tipo di contenuto. Nella procedura seguente, si verrà espandere il progetto aggiungendo un gestore di evento semplice (un ricevitore di eventi) a un'istanza di elenco per mostrare come gestire gli eventi che si verificano negli elementi quali gli elenchi di SharePoint.  
  
#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Per aggiungere un ricevitore di eventi per l'istanza di elenco  
  
1.  Aprire il progetto che è stato creato in [procedura dettagliata: creazione di una colonna del sito, tipo di contenuto e l'elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  In **Esplora**, scegliere il nodo di progetto SharePoint, denominato **Clinic**.  
  
3.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
4.  In presenza di **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** elemento.  
  
5.  Nel **modelli** riquadro scegliere **ricevitore di eventi**, denominarla **il nome TestEventReceiver1**e quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzato.  
  
6.  Nel **il tipo di ricevitore di eventi si desidera?** scegliere **eventi elementi elenco**.  
  
7.  Nel **selezionare l'elemento deve essere l'origine evento?** scegliere **pazienti (Clinic\Patients)**.  
  
8.  Nel **gestire gli eventi seguenti** elenco, selezionare la casella di controllo accanto a **è stato aggiunto un elemento**, quindi scegliere il **fine** pulsante.  
  
     Il file di codice per il nuovo ricevitore di eventi contiene un solo metodo denominato `ItemAdded`. Nel passaggio successivo, si aggiungerà codice al metodo in modo che ogni contatto verrà denominato Scott Brown per impostazione predefinita.  
  
9. Sostituire `ItemAdded` metodo con il seguente codice e quindi premere il tasto F5:  
  
     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Il codice viene eseguito e il sito verrà visualizzato nel browser web di SharePoint.  
  
10. Nella barra Avvio veloce scegliere il **pazienti** collegamento e quindi scegliere il **Aggiungi nuovo elemento** collegamento.  
  
     Apre il form di immissione di nuovi elementi.  
  
11. Immettere i dati nei campi e quindi scegliere il **salvare** pulsante.  
  
     Dopo aver scelto il **salvare** pulsante, il **Nome paziente** colonna Aggiorna automaticamente per il nome Scott Brown.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  