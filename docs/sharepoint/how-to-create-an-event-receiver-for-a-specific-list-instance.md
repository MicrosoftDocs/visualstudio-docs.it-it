---
title: 'Procedura: creare un ricevitore di eventi per un''istanza di elenco specifico | Documenti Microsoft'
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
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 66801e82f64e23ee24e66c63a62dd895c58389dc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Procedura: creare un ricevitore di eventi per un'istanza di elenco specifica
  Un ricevitore di eventi di istanza di elenco risponde agli eventi che si verificano in qualsiasi istanza di una definizione di elenco. Sebbene il modello del ricevitore di eventi viene abilitata la destinazione di un'istanza di elenco specifico, è possibile modificare un ricevitore di eventi con ambito di una definizione di elenco per rispondere agli eventi in un'istanza di elenco specifico.  
  
 Per impostare come destinazione un'istanza di elenco specifico, nel file Elements. XML per il ricevitore di eventi, sostituire `ListTemplateId` con `ListUrl` e aggiungere l'URL dell'istanza di elenco.  
  
## <a name="creating-a-list-instance-event-receiver"></a>Creazione di un ricevitore di eventi di istanza di elenco  
 La procedura seguente viene illustrato come modificare un ricevitore di eventi di elemento di elenco per rispondere solo a eventi che si verificano in un'istanza di elenco di annunci personalizzato.  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Per modificare un ricevitore di eventi per rispondere a un'istanza di elenco specifico  
  
1.  In un browser aprire il sito di SharePoint.  
  
2.  Nel riquadro di spostamento, **Elenca** collegamento.  
  
3.  Nel **tutto il contenuto del sito** pagina, scegliere il **crea** collegamento.  
  
4.  Nel **crea** finestra di dialogo scegliere la **annunci** tipo, denominare l'annuncio **TestAnnouncements**e quindi scegliere il **crea**pulsante.  
  
5.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un progetto di ricevitore di eventi.  
  
6.  Nel **il tipo di ricevitore di eventi si desidera?** scegliere **eventi elementi elenco**.  
  
    > [!NOTE]  
    >  È inoltre possibile selezionare qualsiasi altro tipo di ricevitore di eventi che definisce l'ambito di una definizione di elenco, ad esempio, **elenco eventi di posta elettronica** o **gli eventi del flusso di lavoro elenco**.  
  
7.  Nel **selezionare l'elemento deve essere l'origine evento?** scegliere **annunci**.  
  
8.  Nel **gestire gli eventi seguenti** elenco, selezionare il **viene aggiunto un elemento** casella di controllo e quindi scegliere il **fine** pulsante.  
  
9. In **Esplora**, sotto EventReceiver1 aprire Elements.xml.  
  
     Il ricevitore di eventi fa riferimento attualmente alla definizione di elenco degli annunci tramite la riga seguente:  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Modificare questa riga nel testo seguente:  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     In questo modo il ricevitore di eventi per rispondere solo a eventi che si verificano nel nuovo **TestAnnouncements** elenco di annunci appena creato. È possibile modificare il `ListURL` attributo per fare riferimento a qualsiasi istanza di elenco nel server SharePoint.  
  
10. Aprire il file di codice per il ricevitore di eventi e inserire un punto di interruzione nel metodo ItemAdding.  
  
11. Premere il tasto F5 per compilare ed eseguire la soluzione.  
  
12. In SharePoint, scegliere il **TestAnnouncements** collegamento nel riquadro di spostamento.  
  
13. Scegliere il **Aggiungi nuovo annuncio** collegamento.  
  
14. Immettere un titolo per l'annuncio e quindi scegliere il **salvare** pulsante.  
  
     Si noti che il punto di interruzione viene raggiunto quando viene aggiunto il nuovo elemento all'elenco di annunci personalizzato.  
  
15. Scegliere il tasto F5 per riprendere.  
  
16. Nel riquadro di spostamento, scegliere il **Elenca** collegamento e quindi scegliere il **annunci** collegamento.  
  
17. Aggiungere un nuovo annuncio.  
  
     Si noti che il ricevitore di eventi non viene attivato sul nuovo annuncio perché il destinatario è configurato per rispondere solo agli eventi nell'istanza di elenco di annuncio personalizzato, **TestAnnouncements**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  