---
title: 'Procedura dettagliata: Aggiungere ricevitori di eventi | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e028eb4d95495e92718769979f43012319596960
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-add-feature-event-receivers"></a>Procedura dettagliata: aggiungere ricevitori di eventi di funzionalità
  Ricevitori di eventi sono metodi che vengono eseguite quando si verifica uno dei seguenti eventi correlati alle funzionalità in SharePoint:  
  
-   Una funzionalità viene installata.  
  
-   Una funzionalità è attivata.  
  
-   Una funzionalità è disattivata.  
  
-   Rimozione di una funzionalità.  
  
 Questa procedura dettagliata viene illustrato come aggiungere un ricevitore di eventi a una funzionalità in un progetto SharePoint. Vengono illustrate le attività seguenti:  
  
-   Creazione di un progetto vuoto con un ricevitore di eventi.  
  
-   La gestione di **FeatureDeactivating** metodo.  
  
-   Utilizzo del modello oggetto di progetto SharePoint per aggiungere un annuncio all'elenco di annunci.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-feature-event-receiver-project"></a>Creazione di un progetto di ricevitore di eventi di funzionalità  
 Creare innanzitutto un progetto per contenere il ricevitore di eventi.  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Per creare un progetto con un ricevitore di eventi  
  
1.  Nella barra dei menu, scegliere **File**, **New**, **progetto** per visualizzare il **nuovo progetto** la finestra di dialogo.  
  
2.  Espandere il **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
3.  Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello.  
  
     Utilizzare questo tipo di progetto per i ricevitori di eventi perché non hanno alcun modello di progetto.  
  
4.  Nel **nome** immettere **FeatureEvtTest**, quindi scegliere il **OK** pulsante per visualizzare il **Personalizzazione guidata SharePoint**.  
  
5.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, immettere l'URL per il server di sito di SharePoint a cui si desidera aggiungere il nuovo elemento di campo personalizzato oppure utilizzare il percorso predefinito (http://\<*sistema nome*> /).  
  
6.  Nel **qual è il livello di attendibilità per la soluzione SharePoint?** , scegliere il **Distribuisci come soluzione farm** pulsante di opzione.  
  
     Per ulteriori informazioni sulle soluzioni create mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Scegliere il **fine** pulsante e quindi si noti che una funzionalità denominata Feature1 visualizzata sotto il **funzionalità** nodo.  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>Aggiunta di un ricevitore di eventi per la funzionalità  
 Successivamente, aggiungere la funzionalità di un ricevitore di eventi e aggiungere il codice che viene eseguito quando questa caratteristica è disattivata.  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>Per aggiungere un ricevitore di eventi per la funzionalità  
  
1.  Aprire il menu di scelta rapida per il nodo della funzionalità e quindi scegliere **Aggiungi funzionalità** per creare una funzionalità.  
  
2.  Sotto il **funzionalità** nodo, aprire il menu di scelta rapida per **Feature1**, quindi scegliere **Aggiungi ricevitore di eventi** per aggiungere un ricevitore di eventi per la funzionalità.  
  
     Verrà aggiunto un file di codice sotto Funzionalità1. In questo caso, denominato Feature1. EventReceiver.cs o Feature1.EventReceiver.vb, a seconda del linguaggio di sviluppo del progetto.  
  
3.  Se il progetto è scritto in [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], aggiungere il codice seguente all'inizio del ricevitore di eventi se non è già presente:  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  La classe del ricevitore di eventi contiene diversi metodi di commento che agiscono come eventi. Sostituire il **FeatureDeactivating** metodo con le operazioni seguenti:  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>Test del ricevitore di eventi di funzionalità  
 Successivamente, disattivare la funzionalità per verificare se il **FeatureDeactivating** metodo viene generato un annuncio all'elenco di annunci di SharePoint.  
  
#### <a name="to-test-the-feature-event-receiver"></a>Per testare il ricevitore di eventi  
  
1.  Impostare la proprietà del progetto **configurazione distribuzione attiva** proprietà **Nessuna attivazione**.  
  
     Impostazione di questa proprietà impedisce la funzionalità di attivazione in SharePoint e consente di eseguire il debug di ricevitori di eventi. Per ulteriori informazioni, vedere [debug delle soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Scegliere il **F5** chiave per eseguire il progetto e distribuirlo in SharePoint.  
  
3.  Nella parte superiore della pagina Web di SharePoint, aprire il **Azioni sito** menu, quindi scegliere **Impostazioni sito**.  
  
4.  Nel **Azioni sito** sezione la **Impostazioni sito** pagina, scegliere il **Gestisci caratteristiche sito** collegamento.  
  
5.  Nel **funzionalità** pagina, scegliere il **attiva** accanto al pulsante il **FeatureEvtTest Feature1** funzionalità.  
  
6.  Nel **funzionalità** pagina, scegliere il **disattiva** accanto al pulsante il **FeatureEvtTest Feature1** funzionalità e quindi scegliere il **disattivare questa funzionalità**  collegamento di conferma per disattivare la funzionalità.  
  
7.  Scegliere il **Home** pulsante.  
  
     Si noti che in cui viene visualizzato un annuncio di **annunci** elenco dopo la disattivazione della funzionalità.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  