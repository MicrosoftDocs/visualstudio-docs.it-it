---
title: Impostare i valori predefiniti per le distribuzioni aziendali
description: Informazioni sui criteri di dominio e altre operazioni di configurazione per la distribuzione aziendale di Visual Studio.
ms.date: 04/13/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b32c56e418631bfc8f5435d0eb113c9da2296ae9
ms.sourcegitcommit: 3985d0ae8d6332f4682c82a10897763173d52961
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2021
ms.locfileid: "107386005"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Impostare i valori predefiniti per le distribuzioni aziendali di Visual Studio

È possibile impostare i criteri del Registro di sistema che influiscono sulla distribuzione di Visual Studio. Questi criteri sono globali per il computer e influiscono su:

- Dove vengono installati alcuni pacchetti condivisi con altre versioni o istanze
- Dove e se i pacchetti vengono memorizzati nella cache
- Come applicare gli aggiornamenti dell'amministratore

È possibile impostare alcuni di questi criteri usando le [opzioni della riga di comando](use-command-line-parameters-to-install-visual-studio.md), impostare i valori del Registro di sistema nel computer in uso o persino distribuirli tramite Criteri di gruppo all'interno dell'organizzazione.

## <a name="registry-keys"></a>Chiavi del Registro di sistema

Esistono diverse posizioni in cui è possibile impostare le impostazioni predefinite aziendali per abilitarne il controllo tramite Criteri di gruppo o direttamente nel Registro di sistema. Visual Studio controlla in modo sequenziale se sono stati impostati criteri aziendali; non appena viene trovato un valore di criteri nell'ordine seguente, le chiavi rimanenti vengono ignorate.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (in sistemi operativi a 64 bit)

Se non sono ancora impostati, alcuni valori del Registro di sistema vengono impostati automaticamente al primo utilizzo. In questo modo si garantisce che eventuali installazioni successive usino gli stessi valori, che vengono archiviati nella seconda chiave del Registro di sistema: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

È possibile impostare i valori del Registro di sistema seguenti:

::: moniker range="vs-2017"
| **Nome** | **Tipo** | **Default** | **Descrizione** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Directory in cui vengono archiviati i manifesti di pacchetto e, facoltativamente, i payload. Per altre informazioni, vedere [Disabilitare o spostare la pagina della cache dei](disable-or-move-the-package-cache.md) pacchetti. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Consente di mantenere i payload dei pacchetti anche dopo l'installazione. È possibile modificare questo valore in qualsiasi momento. Disabilitando questi criteri vengono rimossi tutti i payload di pacchetti memorizzati nella cache per l'istanza da riparare o modificare. Per altre informazioni, vedere [Disabilitare o spostare la pagina della cache dei](disable-or-move-the-package-cache.md) pacchetti. |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Directory in cui sono installati alcuni pacchetti condivisi tra più versioni di istanze di Visual Studio. È possibile modificare il valore in qualsiasi momento, ma influirà solo sulle installazioni future. I prodotti già installati nel percorso precedente non devono essere spostati o potrebbero non funzionare correttamente. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 0 | Impedire al programma di installazione di scaricare automaticamente gli aggiornamenti per tutti i prodotti Visual Studio installati. È possibile modificare questo valore in qualsiasi momento. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 0 | Consente l'applicazione degli aggiornamenti dell'amministratore al computer client. Se questo valore è mancante o è impostato su 0, gli aggiornamenti dell'amministratore verranno bloccati. Questo valore è per uso amministrativo. Per altre informazioni, vedere [Abilitazione degli aggiornamenti dell'amministratore](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 0 | Indica che l'utente non vuole ricevere gli aggiornamenti dell'amministratore Visual Studio. L'assenza del valore del Registro di sistema o di un valore impostato pari a 0 indica che l'utente Visual Studio desidera ricevere gli aggiornamenti dell'amministratore per Visual Studio. Questo è per gli utenti sviluppatori (se hanno le autorizzazioni di amministratore nel computer client). Per altre informazioni, vedere [Applicazione degli aggiornamenti dell'amministratore](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | Percorso del file per la configurazione degli aggiornamenti amministrativi. Per altre informazioni, vedere [Metodi per la configurazione di un aggiornamento amministratore.](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update) | 
::: moniker-end

::: moniker range="vs-2019"
| **Nome** | **Tipo** | **Default** | **Descrizione** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Directory in cui vengono archiviati i manifesti di pacchetto e, facoltativamente, i payload. Per altre informazioni, vedere [Disabilitare o spostare la pagina della cache dei](disable-or-move-the-package-cache.md) pacchetti. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Consente di mantenere i payload dei pacchetti anche dopo l'installazione. È possibile modificare questo valore in qualsiasi momento. Disabilitando questi criteri vengono rimossi tutti i payload di pacchetti memorizzati nella cache per l'istanza da riparare o modificare. Per altre informazioni, vedere [Disabilitare o spostare la pagina della cache dei](disable-or-move-the-package-cache.md) pacchetti. |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Directory in cui sono installati alcuni pacchetti condivisi tra più versioni di istanze di Visual Studio. È possibile modificare il valore in qualsiasi momento, ma influirà solo sulle installazioni future. I prodotti già installati nel percorso precedente non devono essere spostati o potrebbero non funzionare correttamente. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 0 | Impedire al programma di installazione di scaricare automaticamente gli aggiornamenti per tutti i prodotti Visual Studio installati. È possibile modificare questo valore in qualsiasi momento. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 0 | Consente di applicare gli aggiornamenti dell'amministratore al computer client. Se questo valore è mancante o è impostato su 0, gli aggiornamenti dell'amministratore verranno bloccati. Questo valore è per uso amministrativo. Per altre informazioni, vedere [Abilitazione degli aggiornamenti dell'amministratore.](enabling-administrator-updates.md) | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 0 | Indica che l'utente non desidera ricevere gli aggiornamenti dell'amministratore per Visual Studio. L'assenza del valore del Registro di sistema o di un valore impostato pari a 0 indica che l'utente Visual Studio desidera ricevere gli aggiornamenti dell'amministratore per Visual Studio. È per gli utenti sviluppatori (se hanno autorizzazioni di amministratore nel computer client). Per altre informazioni, vedere [Applicazione degli aggiornamenti dell'amministratore.](../install/applying-administrator-updates.md#understanding-configuration-options) | 
| `UpdateConfigurationFile` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | Percorso del file per la configurazione degli aggiornamenti amministrativi. Per altre informazioni, vedere [Metodi per la configurazione di un aggiornamento amministratore.](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update) | 
| `BaselineStickinessVersions2019` | `REG_SZ` o `REG_EXPAND_SZ` | `16.7.0` | Versione secondaria della baseline di manutenzione su cui deve rimanere il client. Per altre informazioni, vedere [la pagina Applicazione degli aggiornamenti dell'amministratore.](../install/applying-administrator-updates.md#understanding-configuration-options) | 
::: moniker-end

> [!IMPORTANT]
> Se si modificano i criteri del Registro di sistema `CachePath` dopo un'installazione, è necessario spostare la cache del pacchetto esistente nel nuovo percorso e verificare che sia protetto in modo che `SYSTEM` e `Administrators` abbiano il controllo completo e `Everyone` l'accesso in lettura.
> Se non si sposta o non si protegge la cache esistente, è possibile che si verifichino problemi con le installazioni future.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

- [Installa Visual Studio](install-visual-studio.md)
- [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
- [Applicazione degli aggiornamenti dell'amministratore](applying-administrator-updates.md)
- [Disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md)
- [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
