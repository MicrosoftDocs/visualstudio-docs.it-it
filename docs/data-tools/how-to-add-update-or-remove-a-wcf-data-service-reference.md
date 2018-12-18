---
title: 'Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4dba04455c4ac6ea6d124911b836d24ab2ec63ec
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF
Oggetto *servizio riferimento* consente a un progetto di accedere a uno o più [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Utilizzare il **Aggiungi riferimento al servizio** la finestra di dialogo per la ricerca [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] nella soluzione corrente, in locale, una rete LAN o Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-a-service-reference"></a>Aggiunta di un riferimento al servizio

#### <a name="to-add-a-reference-to-an-external-service"></a>Per aggiungere un riferimento a un servizio esterno

1.  In **Esplora**, il nome del progetto che si desidera aggiungere il servizio e quindi fare clic destro **Aggiungi riferimento al servizio**.

     Il **Aggiungi riferimento al servizio** viene visualizzata la finestra di dialogo.

2.  Nel **indirizzo** casella, immettere l'URL per il servizio e quindi fare clic su **passare** per cercare il servizio. Se il servizio implementa sicurezza nome e la password dell'utente, potrebbero essere richieste un nome utente e una password.

    > [!NOTE]
    >  Si consiglia di fare riferimento solo a servizi provenienti da un'origine attendibile. L'aggiunta di riferimenti da un'origine non attendibile può compromettere la sicurezza.

     È anche possibile selezionare l'URL di **indirizzo** elenco, che archivia i 15 URL precedenti in cui sono stati trovati metadati di servizio valido.

     Un indicatore di stato viene visualizzato quando viene eseguita la ricerca. È possibile arrestare la ricerca in qualsiasi momento facendo clic su **arrestare**.

3.  Nel **servizi** elenco, espandere il nodo per il servizio che si desidera utilizzare e selezionare un set di entità.

4.  Nel **Namespace** immettere lo spazio dei nomi che si desidera utilizzare per il riferimento.

5.  Fare clic su **OK** per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy), e i metadati che descrivono il servizio viene aggiunto al file app. config.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Per aggiungere un riferimento a un servizio nella soluzione corrente

1.  In **Esplora**, il nome del progetto che si desidera aggiungere il servizio e quindi fare clic destro **Aggiungi riferimento al servizio**.

     Il **Aggiungi riferimento al servizio** viene visualizzata la finestra di dialogo.

2.  Fare clic su **individuare**.

     Tutti i servizi (entrambi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] e i servizi WCF) nella soluzione corrente vengono aggiunti per il **servizi** elenco.

3.  Nel **servizi** elenco, espandere il nodo per il servizio che si desidera utilizzare e selezionare un set di entità.

4.  Nel **Namespace** immettere lo spazio dei nomi che si desidera utilizzare per il riferimento.

5.  Fare clic su **OK** per aggiungere il riferimento al progetto.

     Viene generato un client del servizio (proxy), e i metadati che descrivono il servizio viene aggiunto al file app. config.

## <a name="updating-a-service-reference"></a>L'aggiornamento di un riferimento al servizio
 Entity Data Model per un [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] talvolta cambia. In questo caso, è necessario aggiornare il riferimento al servizio.

#### <a name="to-update-a-service-reference"></a>Per aggiornare un riferimento al servizio

-   In **Esplora**, fare riferimento al servizio e quindi fare clic su **riferimento al servizio di aggiornamento**.

     Il riferimento viene aggiornato dal percorso originale, mentre il client del servizio viene rigenerato per riflettere le modifiche apportate nei metadati, viene visualizzata una finestra di dialogo di stato di avanzamento.

## <a name="removing-a-service-reference"></a>Rimozione di un riferimento al servizio
 Se un riferimento al servizio non è più utilizzato, è possibile rimuoverlo dalla soluzione.

#### <a name="to-remove-a-service-reference"></a>Per rimuovere un riferimento al servizio

-   In **Esplora**, fare riferimento al servizio e quindi fare clic su **eliminare**.

     Il client del servizio verrà rimosso dalla soluzione e i metadati che descrivono il servizio verranno rimosso dal file app. config.

    > [!NOTE]
    >  Qualsiasi codice che fa riferimento il servizio dovrà essere rimosso manualmente.

## <a name="see-also"></a>Vedere anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)