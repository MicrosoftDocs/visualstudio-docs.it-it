---
title: "Procedura: personalizzare la pagina Web predefinita per un'applicazione ClickOnce | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 743d7f259da4129eda578808d1ce04619104a3f1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Procedura: Personalizzare la pagina Web predefinita per un'applicazione ClickOnce
Quando si pubblica un'applicazione ClickOnce per il Web, una pagina Web viene automaticamente generata e pubblicata insieme all'applicazione. La pagina predefinita contiene il nome dell'applicazione e i collegamenti per installare l'applicazione, installare i prerequisiti o accedere alla Guida in MSDN.  
  
> [!NOTE]
>  I collegamenti effettivi che viene visualizzato nella pagina dipendono dai computer in cui viene visualizzata la pagina e cosa prerequisiti inclusi.  
  
 Il nome predefinito per la pagina Web è Publish; htm. è possibile modificare il nome di **progettazione**. Per ulteriori informazioni, vedere [procedura: specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 La pagina Web Publish viene pubblicata solo se viene rilevata una versione più recente.  
  
> [!NOTE]
>  Le modifiche apportate al **pubblica** impostazioni non riguardano la pagina Publish.htm, con una sola eccezione: se si aggiungono o rimuovono prerequisiti dopo la pubblicazione inizialmente, l'elenco dei prerequisiti non saranno accurato. È necessario modificare il testo per il collegamento dei prerequisiti in modo da riflettere le modifiche.  
  
### <a name="to-customize-the-publish-web-page"></a>Per personalizzare la pagina Web di pubblicazione  
  
1.  Pubblicare l'applicazione ClickOnce in un percorso Web. Per ulteriori informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Nel server Web, aprire il file Publish nella finestra di progettazione Web visiva o un altro editor HTML.  
  
3.  Personalizzare la pagina in base alle esigenze e salvarlo.  
  
4.  Facoltativo. Per impedire la sovrascrittura della pagina Web di pubblicazione personalizzata di Visual Studio, deselezionare **genera automaticamente pagina web di distribuzione dopo ogni pubblicazione** nella finestra di dialogo Opzioni di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Procedura: Specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)