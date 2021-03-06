---
title: Registrazione eventi per le soluzioni Office
description: Informazioni su come usare il Visualizzatore eventi in Windows per visualizzare i messaggi di eccezione acquisiti dalla Strumenti di Visual Studio per Office Runtime.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fb38c08e807c65845c323671b0c82151f5c8567c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910365"
---
# <a name="event-logging-for-office-solutions"></a>Registrazione eventi per le soluzioni Office
  È possibile usare il Visualizzatore eventi di Windows per visualizzare i messaggi di eccezione acquisiti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando si installano o disinstallano soluzioni Office. Questi messaggi del registratore eventi possono essere usati per risolvere i problemi di installazione e di distribuzione.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="read-the-event-log"></a>Leggi il registro eventi
 Aprire il **Visualizzatore eventi** e applicare un filtro per visualizzare solo gli eventi desiderati.

### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Per leggere il registro eventi in Windows Server 2003 e Windows XP

1. Nel pannello di controllo aprire **strumenti di amministrazione**.

2. Avviare **Visualizzatore eventi**.

3. Nell'elenco dei registri eventi, selezionare **Applicazione**.

4. Scegliere **Filtro** dal menu **Visualizza**.

5. Selezionare **VSTO 4.0** nell'elenco **Origine evento**.

6. Per gli eventi di installazione, digitare **4096** nella casella **ID evento**.

7. Fare clic su **OK** per visualizzare l'elenco filtrato.

### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Per leggere il registro eventi in Windows 7, Windows Vista e Windows Server 2008

1. Nel pannello di controllo aprire **strumenti di amministrazione**.

2. Avviare **Visualizzatore eventi**.

3. Espandere **Registri di Windows**.

4. Nell'elenco dei registri eventi, selezionare **Applicazione**.

5. Scegliere **Filtro registro corrente** dal menu **Azione**.

6. Selezionare **VSTO 4.0** nell'elenco **Origine evento**.

7. Per gli eventi di installazione, digitare **4096** nella casella **ID evento**.

8. Fare clic su **OK** per visualizzare l'elenco filtrato.

   Il Visualizzatore eventi include le informazioni seguenti:

- Il percorso del manifesto della distribuzione per la soluzione.

- Un messaggio che descrive la causa dell'errore o dell'eccezione.

  Questi messaggi di eccezione possono consentire di determinare la causa di un problema di installazione, ad esempio un certificato o un percorso di documento non attendibile oppure un manifesto della distribuzione non valido.

  Dopo la disinstallazione di una soluzione Office, i messaggi di eccezione rimangono nel registro eventi.

  Per visualizzare o registrare i messaggi di eccezione quando si esegue una soluzione Office, vedere eseguire il debug di progetti di [Office](../vsto/debugging-office-projects.md) ed [eseguire il debug di progetti](../vsto/debugging-office-projects.md)di Office.

### <a name="localization"></a>Localizzazione
 Il linguaggio del messaggio di eccezione viene determinato dal linguaggio di runtime di Visual Studio Tools per Office. Ad esempio, se nel computer dell'utente finale è installato il Language Pack giapponese, il messaggio di eccezione viene scritto nel registro eventi in giapponese.

## <a name="disable-the-event-logger"></a>Disabilitare il logger di eventi
 Quando si installano o disinstallano soluzioni Office, il registratore eventi viene attivato per impostazione predefinita. Per disabilitarlo è possibile impostare la variabile di ambiente VSTO_EVENTLOGDISABLED su "1" (uno).

### <a name="to-disable-the-event-log"></a>Per disabilitare il registro eventi

1. Aprire **Sistema** nel Pannello di controllo.

2. Nella scheda **Avanzate** fare clic su **Variabili di ambiente**.

3. Nel riquadro **Variabili di sistema** , fare clic su **Nuovo**.

4. Nella finestra di dialogo **Nuova variabile di sistema** , digitare **VSTO_EVENTLOGDISABLED** nella casella **Nome variabile** .

5. Nella casella **Valore variabile** , digitare **1**.

6. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Risolvere i problemi di distribuzione della soluzione Office](../vsto/troubleshooting-office-solution-deployment.md)
