---
title: Guida dell'amministratore di Help Viewer | Microsoft Docs
ms.custom: 
ms.date: 11/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5f509b0ace14c4e0becd714e25ee9ec26770c6e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="help-viewer-administrator-guide"></a>Guida dell'amministratore di Help Viewer
Il visualizzatore della Guida consente di gestire le installazioni della Guida locale per gli ambienti di rete con o senza accesso a Internet. Il contenuto della Guida locale viene configurato per ogni singolo computer. Per impostazione predefinita, gli utenti devono disporre dei diritti di amministratore per aggiornare l'installazione della Guida locale.  
  
Se l'ambiente di rete consente ai client di accedere a Internet, è possibile usare l'eseguibile di Gestione contenuto della Guida per distribuire contenuto della Guida locale da Internet. Per altre informazioni sulla sintassi della riga di comando di HlpCtntMgr.exe, vedere [Argomenti della riga di comando per Gestione contenuto della Guida](../ide/command-line-arguments-for-the-help-content-manager.md).

Per informazioni sulla creazione del contenuto, sulla creazione di un endpoint servizio Intranet e tipi di attività simili, vedere [Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md).  
  
Se nell'ambiente di rete non è disponibile l'accesso a Internet, Help Viewer può distribuire il contenuto della Guida locale dalla Intranet o da una condivisione di rete. È anche possibile disabilitare le opzioni della Guida dell'IDE di Visual Studio tramite [override di chiavi del Registro di sistema](../ide/help-content-manager-overrides.md) per le funzionalità, ad esempio:

- Guida online o offline

- installazione del contenuto al primo avvio dell'IDE

- Specifica di un servizio contenuto nella rete Intranet

- Gestione del contenuto 
  
## <a name="deploying-local-help-content-from-the-internet"></a>Distribuzione del contenuto della Guida locale da Internet  
È possibile usare Gestione contenuto della Guida (HlpCtntMgr.exe) per distribuire il contenuto della Guida locale da Internet ai computer client. Usare la sintassi seguente:  
  
```
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```
  
Per altre informazioni sulla sintassi della riga di comando di HlpCtntMgr.exe, vedere [Argomenti della riga di comando per Gestione contenuto della Guida](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
Requisiti:  
  
-   I computer client devono avere accesso a Internet.  
  
-   Gli utenti devono disporre dei diritti di amministratore per aggiornare, aggiungere o rimuovere il contenuto della Guida locale dopo l'installazione.  
  
 Avvertenze:  
  
-   L'origine predefinita per la Guida sarà ancora online.
  
### <a name="example"></a>Esempio  
L'esempio seguente installa il contenuto in lingua inglese per Visual Studio in un computer client.  
  
##### <a name="to-install-english-content-from-the-internet"></a>Per installare il contenuto in lingua inglese da Internet  
  
1.  Scegliere **Start** e quindi **Esegui**.  
  
2.  Digitare quanto segue:  
  
     C:\Programmi (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale it-it  
  
3.  Premere **INVIO**.  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Distribuzione del contenuto della Guida locale preinstallato nei computer client
È possibile installare un set di contenuti online in un computer e quindi copiarlo in altri computer.  
  
Requisiti:  
  
-   Il computer in cui si installa il set del contenuto deve avere accesso a Internet.  
  
-   Gli utenti devono disporre dei diritti di amministratore per aggiornare, aggiungere o rimuovere il contenuto della Guida locale dopo l'installazione.  
  
    > [!TIP]
    >  Se gli utenti non dispongono dei diritti di amministratore, si consiglia di disabilitare la scheda Gestisci contenuto nel visualizzatore della Guida. Per altre informazioni, vedere [Override di Gestione contenuto della Guida](../ide/help-content-manager-overrides.md).  
  
Avvertenze:
  
-   L'origine predefinita per la Guida sarà ancora online.
  
### <a name="create-the-content-set"></a>Creare il set di contenuti  
Prima di poter creare il set di contenuti di base, è necessario disinstallare tutto il contenuto di Visual Studio locali dal computer di destinazione.  
  
#### <a name="to-uninstall-local-help"></a>Per disinstallare la Guida locale  
  
1.  In Help Viewer scegliere la scheda **Gestisci contenuto**.  
  
2.  Passare al set di documenti di Visual Studio.  
  
3.  Scegliere **Rimuovi** accanto a ogni elemento secondario.  
  
4.  Scegliere **Aggiorna** per disinstallare.
  
5.  Passare a %ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 e verificare che la cartella contenga solo il file catalogType.xml.  
  
 Dopo aver rimosso tutto il contenuto della Guida locale di Visual Studio installato in precedenza, si è pronti per scaricare il set di contenuti di base.  
  
#### <a name="to-download-the-content"></a>Per scaricare il contenuto  
  
1.  In Help Viewer scegliere la scheda **Gestisci contenuto**.  
  
2.  In **Documentazione consigliata** o **Documentazione disponibile** passare ai set di documentazione che si vuole scaricare e quindi scegliere **Aggiungi**.  
  
3.  Scegliere **Aggiorna**.  
  
 Ora è necessario creare un pacchetto del contenuto per poterlo distribuire ai computer client.  
  
#### <a name="to-package-the-content"></a>Per creare un pacchetto del contenuto  
  
1.  Creare una cartella in cui copiare il contenuto da distribuire. Ad esempio: C:\VSHelp.  
  
2.  Aprire cmd.exe con le autorizzazioni di amministratore.  
  
3.  Passare alla cartella creata nel passaggio 1.  
  
4.  Digitare quanto segue:  
  
     Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*nomecartella*>\ /y /e /k /o  
  
     Ad esempio: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`  
  
### <a name="deploying-the-content"></a>Distribuzione del contenuto  
  
#### <a name="to-deploy-the-content"></a>Per distribuire il contenuto  
  
1.  Creare una condivisione di rete e copiare il contenuto della Guida in tale posizione.  
  
     Ad esempio, copiare il contenuto di C:\VSHelp in \\\myserver\VSHelp.  
  
2.  Creare un file .bat che dovrà contenere lo script di distribuzione per il contenuto della Guida. Poiché potrebbe verificarsi un blocco di lettura nel client per qualsiasi file da eliminare durante il push, è necessario arrestare il client prima del push degli aggiornamenti. Ad esempio:  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```  
  
3.  Eseguire il file con estensione bat nei computer locali in cui si vuole installare il contenuto della Guida.  
  
## <a name="see-also"></a>Vedere anche
[Argomenti della riga di comando per Gestione contenuto della Guida](../ide/command-line-arguments-for-the-help-content-manager.md)  
[Ovverride di Gestione contenuto della Guida](../ide/help-content-manager-overrides.md)  
[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)  
[Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)