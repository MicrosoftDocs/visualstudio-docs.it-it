---
title: Pagina Pubblica, Progettazione progetti | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d9f050662ed38814920e17b36f77bf6795aabfa9
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="publish-page-project-designer"></a>Pagina Pubblica, Progettazione progetti
La pagina **Pubblica** della **Creazione progetti** consente di configurare le proprietà relative alla distribuzione ClickOnce.  
  
 Per accedere alla pagina **Pubblica** , selezionare un nodo di progetto in **Esplora soluzioni**, quindi fare clic su **Proprietà** dal menu **Progetto**. In **Progettazione progetti** fare clic sulla scheda **Pubblica** .  
  
> [!NOTE]
>  Alcune delle proprietà ClickOnce descritte possono essere impostate anche nella **Pubblicazione guidata** disponibile nel menu **Compila** oppure facendo clic sul pulsante **Pubblicazione guidata** nella pagina.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Posizione cartella di pubblicazione**  
 Specifica il percorso in cui l'applicazione viene pubblicata. Può essere un percorso di unità (`C:\deploy\myapplication`), una condivisione file (`\\server\myapplication`) o un server FTP (`ftp://ftp.microsoft.com/myapplication`). Si noti che il testo deve essere presente nella scheda **Posizione di pubblicazione** perché il pulsante Sfoglia (**...**) funzioni.  
   
 **URL cartella di installazione**  
 Facoltativo. Specifica un sito Web a cui gli utenti accedono per installare l'applicazione. Questa operazione è necessaria solo se si tratta di un percorso diverso da **Posizione di pubblicazione**, ad esempio quando l'applicazione viene pubblicata in un server di gestione temporanea.  
  
 **Modalità di installazione e impostazioni**  
 Determina se l'applicazione viene eseguita direttamente dalla **Posizione di pubblicazione** (quando è selezionata l'opzione **Applicazione disponibile solo online** ) o viene installata e aggiunta al menu **Start** e all'elemento **Installazione applicazioni** del **Pannello di controllo** (quando è selezionata l'opzione **Applicazione disponibile anche offline** ).  
  
 Per le applicazioni Web Browser WPF, l'opzione **Applicazione disponibile anche offline** è disabilitata, perché tali applicazioni sono disponibili solo online.  
  
 **File dell'applicazione**  
 Apre la finestra di dialogo File applicazione usata per specificare come e dove vengono installati i singoli file.  
  
 **Prerequisiti**  
 Apre la finestra di dialogo Prerequisiti usata per specificare i componenti necessari, ad esempio .NET Framework, da installare insieme all'applicazione.  
  
 **Aggiornamenti**  
 Apre la finestra di dialogo Aggiornamenti applicazione usata per specificare il comportamento di aggiornamento per l'applicazione. Non è disponibile quando è selezionata l'opzione **Applicazione disponibile solo online** .  
  
 **Opzioni**  
 Apre la finestra di dialogo Opzioni di pubblicazione usata per specificare altre opzioni di pubblicazione avanzate.  
  
 **Versione di pubblicazione**  
 Imposta il numero della versione di pubblicazione per l'applicazione. Quando viene modificato il numero di versione, l'applicazione viene pubblicata come aggiornamento. Ogni parte della versione di pubblicazione (**Principale**, **Secondaria**, **Compilazione**, **Revisione**) può avere un valore massimo di 65355 (<xref:System.UInt16.MaxValue>), il massimo consentito da <xref:System.Version>.  
  
 Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
 **Incrementa automaticamente revisione a ogni pubblicazione**  
 Facoltativo. Quando questa opzione è selezionata (impostazione predefinita), la parte **Revisione** del numero di versione viene incrementata di un'unità ogni volta che viene pubblicata l'applicazione. In questo modo l'applicazione viene pubblicata come aggiornamento.  
  
 **Pubblicazione guidata**  
 Apre la Pubblicazione guidata. Il completamento della Pubblicazione guidata ha lo stesso effetto dell'esecuzione del comando **Pubblica** del menu **Compila** .  
  
 **Pubblica**  
 Pubblica l'applicazione usando le impostazioni correnti. Equivale al pulsante **Fine** della **Pubblicazione guidata**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Procedura: Specificare il percorso in cui vengono copiati i file in Visual Studio](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Procedura: Specificare il percorso da cui gli utenti finali eseguiranno l'installazione](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [Procedura: Specificare un collegamento per il supporto tecnico](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [Procedura: Specificare la modalità di installazione online o offline di ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [Procedura: Attivare l'avvio automatico per le installazioni da CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)   
 [Procedura: Impostare la versione pubblicazione per un'applicazione ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Procedura: Incrementare automaticamente il numero di versione pubblicazione dell'applicazione ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Procedura: Specificare i file da pubblicare mediante ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)   
 [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Procedura: Gestire gli aggiornamenti per un'applicazione ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)   
 [Procedura: Cambiare la lingua di pubblicazione di un'applicazione ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [Procedura: Specificare il nome di un'applicazione ClickOnce per il menu Start](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [Sicurezza e distribuzione di ClickOnce](../../deployment/clickonce-security-and-deployment.md)
