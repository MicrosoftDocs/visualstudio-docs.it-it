---
title: 'Procedura: connettersi ai dati di un servizio'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d82e84c8f71b42f5cbe4f6386ed2ceb87b32ffbd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedura: connettersi ai dati di un servizio

Per connettere l'applicazione ai dati restituiti da un servizio, eseguire il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) e selezionando **servizio** sul **scegliere un tipo di origine dati**pagina.

Al termine della procedura guidata, viene aggiunto al progetto un riferimento al servizio e sono immediatamente disponibile nel [finestra Origini dati](add-new-data-sources.md).

> [!NOTE]
> Gli elementi visualizzati nel **origini dati** finestra dipendono dalle informazioni restituite dal servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti affinché il **configurazione guidata origine dati** per creare oggetti associabili. Ad esempio, se il servizio restituisce un dataset non tipizzato, quindi viene visualizzato alcun elemento nella **finestra Origini dati** dopo avere completato la procedura guidata. Questo avviene perché i dataset non tipizzati non forniscono alcuno schema, pertanto la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Per connettere l'applicazione a un servizio

1.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

2.  Selezionare **servizio** sul **scegliere un tipo di origine dati** pagina e quindi fare clic su **Avanti**.

3.  Immettere l'indirizzo del servizio che si desidera utilizzare oppure fare clic su **Discover** per individuare i servizi nella soluzione corrente e quindi fare clic su **passare**.

4.  Facoltativamente, un nuovo **Namespace** possono essere digitati al posto del valore predefinito.

    > [!NOTE]
    > Fare clic su **avanzate** per aprire la [dialogo Configura riferimento al servizio](../data-tools/configure-service-reference-dialog-box.md).

5.  Fare clic su **OK** per aggiungere un riferimento al progetto.

6.  Scegliere **Fine**.

     L'origine dati viene aggiunta per il **origini dati** finestra.

## <a name="next-steps"></a>Passaggi successivi

Per aggiungere funzionalità all'applicazione, selezionare un elemento di **origini dati** finestra e trascinarlo su un form per creare controlli associati. Per ulteriori informazioni, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF a un servizio di dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)