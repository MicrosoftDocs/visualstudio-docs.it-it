---
title: La registrazione degli eventi per le soluzioni Office | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0c8a304b314fe09536e2659f88bfdbf53c58552c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="event-logging-for-office-solutions"></a>Registrazione degli eventi per le soluzioni Office
  È possibile usare il Visualizzatore eventi di Windows per visualizzare i messaggi di eccezione acquisiti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando si installano o disinstallano soluzioni Office. Questi messaggi del registratore eventi possono essere usati per risolvere i problemi di installazione e di distribuzione.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="reading-the-event-log"></a>Lettura del registro eventi  
 Aprire il **Visualizzatore eventi** e applicare un filtro per visualizzare solo gli eventi desiderati.  
  
#### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Per leggere il registro eventi in Windows Server 2003 e Windows XP  
  
1.  Aprire **Strumenti di amministrazione**nel Pannello di controllo.  
  
2.  Avviare il **Visualizzatore eventi**.  
  
3.  Nell'elenco dei registri eventi, selezionare **Applicazione**.  
  
4.  Scegliere **Filtro** dal menu **Visualizza**.  
  
5.  Selezionare **VSTO 4.0** nell'elenco **Origine evento**.  
  
6.  Per gli eventi di installazione, digitare **4096** nella casella **ID evento**.  
  
7.  Fare clic su **OK** per visualizzare l'elenco filtrato.  
  
#### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Per leggere il registro eventi in Windows 7, Windows Vista e Windows Server 2008  
  
1.  Aprire **Strumenti di amministrazione**nel Pannello di controllo.  
  
2.  Avviare il **Visualizzatore eventi**.  
  
3.  Espandere **Registri di Windows**.  
  
4.  Nell'elenco dei registri eventi, selezionare **Applicazione**.  
  
5.  Scegliere **Filtro registro corrente** dal menu **Azione**.  
  
6.  Selezionare **VSTO 4.0** nell'elenco **Origine evento**.  
  
7.  Per gli eventi di installazione, digitare **4096** nella casella **ID evento**.  
  
8.  Fare clic su **OK** per visualizzare l'elenco filtrato.  
  
 Il Visualizzatore eventi include le informazioni seguenti:  
  
-   Il percorso del manifesto della distribuzione per la soluzione.  
  
-   Un messaggio che descrive la causa dell'errore o dell'eccezione.  
  
 Questi messaggi di eccezione possono consentire di determinare la causa di un problema di installazione, ad esempio un certificato o un percorso di documento non attendibile oppure un manifesto della distribuzione non valido.  
  
 Dopo la disinstallazione di una soluzione Office, i messaggi di eccezione rimangono nel registro eventi.  
  
 Per visualizzare o registrare messaggi di eccezione durante l'esecuzione di una soluzione Office, vedere [il debug di progetti di Office](../vsto/debugging-office-projects.md) e [il debug di progetti di Office](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Localizzazione  
 Il linguaggio del messaggio di eccezione viene determinato dal linguaggio di runtime di Visual Studio Tools per Office. Ad esempio, se nel computer dell'utente finale è stato installato il Language Pack giapponese, il messaggio di eccezione viene scritto nel registro eventi in giapponese.  
  
## <a name="disabling-the-event-logger"></a>Disattivazione del registratore eventi  
 Quando si installano o disinstallano soluzioni Office, il registratore eventi viene attivato per impostazione predefinita. Per disabilitarlo è possibile impostare la variabile di ambiente VSTO_EVENTLOGDISABLED su "1" (uno).  
  
#### <a name="to-disable-the-event-log"></a>Per disabilitare il registro eventi  
  
1.  Aprire **Sistema**nel Pannello di controllo.  
  
2.  Nella scheda **Avanzate** fare clic su **Variabili di ambiente**.  
  
3.  Nel riquadro **Variabili di sistema** , fare clic su **Nuovo**.  
  
4.  Nella finestra di dialogo **Nuova variabile di sistema** , digitare **VSTO_EVENTLOGDISABLED** nella casella **Nome variabile** .  
  
5.  Nella casella **Valore variabile** , digitare **1**.  
  
6.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Risoluzione dei problemi relativi alla distribuzione di soluzioni Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  