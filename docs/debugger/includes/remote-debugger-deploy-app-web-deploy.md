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
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
Se è stato installato utilizzando l'installazione guidata piattaforma Web di distribuzione Web, è possibile distribuire l'app direttamente da Visual Studio.

1. Avviare Visual Studio con privilegi di amministratore e riaprire il progetto.

    Per distribuire l'app tramite distribuzione Web sono necessari i privilegi di amministratore.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica**.

3. Per **selezionare una destinazione di pubblicazione**selezionare **IIS, FTP, e così via** e fare clic su **pubblica**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. Immettere i parametri di configurazione della correzione per l'installazione IIS.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Se non si risolve un nome host quando si tenta di convalidare nei passaggi successivi il **Server** testo casella, provare l'indirizzo IP. Includere `http://` come un prefisso nel **Server** campo.  Assicurarsi di utilizzare la porta 80 nel **Server** testo e assicurarsi che la porta 80 sia aperta nel firewall.

6. Fare clic su **Avanti**, scegliere un **Debug** configurazione, scegliere **Rimuovi file aggiuntivi nella destinazione** sotto il **pubblicare File** Opzioni.

    > [!NOTE]
    > Se si sceglie una configurazione di rilascio, disabilitare il debug nel file Web. config quando esegue la pubblicazione.

5. Fare clic su **Prev**, quindi scegliere **convalida**. Se la configurazione della connessione di convalida, è possibile provare a pubblicare.

6. Fare clic su **pubblica** per pubblicare l'app.

    Nella scheda Output Mostra se la pubblicazione ha esito positivo e il browser apre quindi l'app.

    Se si verifica un errore citare distribuzione Web, eseguire nuovamente la procedura di installazione Web Deploy e assicurarsi che siano aperte le porte corrette (distribuzione Web è necessario porta 8172 sia aperta sul server).

    Se l'app viene distribuito correttamente, ma non viene eseguito correttamente, potrebbe esserci un problema con la configurazione di IIS, l'installazione di ASP.NET o la configurazione del sito Web. In Windows Server, aprire il sito Web da IIS per i messaggi di errore più specifici e quindi eseguire nuovamente i passaggi precedenti.