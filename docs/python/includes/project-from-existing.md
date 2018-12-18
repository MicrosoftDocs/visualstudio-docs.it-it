---
ms.topic: include
ms.openlocfilehash: 37079cfaa1204cd8ce7a77e1e2f5aa91ea844ea5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
1. Avviare Visual Studio e selezionare **File > Nuovo > Progetto**.

1. Nella finestra di dialogo **Nuovo progetto** cercare "Python", selezionare il modello "Da codice Python esistente", assegnare al progetto il nome e una posizione e selezionare **OK**.

1. Nella procedura guidata visualizzata impostare il percorso al codice esistente, un filtro per i tipi di file ed eventuali percorsi di ricerca richiesti dal progetto e quindi fare clic su **Avanti**. In caso di dubbi sui percorsi di ricerca, lasciare vuoto il campo.

    ![Nuovo progetto da codice esistente, passaggio 1](../media/projects-from-existing-1.png)

1. Nella finestra di dialogo successiva selezionare il file di avvio per il progetto e selezionare **Avanti**. Se necessario, è possibile selezionare un ambiente; in caso contrario, accettare le impostazioni predefinite. Si noti che la finestra di dialogo visualizza solo i file presenti nella cartella radice. Se il file necessario si trova in una sottocartella, lasciare vuoto il campo del file di avvio e impostarlo successivamente in Esplora soluzioni (vedere descrizione più avanti).

    ![Nuovo progetto da codice esistente, passaggio 2](../media/projects-from-existing-2.png)

1. Selezionare il percorso in cui salvare il file di progetto (un file `.pyproj` su disco). Se applicabile, in questa finestra di dialogo è anche possibile includere il rilevamento automatico di ambienti virtuali e personalizzare il progetto per diversi framework Web. Se non si è certi di queste opzioni, lasciarle impostate sui valori predefiniti.

    ![Nuovo progetto da codice esistente, passaggio 3](../media/projects-from-existing-3.png)

1. Selezionare **Fine**. Visual Studio crea il progetto e lo apre in Esplora soluzioni. Se si vuole spostare il file `.pyproj`, selezionarlo in Esplora soluzioni e scegliere **File > Salva con nome**. Questa azione implica l'aggiornamento dei riferimenti dei file nel progetto, ma non lo spostamento di file di codice.

1. Per impostare un file di avvio diverso, individuare il file in Esplora soluzioni, fare clic con il pulsante destro del mouse e selezionare **Imposta come file di avvio**.