---
title: 'Procedura: verificare le impostazioni delle proprietà IIS | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acd232b76ece37737833d071c8551d1319d4f151
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-verify-iis-property-settings"></a>Procedura: verificare le impostazioni delle proprietà di IIS
È possibile impostare le proprietà di un'applicazione Web utilizzando lo strumento di amministrazione IIS. Per consentire l'esecuzione dell'applicazione, è necessario che tali proprietà siano impostate correttamente, pertanto la verifica di queste impostazioni è spesso un passaggio necessario nel processo di risoluzione dei problemi.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Per controllare le impostazioni IIS dell'applicazione Web  
  
1.  Aprire il **strumenti di amministrazione** finestra: sul **avviare** dal menu **programmi**e quindi fare clic su **strumenti di amministrazione**. Se **strumenti di amministrazione** non viene visualizzato nel **programmi** menu, quindi cercare nella **Pannello di controllo**.  
  
    -   In Windows 2000, selezionare **Gestione servizi Internet**.  
  
    -   In Windows XP selezionare **Internet Information Services**.  
  
    -   In Windows Server 2003, fare doppio clic su **amministrazione Server**.  
  
         Il **amministrazione Server** verrà visualizzata la finestra. In **Server applicazioni**, fare clic su **gestire il server di applicazione**.  
  
         Il **Server applicazioni** verrà visualizzata la finestra. Aprire il **Gestione Internet Information Services (IIS)** nodo nel riquadro a sinistra.  
  
2.  Nella finestra di dialogo fare clic sul nodo del controllo albero per il computer. Fare clic su di **siti Web** nodo, quindi selezionare il nodo dell'applicazione Web. Si tratterà di un nodo di sito Web, quindi di pari livello di **sito Web predefinito** nodo o un nodo di directory virtuale sottostante un nodo di sito Web esistente.  
  
3.  Il pulsante destro l'applicazione Web e il menu di scelta rapida, fare clic su **proprietà**.  
  
4.  Verificare le impostazioni di sicurezza dell'applicazione Web:  
  
    1.  Nell'applicazione Web **proprietà** finestra, fare clic su di **protezione Directory** scheda e fare clic su **modifica**.  
  
    2.  Nel **metodi di autenticazione** nella finestra di dialogo **Abilita accesso anonimo** e **autenticazione integrata di Windows** se non sono già selezionate.  
  
    3.  Fare clic su **OK** per chiudere la **metodi di autenticazione** la finestra di dialogo.  
  
5.  Per un'applicazione ATL Server verificare che il verbo DEBUG sia associato all'estensione ISAPI. Per ulteriori informazioni, vedere [procedura: associare verbo DEBUG con estensione](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Per un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione, assicurarsi che la cartella virtuale dell'applicazione disponga di un nome applicazione impostato in **Gestione Internet Information Services (IIS)**, **Gestione servizi Internet** o  **Internet Information Services**.  
  
    1.  Nell'applicazione Web **proprietà** finestra, seleziona il **Directory** scheda, se l'applicazione è in una directory virtuale, o **Home Directory** scheda, se l'applicazione è in un sito Web.  
  
    2.  Verificare che il nome di **percorso locale** corrisponde al nome della directory in cui l'applicazione è stata effettivamente distribuita.  
  
    3.  In **le impostazioni dell'applicazione**, digitare il nome della directory radice che contiene l'applicazione.  
  
    4.  Fare clic su **OK** per chiudere la **proprietà** la finestra di dialogo.  
  
7.  Per un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione, fare clic su di **ASP.NET** scheda e verificare che la versione corretta di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] specificato.  
  
8.  Fare clic su **OK** per chiudere la **proprietà** la finestra di dialogo.  
  
9. Fare clic su **OK** per chiudere la **Gestione Internet Information Services (IIS)**, **Gestione servizi Internet**, o **Internet Information Services**la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi](../debugger/debugging-web-applications-troubleshooting.md)