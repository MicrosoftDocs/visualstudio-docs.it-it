---
title: Aggiungere archiviazione di Azure usando Servizi connessi
description: Aggiungere archiviazione di Azure all'applicazione usando la finestra di dialogo Aggiungi servizi connessi di Visual Studio
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 3acb009d27a9fa47f890235f6957d1f29ed2f4a0
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916688"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Aggiunta dell’archiviazione di Azure tramite Servizi connessi di Visual Studio
Con Visual Studio è possibile connettere uno dei servizi seguenti ad Archiviazione di Azure tramite la finestra di dialogo **Add Connected Services** (Aggiungi servizi connessi):

- Servizio cloud C#
- Servizio mobile back-end .NET
- Sito Web ASP.NET
- Servizio ASP.NET Core
- Servizio Processo Web di Azure

La funzionalità servizio connesso aggiunge al progetto tutti i riferimenti richiesti e il codice di connessione e modifica i file di configurazione in modo appropriato.

Dopo il completamento, la finestra di dialogo **Add Connected Services** (Aggiungi servizi connessi) visualizza automaticamente la documentazione che illustra in dettaglio i passaggi necessari per iniziare a lavorare con l'archiviazione BLOB, le code e le tabelle.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Connettersi ad archiviazione di Azure usando la finestra di dialogo Servizi connessi
1. Aprire il progetto in Visual Studio

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Servizi connessi** e scegliere **Add Connected Services** (Aggiungi servizi connessi) dal menu di scelta rapida.

    ![Aggiunta di un servizio connesso di Azure](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. Nella pagina **Servizi connessi** selezionare **Archiviazione cloud con Archiviazione di Azure**.

    ![Aggiungi Archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Nella finestra di dialogo **Archiviazione di Azure** selezionare un account di archiviazione esistente, quindi **Aggiungi**.

    Se è necessario creare un account di archiviazione, andare al passaggio successivo. In caso contrario, andare direttamente al passaggio 6.

    ![Aggiungere un account di archiviazione esistente al progetto l'elenco](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Per creare un account di archiviazione:

   1. Nella parte inferiore della finestra di dialogo fare clic su **Crea un nuovo account di archiviazione**.

   1. Compilare la finestra di dialogo **Crea account di archiviazione** e selezionare **Crea**.

       ![Nuovo account di archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Quando viene visualizzata la finestra di dialogo **Archiviazione di Azure**, la nuova risorsa di archiviazione viene visualizzata nell'elenco. Selezionare la nuova risorsa di archiviazione nell'elenco e quindi **Aggiungi**.

1. Il servizio connesso di archiviazione viene visualizzato sotto il nodo **Riferimenti servizio** del progetto.

## <a name="how-your-project-is-modified"></a>Come viene modificato il progetto
Una volta terminata la finestra di dialogo, Visual Studio aggiunge riferimenti e modifica di alcuni file di configurazione. Le modifiche specifiche dipendono dal tipo di progetto.

- Progetti ASP.NET - [Risultati – Progetti ASP.NET](/azure/visual-studio/vs-storage-aspnet-getting-started-blobs).
- Progetti ASP.NET 5 - [Risultati – Progetti ASP.NET 5](/azure/visual-studio/vs-storage-aspnet5-getting-started-blobs).
- Progetti del servizio cloud (ruoli Web e ruoli di lavoro) [Risultati - Progetti del servizio cloud](/azure/visual-studio/vs-storage-cloud-services-getting-started-blobs).
- Progetti di tipo processo Web - [Risultati - Progetti di tipo processo Web](/azure/visual-studio/vs-storage-webjobs-what-happened).

## <a name="next-steps"></a>Passaggi successivi
- [Forum MSDN: Archiviazione di Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog del team di Archiviazione di Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/).
- [Documentazione di Archiviazione di Azure](/azure/storage/)
