---
title: 'Procedura: pubblicare un''applicazione ClickOnce mediante la pubblicazione guidata | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
caps.latest.revision: "25"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d314763f8ff4dc170148cca166e3ecdff051ae24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Procedura: pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata
Per rendere disponibile un'applicazione ClickOnce agli utenti, è necessario pubblicarla in un una condivisione file, in un percorso, in un server FTP o su un supporto rimovibile. È possibile pubblicare l'applicazione tramite la pubblicazione guidata. proprietà aggiuntive relative alla pubblicazione sono disponibili per il **pubblica** pagina del **Progettazione progetti**. Per ulteriori informazioni, vedere [pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md).  
  
 Prima di eseguire la Pubblicazione guidata, impostare correttamente le opzioni di pubblicazione. Ad esempio, se si desidera specificare una chiave per firmare l'applicazione ClickOnce, non è così via di **firma** pagina del **progettazione**. Per altre informazioni, vedere [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>Per pubblicare in una condivisione file o in un percorso  
  
1.  In **Esplora**, selezionare il progetto di applicazione.  
  
2.  Nel **compilare** menu, fare clic su **pubblica**`Projectname`.  
  
     Verrà visualizzata la Pubblicazione guidata.  
  
3.  Nel **in cui si desidera pubblicare l'applicazione?** immettere un indirizzo valido del server FTP o un percorso valido usando uno dei formati indicati e quindi fare clic su **Avanti**.  
  
4.  Nel **come gli utenti installeranno l'applicazione?** pagina, selezionare il percorso in cui accederanno gli utenti di installare l'applicazione:  
  
    -   Se gli utenti eseguiranno l'installazione da un sito Web, fare clic su **da un sito Web** e immettere un URL che corrisponde al percorso di file specificato nel passaggio precedente. Scegliere **Avanti**. In genere questa opzione viene usata quando si specifica un indirizzo FTP come percorso di pubblicazione. Il download diretto da FTP non è supportato, di conseguenza, è necessario specificare un URL.  
  
    -   Se gli utenti installeranno l'applicazione direttamente dalla condivisione file, fare clic su **UNC da un percorso o la condivisione file**, quindi fare clic su **Avanti**. (Per una pubblicazione di percorsi di formato c:\deploy\myapp o \\\server\myapp.)  
  
    -   Se gli utenti eseguiranno l'installazione da un supporto rimovibile, fare clic su **dal CD-ROM o DVD-ROM**, quindi fare clic su **Avanti**.  
  
5.  Nel **l'applicazione sarà disponibile offline?** pagina, fare clic sull'opzione appropriata:  
  
    -   Se si desidera abilitare l'applicazione da eseguire quando l'utente è disconnesso dalla rete, fare clic su **Sì, questa applicazione sarà disponibile online o offline**. Un collegamento di **avviare** menu verrà creato per l'applicazione.  
  
    -   Se si desidera eseguire l'applicazione direttamente dal percorso di pubblicazione, fare clic su **No, questa applicazione è disponibile solo online**. Un collegamento di **avviare** menu non verrà creato.  
  
     Fare clic su **Avanti** per continuare.  
  
6.  Fare clic su **fine** per pubblicare l'applicazione.  
  
     Lo stato di pubblicazione è visualizzato nell'area di notifica dello stato.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Per pubblicare su CD-ROM o DVD-ROM  
  
1.  In **Esplora**, fare clic sul progetto dell'applicazione e fare clic su **proprietà**.  
  
     Viene visualizzata la finestra **Creazione progetti**.  
  
2.  Fare clic su di **pubblica** tab per aprire il **pubblica** nella pagina di **Progettazione progetti**e fare clic sul **pubblicazione guidata** pulsante.  
  
     Verrà visualizzata la Pubblicazione guidata.  
  
3.  Nel **in cui si desidera pubblicare l'applicazione?** pagina, immettere il percorso del file o un percorso FTP in cui verrà pubblicata l'applicazione, ad esempio d:\deploy. Quindi fare clic su **Avanti** per continuare.  
  
4.  Nel **come gli utenti installeranno l'applicazione?** pagina, fare clic su un **CD-ROM o DVD-ROM**, quindi fare clic su **Avanti**.  
  
    > [!NOTE]
    >  Se si desidera che l'installazione venga eseguita automaticamente quando il CD-ROM viene inserito nell'unità, aprire il **pubblica** nella pagina di **Progettazione progetti** e fare clic sul **opzioni** pulsante, quindi il **opzioni di pubblicazione** procedura guidata, selezionare **per installazioni da CD, avvia automaticamente l'installazione all'inserimento del CD**.  
  
5.  Se l'applicazione viene distribuita tramite CD-ROM, sarà necessario pubblicare gli aggiornamenti in un sito Web. Nel **in cui l'applicazione controllerà gli aggiornamenti?** pagina, scegliere un'opzione di aggiornamento:  
  
    -   Se l'applicazione verificherà la disponibilità di aggiornamenti, fare clic su **l'applicazione controllerà gli aggiornamenti dal seguente percorso** e immettere il percorso in cui verranno pubblicati gli aggiornamenti. Può trattarsi di un percorso di file, un sito Web o un server FTP.  
  
    -   Se l'applicazione non verificherà la disponibilità di aggiornamenti, fare clic su **l'applicazione non controllerà la disponibilità di aggiornamenti**.  
  
     Fare clic su **Avanti** per continuare.  
  
6.  Fare clic su **fine** per pubblicare l'applicazione.  
  
     Lo stato di pubblicazione è visualizzato nell'area di notifica dello stato.  
  
    > [!NOTE]
    >  Al termine della pubblicazione, sarà necessario usare un masterizzatore CD o DVD per copiare i file dal percorso specificato nel passaggio 3 al CD-ROM o DVD-ROM.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Distribuzione di una soluzione Office mediante ClickOnce](/office-dev/office-dev/deploying-an-office-solution-by-using-clickonce)