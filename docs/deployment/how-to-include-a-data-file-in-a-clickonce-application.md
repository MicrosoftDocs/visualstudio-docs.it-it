---
title: 'Procedura: includere un File di dati in un''applicazione ClickOnce | Documenti Microsoft'
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
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a7ddfdb0518a8e3154d966fdea884bf7f2e3ea37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Procedura: includere un file di dati in un'applicazione ClickOnce
Ogni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installata viene assegnata una directory dei dati su disco del computer di destinazione in cui l'applicazione può gestire i propri dati. File di dati possono includere qualsiasi tipo file: file di testo, file XML o anche i file di Microsoft Access (mdb). Di seguito viene illustrato come aggiungere un file di dati di qualsiasi tipo nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Per includere un file di dati tramite Mage.exe  
  
1.  Aggiungere il file di dati nella directory dell'applicazione con il resto del file dell'applicazione.  
  
     In genere, la directory dell'applicazione è una directory contrassegnata con la versione corrente di distribuzione, ad esempio, v 1.0.0.0.  
  
2.  Aggiornare il manifesto dell'applicazione all'elenco di file di dati.  
  
     **v 1.0.0.0 - FromDirectory di Mage -u v1.0.0.0\Application.manifest**  
  
     Per eseguire questa attività verrà ricreato l'elenco di file nel manifesto dell'applicazione e genera automaticamente anche le firme hash.  
  
3.  Aprire il manifesto dell'applicazione nell'editor XML o testo preferito e individuare il `file` elemento per il file aggiunto di recente.  
  
     Se è stato aggiunto un file XML denominato `Data.xml`, il file avrà un aspetto simile al seguente esempio di codice.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Aggiungere l'attributo `type` a questo elemento e fornirlo con un valore di `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Firmare il manifesto dell'applicazione utilizzando la coppia di chiavi o un certificato e firmare il manifesto della distribuzione.  
  
     È necessario firmare nuovamente il manifesto della distribuzione perché il relativo hash del manifesto dell'applicazione è stata modificata.  
  
     **Mage -s app manifesto - cf cert_file - pwd password**  
  
     **manifesto dell'applicazione di Mage -u distribuzione manifesto - appm**  
  
     **manifesto della distribuzione di -s Mage - cf certfile - pwd password**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Per includere un file di dati usando MageUI.exe  
  
1.  Aggiungere il file di dati nella directory dell'applicazione con il resto del file dell'applicazione.  
  
2.  In genere, la directory dell'applicazione è una directory contrassegnata con la versione corrente di distribuzione, ad esempio, v 1.0.0.0.  
  
3.  Nel **File** menu, fare clic su **aprire** per aprire il manifesto dell'applicazione.  
  
4.  Selezionare il **file** scheda.  
  
5.  Nella casella di testo nella parte superiore della scheda, immettere la directory che contiene i file dell'applicazione e quindi fare clic su **Popola**.  
  
     Il file di dati verrà visualizzati nella griglia.  
  
6.  Impostare il **tipo di File** valore del file di dati per **dati**.  
  
7.  Salvare il manifesto dell'applicazione e firmare nuovamente il file.  
  
     MageUI.exe verrà richiesto di firmare il file.  
  
8.  Firmare il manifesto della distribuzione  
  
     È necessario firmare nuovamente il manifesto della distribuzione perché il relativo hash del manifesto dell'applicazione è stata modificata.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)