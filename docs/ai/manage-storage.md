---
title: Esplorare lo spazio di archiviazione per caricare dati
description: Informazioni su come è possibile esplorare tutto lo spazio di archiviazione nel computer remoto o nella condivisione file di Azure per abilitare il caricamento dei dati o il download di modelli e log.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: c32fc5f4ceeb090c8c602b01078fd446249f33eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841419"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Esplorare lo spazio di archiviazione per caricare dati o per scaricare modelli e log

È possibile esplorare tutto lo spazio di archiviazione nel computer remoto o in una condivisione file di Azure per abilitare il caricamento dei dati o il download di modelli e log. È anche possibile usare il browser processi per accedere ai log e all'output per un processo specifico.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Per accedere a tutti i dati nel computer remoto o nella condivisione file

1. Aprire il **Esplora server**.
2. Espandere il contesto di calcolo del computer remoto o di Batch per intelligenza artificiale.
3. Fare clic con il pulsante destro del mouse su **Archiviazione** e quindi scegliere **Sfoglia**.

    ![Screenshot di Esplora server con la cartella computer remoti espansa. L'archiviazione viene evidenziata nell'albero delle cartelle ed è selezionata l'opzione Sfoglia nel menu di scelta rapida.](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Per accedere ai dati specifici di un processo nel computer remoto o nella condivisione file

1. Aprire [Cronologia processi](job-details.md)
2. Selezionare il processo.
3. Fare clic su **cartella di lavoro** o su **stdout/stderr** per accedere rapidamente a questi file di log importanti.

    ![Screenshot della finestra del browser del processo in Esplora server. Il processo train_mnist è selezionato e il collegamento cartella di lavoro è selezionato in dettagli processo.](media/manage-storage/job-workingfolder.png)
