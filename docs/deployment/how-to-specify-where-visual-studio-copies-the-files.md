---
title: 'Procedura: specificare in Visual Studio copierà i file | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b4e626253d9d07a9f263304d02739bdb3f4b012
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procedura: specificare il percorso in cui vengono copiati i file in Visual Studio
Quando si pubblica un'applicazione tramite ClickOnce, la proprietà `Publish Location` specifica il percorso in cui vengono inseriti i file dell'applicazione e il manifesto. Può trattarsi di un percorso di file o del percorso di un server FTP.  
  
 È possibile specificare il `Publish Location` proprietà il **pubblica** pagina del **progettazione**, o tramite la pubblicazione guidata. Per ulteriori informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
### <a name="to-specify-a-publishing-location"></a>Per specificare un percorso di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Nel **percorso di pubblicazione** immettere il percorso di pubblicazione utilizzando uno dei formati seguenti:  
  
    -   Per pubblicare in un percorso di un disco o condivisione di file, immettere il percorso utilizzando un percorso UNC (\\\Server\ApplicationName) o un percorso di file (C:\Deploy\ApplicationName).  
  
    -   Per pubblicare in un server FTP, immettere il percorso nel formato ftp://ftp.microsoft.com/NomeApplicazione.  
  
     Si noti che il testo deve essere presente nel **percorso** casella affinché il pulsante Sfoglia (**...** ) funzionamento del pulsante.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)