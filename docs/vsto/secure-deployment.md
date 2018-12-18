---
title: Distribuzione sicura | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f52c6d26132490defafdf87639e0f1731ea90640
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="secure-deployment"></a>Distribuzione sicura
  Quando si crea una soluzione Office, il computer di sviluppo viene aggiornato automaticamente per consentire al codice nel progetto per l'esecuzione. Tuttavia, quando si distribuisce la soluzione, è necessario fornire l'evidenza sulla quale basare una decisione di attendibilità della soluzione con un certificato di firma o utilizzando il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave di richiesta di attendibilità. Per ulteriori informazioni, vedere [concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Per le personalizzazioni a livello di documento, se si distribuisce il documento in un percorso di rete, è necessario anche aggiungere il percorso del documento all'elenco di percorsi attendibili nel Centro protezione dell'applicazione di Office. Per ulteriori informazioni su come impostare le autorizzazioni di documento per utente finale computer, vedere [concessione dell'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).  
  
## <a name="preventing-office-solutions-from-running-code"></a>Impedisce l'esecuzione del codice di soluzioni Office  
 Gli amministratori possono utilizzare il Registro di sistema per impedire l'esecuzione in un computer di tutte le soluzioni Office. Quando una soluzione Office che Usa estensioni di codice gestito viene aperto, Visual Studio Tools per i controlli di runtime di Office se una voce con il nome `Disabled` esiste in una delle seguenti chiavi del Registro di sistema nel computer:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Per impedire l'esecuzione del codice di soluzioni Office, creare un `Disabled` voce in una o entrambe queste chiavi del Registro di sistema e specificare uno dei seguenti tipi di dati e i valori per `Disabled`:  
  
-   REG_SZ o REG_EXPAND_SZ impostato su qualsiasi stringa diversa da "0" (zero).  
  
-   REG_DWORD che è impostato su qualsiasi valore diverso da 0 (zero).  
  
 Per abilitare l'esecuzione di codice delle soluzioni Office, impostare entrambe le `Disabled` voci su 0 (zero), o eliminare le voci del Registro di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Preparazione dei computer per l'esecuzione o ospitare soluzioni Office](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  