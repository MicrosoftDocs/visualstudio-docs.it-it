---
title: 'Procedura: installare i prerequisiti con un''applicazione ClickOnce | Documenti Microsoft'
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
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 83458b627949cda5f918ec06a5f84bd9697ba6d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Procedura: installare i prerequisiti con un'applicazione ClickOnce
Tutti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni è necessario che la versione corretta di .NET Framework sia installata in un computer prima di poter essere eseguiti, molte applicazioni hanno anche altri prerequisiti. Quando si pubblica un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, è possibile scegliere un set di componenti dei prerequisiti da includere nel pacchetto insieme all'applicazione. Al momento dell'installazione, verrà eseguito un controllo per ogni prerequisito determinare se già presente. Se non viene installato prima di installare il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
 Invece di creare il pacchetto e pubblicare i prerequisiti, è anche possibile specificare un percorso di download per i componenti. Ad esempio, anziché l'inclusione dei prerequisiti con ogni applicazione che si esegue la pubblicazione, è possibile utilizzare una condivisione file centralizzata o un percorso Web che contiene i programmi di installazione per tutti i prerequisiti, al momento dell'installazione, verranno scaricati i componenti e installato da quel percorso.  
  
> [!IMPORTANT]
>  È necessario aggiungere i pacchetti di installazione dei prerequisiti nel computer di sviluppo prima di pubblicare il primo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Per ulteriori informazioni, vedere [procedura: includere prerequisiti con un'applicazione ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Per la gestione di **prerequisiti** la finestra di dialogo, accessibile dal **pubblica** riquadro del **Progettazione progetti**.  
  
> [!NOTE]
>  Oltre all'elenco predeterminato di prerequisiti, è possibile aggiungere componenti personalizzati all'elenco. Per ulteriori informazioni, vedere [la creazione di pacchetti del programma di avvio](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Per specificare i prerequisiti di installazione con un'applicazione ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Selezionare il **pubblica** riquadro.  
  
3.  Fare clic su di **prerequisiti** pulsante per aprire la **prerequisiti** la finestra di dialogo.  
  
4.  Nella finestra di dialogo **Prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.  
  
5.  Nel **prerequisiti** elenco, controllare i componenti che si desiderano installare e quindi fare clic su **OK**.  
  
     I componenti selezionati verranno incluso nel pacchetto e pubblicati insieme all'applicazione.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Per specificare un percorso di download diversi per i prerequisiti  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Selezionare il **pubblica** riquadro.  
  
3.  Fare clic su di **prerequisiti** pulsante per aprire la **prerequisiti** la finestra di dialogo.  
  
4.  Nella finestra di dialogo **Prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.  
  
5.  Nel **specificare il percorso di installazione dei prerequisiti** selezionare **Scarica prerequisiti dal seguente percorso**.  
  
6.  Selezionare un percorso nell'elenco a discesa o immettere un URL, un percorso del file o un percorso FTP e quindi fare clic su **OK.**  
  
    > [!NOTE]
    >  È necessario assicurarsi che i programmi di installazione per i componenti specificati esistano nel percorso specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)