---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: a55b2a12c9a45c5a3952e3e6f4e1627bec8ba520
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
1. Nel **Esplora**del mouse sul nodo del progetto e scegliere **pubblica** (per Web Form, **pubblicare App Web**).

2. Nel **pubblica** nella finestra di dialogo **cartella**, fare clic su **Sfoglia**e creare una nuova cartella **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Per un'app Web Form, scegliere **personalizzato** nella finestra di dialogo pubblica, immettere un nome di profilo e scegliere **OK**.

3. Fare clic su **Pubblica**.

    Visual Studio pubblica il progetto nella cartella. Stato di avanzamento Mostra nella finestra di Output.

4. Nel **pubblica** la finestra di dialogo, fare clic sul **impostazioni** collegamento e quindi selezionare il **impostazioni** scheda.

5. Impostare la configurazione su **Debug**selezionare **Elimina tutti i file esistenti prima della pubblicazione**, quindi fare clic su **salvare**.

    > [!NOTE]
    > Se si utilizza una build di rilascio, disabilitare il debug nel file Web. config quando esegue la pubblicazione.

6. Fare clic su **Pubblica**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    Pubblica l'applicazione un **Debug** configurazione del progetto nella cartella locale.

5. Copiare la directory del progetto ASP.NET dal computer di Visual Studio nella directory locale configurata per l'applicazione ASP.NET (in questo esempio, **C:\Publish**) nel computer del Server di Windows. In questa esercitazione si presuppone che si sta copiando manualmente, ma è possibile utilizzare altri strumenti come PowerShell, Xcopy o Robocopy.

    > [!CAUTION]
    >  Se è necessario apportare modifiche al codice o di ricompilazione, è necessario ripubblicare e ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.

6. In Windows Server, verificare che sia possibile eseguire correttamente l'app, aprire l'app nel browser.

    Se l'app non viene eseguito correttamente, può essere presente una mancata corrispondenza tra la versione di ASP.NET installati sul server e computer di Visual Studio oppure si potrebbe avere un problema con la configurazione di IIS o il sito Web. Controlla di nuovo i passaggi precedenti.