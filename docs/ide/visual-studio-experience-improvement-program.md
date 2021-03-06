---
title: Analisi utilizzo software
description: Informazioni su come gestire le impostazioni di privacy in Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c7f425d87ba6316c3a3cab66f2b342b4c1141f4
ms.sourcegitcommit: 5c0e20fc6005bc1f8ca38f4122378c4ac21ba89a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2021
ms.locfileid: "106110597"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Analisi utilizzo software di Visual Studio

Analisi utilizzo software di Visual Studio è stato pensato per aiutare Microsoft a migliorare nel tempo Visual Studio. Il programma [raccoglie informazioni su errori](../ide/diagnostic-data-collection.md), hardware del computer e modalità d'uso di Visual Studio senza interrompere le attività dell'utente al computer. I dati raccolti consentono a Microsoft di identificare le funzionalità da migliorare. Questo documento illustra come acconsentire o rifiutare esplicitamente di partecipare al programma. Quando si rifiuta esplicitamente, si rifiuta esplicitamente la raccolta dei dati di diagnostica **facoltativi** . È **necessaria** una raccolta di dati di diagnostica per assicurarsi che Visual Studio sia protetto, aggiornato e funzioni come previsto. La raccolta dei dati di diagnostica richiesta non sarà interessata dalla scelta di rifiutare esplicitamente la VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Le impostazioni di consenso esplicito per la telemetria VSCEIP non si applicano a "segnala un problema" in Visual Studio. Quando si segnala un problema, i log vengono raccolti e inviati a Microsoft solo quando si fornisce l'autorizzazione facendo clic su "Invia". Se si è interessati a gestire i log prima di inviare a "segnala un problema", vedere la pagina relativa alla [privacy dei dati di feedback](./developer-community-privacy.md) per ulteriori dettagli.

## <a name="opt-in-or-out"></a>Acconsentire o rifiutare

Analisi utilizzo software di Visual Studio è attivato per impostazione predefinita. È possibile disattivarlo o riattivarlo seguendo queste istruzioni:

1. In Visual Studio scegliere **Guida**  >  **inviare commenti e suggerimenti** e quindi selezionare **Impostazioni**.

   Verrà aperta la finestra di dialogo **Analisi utilizzo software di Visual Studio**.

1. Per rifiutare, selezionare **No, non voglio partecipare** e quindi selezionare **OK**. Per acconsentire, selezionare **Sì, voglio partecipare** e quindi selezionare **OK**.

   ![Finestra di dialogo Analisi utilizzo software di Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Impostazioni del Registro di sistema

Se si installa [Build Tools per Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), sarà necessario aggiornare il Registro di sistema per configurare Analisi utilizzo software di Visual Studio. I clienti aziendali possono creare criteri di gruppo per partecipare o meno ad Analisi utilizzo software di Visual Studio impostando criteri basati sul Registro di sistema.

Le relative impostazioni e chiavi del Registro di sistema sono le seguenti:

::: moniker range="vs-2017"

- In un sistema operativo a 64 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- In un sistema operativo a 32 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Quando Criteri di gruppo è abilitato, Key = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- In un sistema operativo a 64 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- In un sistema operativo a 32 bit, chiave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Quando Criteri di gruppo è abilitato, Key = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Voce = **optin**

Valore = (DWORD)

- **0** è stato escluso (disattivare il VSCEIP)
- **1** è stato accettato (attivare il VSCEIP)

> [!CAUTION]
> La modifica non corretta del Registro di sistema potrebbe danneggiare gravemente il sistema. Prima di apportare modifiche al Registro di sistema, si consiglia di effettuare il backup di tutti i dati importanti presenti sul computer. Se si verificano problemi dopo l'applicazione di modifiche manuali, è inoltre possibile utilizzare l'opzione di avvio **Ultima configurazione valido nota** .

Per altre informazioni sui dati raccolti, elaborati o trasmessi da Analisi utilizzo software di Visual Studio, leggere l'[Informativa sulla privacy di Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Vedi anche

* [Diagnostic information collected by Visual Studio](diagnostic-data-collection.md) (Informazioni di diagnostica raccolte da Visual Studio)
* [Opzioni per commenti e suggerimenti in Visual Studio](../ide/feedback-options.md)
* [Come segnalare un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Community degli sviluppatori di Visual Studio](https://aka.ms/feedback/suggest?space=8)
* [Informativa sulla privacy di Microsoft](https://privacy.microsoft.com/privacystatement)
