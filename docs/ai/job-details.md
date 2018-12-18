---
ms.technology: vs-ai-tools
ms.openlocfilehash: f11a66fd06a2b0b3b23d35c3153c5dd26fab282e
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="view-recent-job-performance-and-details"></a>Visualizzare le prestazioni e i dettagli di processi recenti
Dopo l'invio dei processi è possibile visualizzare l'elenco dei processi per controllare il relativo stato, la durata e altri dettagli.

1. In **Esplora server** espandere il contesto di calcolo specifico.
1. Fare doppio clic su **Processi**.
1. Verrà visualizzato l'elenco dei processi inviati a tale contesto di calcolo.
1. Selezionare un **processo** specifico nell'elenco per visualizzare i dettagli

![Monitorare i processi](media\job-details\monitor-jobs.png)

> La cronologia dei processi inviati alle macchine virtuali di Linux viene archiviata nella directory /tmp nella macchina virtuale. La cronologia viene pertanto cancellata a ogni riavvio. Per ottenere un record permanente della cronologia dei processi, configurare la macchina virtuale come contesto di calcolo in Azure Machine Learning, quindi inviare il processo ad Azure Machine Learning selezionando la macchina virtuale come contesto di calcolo.