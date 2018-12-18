---
title: Concessione dell'attendibilità ai documenti | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8556f77b74ee1dab6a257f5ed3634da4bf798cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="granting-trust-to-documents"></a>Granting Trust to Documents
  Un progetto a livello di documento presenta gli stessi requisiti di sicurezza dei progetti a livello di applicazione, ovvero la firma dei manifesti con un certificato o la risposta, tramite clic, a una richiesta di attendibilità. Inoltre, il documento o la cartella di lavoro si deve trovare in una directory definita come percorso attendibile.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Percorsi attendibili  
 Le applicazioni in [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Office 2010 dispongono il Centro protezione in cui gli utenti possono configurare le impostazioni di sicurezza e privacy, come i percorsi attendibili. Per le soluzioni Office, il computer locale è considerato un percorso attendibile. Tuttavia, a causa del rischio più elevato, alcune directory non possono mai essere considerate attendibili, come le cartelle temporanee del sistema, per ciascun utente e per Internet Explorer.  
  
 Per ulteriori informazioni sul Centro protezione, vedere [criteri e sicurezza e le impostazioni di Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Per ulteriori informazioni su come creare, gestire, rimuovere e configurare cartelle attendibili, vedere [configurare percorsi attendibili e le impostazioni di editori attendibili in Office system 2007](http://go.microsoft.com/fwlink/?LinkId=89203) e [creazione, rimozione o modifica un percorso per i file attendibile](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Considerazioni sulla sicurezza per le soluzioni Office  
 Quando si determinano le cartelle da aggiungere ai percorsi attendibili, è necessario tenere in considerazione diversi aspetti relativi alla sicurezza:  
  
-   Le cartelle locali sono considerate più sicure e sono implicitamente attendibili. I percorsi remoti, ad esempio le condivisioni file, devono essere designati come percorsi attendibili.  
  
-   Quando si aggiunge una directory ai percorsi attendibili, questa azione concede l'attendibilità totale non solo alle soluzioni Office, ma anche al codice VBA e ActiveX. Per questo motivo, la directory radice e le cartelle Documenti non devono essere designate come attendibili.  
  
-   Anche se il documento stesso è designato come attendibile mediante l'uso di percorsi attendibili, per rendere attendibile la personalizzazione sono necessarie ulteriori autorizzazioni. È possibile concedere attendibilità totale alla personalizzazione firmando i manifesti con un certificato, rispondendo tramite clic alla richiesta di attendibilità o installando la soluzione Office nella directory Programmi.  
  
-   È possibile archiviare il documento o la cartella di lavoro di una soluzione a livello di documento nella stessa directory dell'assembly o in una directory diversa. Ad esempio, il documento potrebbe trovarsi in un server SharePoint e l'assembly potrebbe essere in una condivisione file di rete. Per ulteriori informazioni, vedere [procedura: pubblicare una soluzione Office a livello di documento in un Server di SharePoint tramite ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Vedere anche  
 [Concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Risoluzione dei problemi di sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  