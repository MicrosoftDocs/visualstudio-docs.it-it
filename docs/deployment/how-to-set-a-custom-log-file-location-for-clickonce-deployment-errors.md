---
title: 'Procedura: impostare un percorso di File di Log personalizzato per gli errori di distribuzione ClickOnce | Documenti Microsoft'
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
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: fbeaf6655ffc3e05afd9633add0defde9368a419
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Procedura: impostare un percorso personalizzato per il file di log degli errori della distribuzione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]gestisce i file di log di attivazione per tutte le distribuzioni. Questi log documentare eventuali errori di installazione e l'inizializzazione di un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per impostazione predefinita, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea un file di log per ogni attivazione di distribuzione. Archivia questi file di log nella cartella dei file temporanei Internet. Il file di log per una distribuzione viene visualizzato all'utente quando si verifica un errore di attivazione e l'utente fa clic **dettagli** nella finestra di dialogo di errore risultante.  
  
 È possibile modificare questo comportamento per un client specifico utilizzando l'Editor del Registro di sistema (**regedit.exe**) per impostare un percorso di file di log personalizzato. In questo caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registri operazioni attivazione riuscite e non per tutte le distribuzioni in un singolo file.  
  
> [!CAUTION]
>  Se si utilizza l'Editor del Registro di sistema in modo non corretto, si può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.  
  
> [!NOTE]
>  È necessario troncare o eliminare il file di registro per impedire l'aumento eccessivo.  
  
 La procedura seguente viene descritto come impostare un percorso di file di log personalizzato per un singolo client.  
  
### <a name="to-set-a-custom-log-file-location"></a>Per impostare un percorso di file di log personalizzato  
  
1.  Aprire **Regedit.exe**.  
  
2.  Passare al nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Impostare il valore stringa `LogFilePath` per il percorso completo e il nome del percorso preferito log personalizzato.  
  
     Questo percorso deve essere in una directory a cui l'utente ha accesso in scrittura. Ad esempio, in Windows Vista, creare la seguente struttura di cartelle e impostare `LogFilePath` a C:\Users\\< nome utente\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)