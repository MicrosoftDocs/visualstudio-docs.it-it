---
title: 'Procedura: utilizzare la finestra di progettazione importazioni | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: cfa65ee24b99fd81712ec88e45f44bb2ed42c21a
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-the-imports-designer"></a>Procedura: utilizzare la finestra di progettazione importazioni
La finestra di progettazione importazioni consente di immettere gli spazi dei nomi per i tipi usati nelle espressioni. Analogamente il **Importa** o **utilizzando** parole chiave in Visual Basic e c#, che specifica gli spazi dei nomi nella finestra di progettazione importazioni consentono di immettere un nome di tipo in un'espressione anziché un nome completo nome del tipo di versione.  
  
 Sulla finestra di progettazione importazioni influiscono sia le modifiche all'interfaccia utente che quelle eseguite quando viene salvato il flusso di lavoro. Quando viene salvato il flusso di lavoro, alla finestra di progettazione importazioni è possibile aggiungere automaticamente spazi dei nomi, tra cui:  
  
-   Spazi dei nomi per qualsiasi tipo usato nelle dichiarazioni di variabili e argomenti.  
  
-   Spazi dei nomi per qualsiasi tipo usato nelle espressioni.  
  
-   Qualsiasi altro spazio dei nomi necessario per la serializzazione del flusso di lavoro (ad esempio, gli spazi dei nomi usati da attività personalizzate rilasciate nel flusso di lavoro).  
  
 Quando viene salvato il flusso di lavoro, è possibile notare che alcuni spazi dei nomi eliminati manualmente sono stati aggiunti di nuovo automaticamente alla finestra di progettazione importazioni a causa della logica descritta nell'elenco precedente.  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Per aggiungere uno spazio dei nomi all'elenco degli spazi dei nomi importati  
  
1.  Aprire un'applicazione di servizi di flussi di lavoro WCF, un'applicazione console del flusso di lavoro o un progetto Libreria attività in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] o in un'applicazione flusso di lavoro riallocata.  
  
2.  Fare clic su **importazioni** nella parte inferiore dell'area di disegno principale. Verrà visualizzata la finestra di progettazione importazioni.  
  
3.  Immettere o selezionare uno spazio dei nomi dal controllo dell'elenco a discesa nella parte superiore della finestra di progettazione importazioni.  
  
     Mentre si digita, viene visualizzato un elenco degli spazi dei nomi validi che corrispondono ai caratteri tipizzati.  
  
4.  Premere **invio** per aggiungere lo spazio dei nomi all'elenco.  
  
5.  Se si desidera rimuovere uno spazio dei nomi dall'elenco, selezionare lo spazio dei nomi, quindi premere il **eliminare** sulla tastiera. Si noti che è possibile eliminare uno spazio dei nomi solo se non è valido per qualsiasi motivo, ad esempio se il progetto non fa più riferimento all'assembly che lo contiene.