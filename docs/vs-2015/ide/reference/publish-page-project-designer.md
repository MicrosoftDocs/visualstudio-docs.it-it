---
title: Pagina Pubblica, Progettazione progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f50c5897f68e43071d4920f85f1a694cacbf655
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441303"
---
# <a name="publish-page-project-designer"></a>Pagina Pubblica, Progettazione progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La pagina **Pubblica** della **Creazione progetti** consente di configurare le proprietà relative alla distribuzione ClickOnce.  
  
 Per accedere alla pagina **Pubblica** , selezionare un nodo di progetto in **Esplora soluzioni**, quindi fare clic su **Proprietà** dal menu **Progetto**. In **Progettazione progetti** fare clic sulla scheda **Pubblica** .  
  
> [!NOTE]
> Alcune delle proprietà ClickOnce descritte possono essere impostate anche nella **Pubblicazione guidata** disponibile nel menu **Compila** oppure facendo clic sul pulsante **Pubblicazione guidata** nella pagina.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Posizione cartella di pubblicazione**  
 Specifica il percorso in cui l'applicazione viene pubblicata. Può essere un percorso di unità (`C:\deploy\myapplication`), una condivisione file (`\\server\myapplication`), un server FTP (`ftp://ftp.microsoft.com/myapplication`) o un sito Web (`http://www.microsoft.com/myapplication`). Si noti che il testo deve essere presente nella scheda **Posizione di pubblicazione** perché il pulsante Sfoglia (**...**) funzioni.  
  
 Per impostazione predefinita, il percorso di pubblicazione è `http://localhost/<projectname>/` se IIS è installato o la directory `publish\` se IIS non è installato. Se il computer esegue Windows Vista, il valore predefinito è sempre la directory `publish\` , indipendentemente dal fatto che sia installato IIS.  
  
 **URL cartella di installazione**  
 Facoltativo. Specifica un sito Web a cui gli utenti accedono per installare l'applicazione. Questa operazione è necessaria solo se si tratta di un percorso diverso da **Posizione di pubblicazione**, ad esempio quando l'applicazione viene pubblicata in un server di gestione temporanea.  
  
 **Modalità di installazione e impostazioni**  
 Determina se l'applicazione viene eseguita direttamente dalla **Posizione di pubblicazione** (quando è selezionata l'opzione **Applicazione disponibile solo online** ) o viene installata e aggiunta al menu **Start** e all'elemento **Installazione applicazioni** del **Pannello di controllo** (quando è selezionata l'opzione **Applicazione disponibile anche offline** ).  
  
 Per le applicazioni Web Browser WPF, l'opzione **Applicazione disponibile anche offline** è disabilitata, perché tali applicazioni sono disponibili solo online.  
  
 **File applicazione**  
 Apre [Application Files Dialog Box](http://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8)che consente di specificare come e dove vengono installati i singoli file.  
  
 **Prerequisiti**  
 Apre il [Prerequisites Dialog Box](../../ide/reference/prerequisites-dialog-box.md)che consente di specificare i componenti necessari, ad esempio .NET Framework, da installare insieme all'applicazione.  
  
 **Aggiornamenti**  
 Apre [Application Updates Dialog Box](http://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)che consente di specificare il comportamento di aggiornamento per l'applicazione. Non è disponibile quando è selezionata l'opzione **Applicazione disponibile solo online** .  
  
 **Opzioni**  
 Apre [Publish Options Dialog Box](http://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)che consente di specificare altre opzioni di pubblicazione avanzate.  
  
 **Versione di pubblicazione**  
 Imposta il numero della versione di pubblicazione per l'applicazione. Quando viene modificato il numero di versione, l'applicazione viene pubblicata come aggiornamento. Ogni parte della versione di pubblicazione (**Principale**, **Secondaria**, **Compilazione**, **Revisione**) può avere un valore massimo di 65355 (<xref:System.UInt16.MaxValue>), il massimo consentito da <xref:System.Version>.  
  
 Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
 **Incrementa automaticamente revisione a ogni pubblicazione**  
 Facoltativo. Quando questa opzione è selezionata (impostazione predefinita), la parte **Revisione** del numero di versione viene incrementata di un'unità ogni volta che viene pubblicata l'applicazione. In questo modo l'applicazione viene pubblicata come aggiornamento.  
  
 **Pubblicazione guidata**  
 Apre [Publish Wizard](http://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872). Il completamento della Pubblicazione guidata ha lo stesso effetto dell'esecuzione del comando **Pubblica** del menu **Compila** .  
  
 **Pubblica**  
 Pubblica l'applicazione usando le impostazioni correnti. Equivale al pulsante **Fine** della **Pubblicazione guidata**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Procedura: Specifica in cui vengono copiati i file di Visual Studio](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Procedura: Specificare il percorso in cui gli utenti finali eseguiranno l'installazione da](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [Procedura: Specificare un collegamento per il supporto tecnico](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [Procedura: Specificare la modalità Offline o ClickOnce modalità di installazione Online](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [Procedura: Attivare l'avvio automatico per le installazioni da CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)   
 [Procedura: Versione di pubblicazione di set di ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Procedura: Incrementare il ClickOnce automaticamente versione pubblicazione](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Procedura: Specificare i file da pubblicare mediante ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)   
 [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Procedura: Gestire gli aggiornamenti per un'applicazione ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)   
 [Procedura: Modifica la lingua di pubblicazione di un'applicazione ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [Procedura: Specificare il nome dal Menu Start per un'applicazione ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [Sicurezza e distribuzione di ClickOnce](../../deployment/clickonce-security-and-deployment.md)
