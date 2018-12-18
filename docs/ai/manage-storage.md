---
ms.technology: vs-ai-tools
ms.openlocfilehash: b941d0ba55c540de4bda1cb0f9c4ed18ceab524f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Esplorare lo spazio di archiviazione per caricare dati o per scaricare modelli e log

È possibile esplorare tutto lo spazio di archiviazione nel computer remoto o in una condivisione file di Azure per abilitare il caricamento dei dati o il download di modelli e log. È anche possibile usare il browser processi per accedere ai log e all'output per un processo specifico.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Per accedere a tutti i dati nel computer remoto o nella condivisione file
1. Aprire **Esplora server**
2. Espandere il contesto di calcolo del computer remoto o di Batch per intelligenza artificiale
3. Fare clic con il pulsante destro del mouse su **Archiviazione** e quindi scegliere **Sfoglia**

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Per accedere ai dati specifici di un processo nel computer remoto o nella condivisione file
1. Aprire [Cronologia processi](job-details.md)
2. Selezionare il processo
3. Fare clic su **Cartella di lavoro** oppure fare clic su StdOut/Stderr per l'accesso rapido a questi file di log importanti

    ![storage](media\manage-storage\job-workingfolder.png)
