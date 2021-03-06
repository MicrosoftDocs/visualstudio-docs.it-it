---
title: Imposta percorso file di log personalizzato (errori di distribuzione ClickOnce)
description: Informazioni sui file di log di attivazione gestiti da ClickOnce per tutte le distribuzioni, che documentano gli errori per l'installazione e l'inizializzazione di una distribuzione ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e527e1aec630faadec6e594f944a6715028c6d82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885053"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Procedura: Impostare un percorso personalizzato per il file di log degli errori della distribuzione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene i file del log di attivazione per tutte le distribuzioni. Questi log documentano gli eventuali errori relativi all'installazione e all'inizializzazione di una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per impostazione predefinita, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Crea un file di log per ogni attivazione della distribuzione. Questi file di log vengono archiviati nella cartella file temporanei Internet. Il file di log per una distribuzione viene visualizzato all'utente quando si verifica un errore di attivazione e l'utente fa clic su **Dettagli** nella finestra di dialogo di errore risultante.

 È possibile modificare questo comportamento per un client specifico utilizzando l'editor del registro di sistema (**regedit.exe**) per impostare un percorso personalizzato per il file di log. In questo caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registra le operazioni riuscite ed errori per tutte le distribuzioni in un singolo file.

> [!CAUTION]
> L'errato utilizzo dell'Editor del Registro di sistema può causare gravi problemi che possono richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.

> [!NOTE]
> È necessario troncare o eliminare occasionalmente il file di log per impedire che cresca troppo grande.

 Nella procedura seguente viene descritto come impostare un percorso di file di log personalizzato per un singolo client.

### <a name="to-set-a-custom-log-file-location"></a>Per impostare un percorso personalizzato per il file di log

1. Aprire **Regedit.exe**.

2. Passare al nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Impostare il valore di stringa sul `LogFilePath` percorso completo e il nome file del percorso del log personalizzato preferito.

     Questo percorso deve trovarsi in una directory a cui l'utente dispone dell'accesso in scrittura. In Windows Vista, ad esempio, creare la struttura di cartelle seguente e impostare su `LogFilePath` *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Vedi anche
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)