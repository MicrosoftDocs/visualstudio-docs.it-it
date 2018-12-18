---
title: Requisiti di sistema per Visual Studio Emulator for Android | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 520cd9eacf494ac1d8f8e26a7e1ef51581a49956
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Requisiti di sistema per Visual Studio Emulator for Android
Visual Studio Emulator per Android viene eseguito come una macchina virtuale in Hyper-V, la tecnologia di virtualizzazione per Windows 8 e versioni successive. Per eseguire l'emulatore, il computer deve soddisfare i requisiti per l'esecuzione di Hyper-V, come descritto in questo argomento.  
  
 Il programma di installazione tenta di configurare automaticamente i prerequisiti quando si installa l'emulatore. Se i prerequisiti vengono configurati correttamente, l'emulatore funziona come previsto. In caso contrario potrebbe essere necessario abilitare i prerequisiti manualmente. Per configurare manualmente i prerequisiti, usare i passaggi e gli strumenti descritti [qui](https://msdn.microsoft.com/en-us/library/windows/apps/jj863509\(v=vs.105\).aspx) per l'emulatore di Windows Phone.  
  
> [!IMPORTANT]
>  Il programma di installazione per l'emulatore verifica i prerequisiti per l'esecuzione di Visual Studio Emulator per Android. Se i prerequisiti non sono presenti, visualizza degli avvisi ma non richiede i prerequisiti.  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
-   [Elenco di controllo rapido](#Checklist)  
  
-   [Requisiti di sistema](#System)  
  
-   [Requisiti di rete](#Network)  
  
-   [Requisiti di Hyper-V](#HyperV)  
  
-   [L'esecuzione dell'emulatore da un VHD di avvio non è supportata](#BootableVHD)  
  
-   [Hyper-V richiede file non compressi e non crittografati](#Files)  
  
##  <a name="Checklist"></a> Elenco di controllo rapido  
 Di seguito è riportato un elenco di controllo rapido dei requisiti per l'esecuzione di Visual Studio Emulator per Android. Per informazioni più dettagliate, vedere le sezioni successive in questo argomento.  
  
 Requisiti di sistema  
  
-   Supporto di Hyper-V (vedere Requisiti di Hyper-V di seguito)  
  
-   6 GB o più di RAM.  
  
-   Versione a 64 bit dell'edizione Pro di Windows 8, Windows 8.1, Windows10 o successive  
  
-   Processore che supporta SSSE3 o versione successiva.  
  
 Requisiti di rete  
  
-   DHCP  
  
-   Impostazioni di DNS e gateway configurate automaticamente  
  
 Requisiti di Hyper-V  
  
-   Nel BIOS, devono essere supportate le funzionalità seguenti:  
  
    -   Virtualizzazione assistita da hardware  
  
    -   Conversione indirizzi di secondo livello  
  
    -   Protezione esecuzione programmi basata su hardware  
  
-   In Windows, Hyper-V deve essere abilitato e in esecuzione.  
  
-   È necessario essere un membro del gruppo di amministratori di Hyper-V locali.  
  
##  <a name="System"></a> Requisiti di sistema  
 Il computer deve soddisfare i seguenti requisiti:  
  
-   Supporto di Hyper-V (vedere [Requisiti di Hyper-V](#HyperV))  
  
-   6 GB o più di RAM.  
  
-   Versione a 64 bit dell'edizione Pro di Windows 8, Windows 8.1, Windows10 o successive.  
  
 Per verificare i requisiti di RAM e di Windows, nel Pannello di controllo scegliere Sistema e sicurezza e quindi scegliere Sistema.  
  
 ![Verificare i requisiti di sistema](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")  
  
##  <a name="Network"></a> Requisiti di rete  
 La rete deve soddisfare i seguenti requisiti:  
  
-   DHCP  
  
     L'emulatore richiede DHCP perché viene configurato automaticamente come un dispositivo separato sulla rete con il relativo indirizzo IP.  
  
-   Impostazioni di DNS e gateway configurate automaticamente  
  
     Non è possibile configurare manualmente le impostazioni di DNS e gateway per l'emulatore.  
  
 Per risolvere i problemi di rete nell'emulatore, vedere gli argomenti seguenti:  
  
-   [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)  
  
##  <a name="HyperV"></a> Requisiti di Hyper-V  
 Requisiti di Hyper-V nel BIOS  
  
 Il BIOS del computer deve supportare i requisiti seguenti e tali requisiti devono essere abilitati:  
  
-   Virtualizzazione assistita da hardware  
  
-   Conversione indirizzi di secondo livello  
  
-   Protezione esecuzione programmi basata su hardware  
  
 Requisiti di Hyper-V in Windows  
  
 Se le impostazioni del computer e del BIOS sono già configurate per supportare Hyper-V, il programma di installazione abilita e avvia Hyper-V. In caso contrario potrebbe essere necessario abilitare i requisiti manualmente.  
  
|Requisito|Come controllare e abilitare questo requisito|  
|-----------------|----------------------------------------------|  
|Hyper-V deve essere installato|Seguire le stesse istruzioni usate per [abilitare Hyper-V per l'emulatore di Windows Phone](https://msdn.microsoft.com/en-us/library/windows/apps/jj863509\(v=vs.105\).aspx).<br /><br /> Controllare lo stato del servizio **Hyper-V Virtual Machine Management** nello snap-in Servizi.|  
|Hyper-V deve essere in esecuzione.|Per altre informazioni sulla gestione dei servizi, vedere gli argomenti seguenti:<br /><br /> -   [Avviare, arrestare, sospendere, riprendere o riavviare un servizio](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Configurare la modalità di avvio di un servizio](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|  
  
 È necessario essere un membro del gruppo di amministratori di Hyper-V locali.  
  
 Per eseguire Visual Studio Emulator per Android senza una richiesta ricorrente per elevare i diritti dell'utente, è necessario essere un membro del gruppo di amministratori di Hyper-V locali. Se si è già un amministratore locale del computer quando si installa l'SDK, il programma di installazione per l'SDK aggiunge l'utente al gruppo di amministratori di Hyper-V. In caso contrario potrebbe essere necessario abilitare manualmente i prerequisiti.  
  
 Quando si esegue l'emulatore, se non si è già un membro del gruppo di amministratori di Hyper-V, viene richiesto di partecipare al gruppo (la finestra di dialogo si riferisce all'emulatore di Windows Phone). Per la partecipazione al gruppo sono necessari i diritti di amministratore.  
  
> [!IMPORTANT]
>  Dopo aver partecipato al gruppo, disconnettersi o riavviare il computer per rendere effettiva la modifica.  
  
 ![Aggiunta al gruppo di sicurezza Amministratori Hyper&#45;V](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")  
  
 Per aggiungersi manualmente a un gruppo, aprire lo snap-in Utenti e gruppi locali. Per altre informazioni, vedere [Aggiungere un account utente a un gruppo](http://windows.microsoft.com/en-us/windows/add-user-account-to-group#1TC=windows-7). (Questo argomento di Windows 7 è applicabile anche a Windows 8).  
  
##  <a name="BootableVHD"></a> L'esecuzione dell'emulatore da un VHD di avvio non è supportata  
 Se si tenta di eseguire un'applicazione in Visual Studio Emulator per Android durante l'esecuzione di Windows da un VHD di avvio, l'emulatore in genere richiede alcuni minuti per l'avvio o non viene avviato. Se l'emulatore non viene avviato, viene visualizzato il seguente messaggio: Distribuzione dell'applicazione non riuscita. Riprovare.  
  
 Questa configurazione non è supportata. Per informazioni sui problemi correlati, vedere [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Files"></a> Hyper-V richiede file non compressi e non crittografati  
 Su un disco rigido configurato con il file system NTFS, i file del disco rigido virtuale usati da Hyper-V devono essere non compressi e non crittografati. Assicurarsi che le seguenti directory non siano compresse o crittografate:  
  
-   %localappdata%\Microsoft\XDE  
  
-   C:\Programmi (x86)\Microsoft Emulator Manager  
  
-   C:\Programmi (x86)\Microsoft Visual Studio Emulator per Android  
  
-   %localappdata%\Microsoft\VisualStudioEmulator  
  
 Nel file system ReFS, i file del disco rigido virtuale non devono avere il set di bit di integrità.  
  
## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Requisiti di inoltro grafica hardware (supporto OpenGL ES)  
 Affinché l'emulatore emuli le chiamate alla GPU, come quelle usate da OpenGL ES, il computer deve disporre di una GPU compatibile con DirectX con i driver DirectX appropriati installati.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi di Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)