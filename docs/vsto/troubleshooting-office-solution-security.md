---
title: Risoluzione dei problemi di sicurezza delle soluzioni Office | Documenti Microsoft
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
helpviewer_keywords: security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2ab3571da02fa56cd905369ee44e372aedea4e36
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-office-solution-security"></a>Risoluzione dei problemi relativi alla sicurezza delle soluzioni Office
  In questo argomento contiene suggerimenti per la risoluzione dei problemi comuni che possono verificarsi quando si lavora con sicurezza delle soluzioni Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Trusted soluzioni non possono essere installate da siti con restrizioni  
 Gli utenti non è possibile installare una soluzione da un percorso web se il sito web è presente nell'area siti con restrizioni di Internet Explorer. Questo vale anche se la soluzione è firmata con un certificato attendibile.  
  
 L'URL del manifesto di distribuzione può essere suddivise in una delle cinque aree:  
  
-   Risorse del Computer  
  
-   Internet  
  
-   Intranet locale  
  
-   Siti attendibili  
  
-   Siti con restrizioni  
  
 Se il percorso del manifesto della distribuzione è stato assegnato all'area siti con restrizioni, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non installare la soluzione. Se il percorso è noto e può essere considerato attendibile, l'utente può rimuovere il percorso dall'area siti con restrizioni e installare la soluzione. Per informazioni su come gestire le zone, vedere [di editori attendibili ClickOnce configurazione](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Soluzioni non possono essere installate da condivisioni File di rete o indirizzi di siti Web quando sicurezza avanzata di Internet Explorer o sia installato Internet Explorer 7  
 Internet Explorer Enhanced Security Configuration (IEESC) in Windows Server 2003 e versioni successive e Internet Explorer 7 e versioni successive, in modo significativo limita la capacità degli utenti per accedere a Internet. Quando gli utenti tentano di installare soluzioni Office da un percorso web o condivisione di rete di file, è possibile che venga visualizzato il seguente messaggio di errore: "la funzionalità personalizzata in questa applicazione non funzionerà perché il certificato utilizzato per firmare il manifesto di distribuzione per *SolutionName* non è attendibile. Contattare l'amministratore per ulteriore assistenza."  
  
 Con IEESC e Internet Explorer 7 e versioni successive, se l'URL del manifesto della distribuzione è stato categorizzato nell'area Internet, il manifesto deve essere un certificato da un autore attendibile o non è possibile installare la soluzione. Senza IEESC, il comportamento predefinito è per richiedere all'utente finale per prendere una decisione di attendibilità.  
  
 Per gestire l'effetto di IEESC e Internet Explorer 7 e versioni successive, identificare i siti web e i percorsi UNC universal naming convention (UNC) che si considera attendibile e aggiungerli a una delle aree di sicurezza attendibili (intranet locale o siti attendibili). Per informazioni su come gestire le zone, vedere [di editori attendibili ClickOnce configurazione](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  