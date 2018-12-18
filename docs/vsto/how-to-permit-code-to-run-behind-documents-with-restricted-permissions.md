---
title: "Procedura: consentire codice per l'esecuzione sottostante i documenti con autorizzazioni limitate | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eb5b9421bd6d0228a93ba7ba7516c9ebc7b7c761
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Procedura: supportare l'esecuzione di codice sottostante i documenti con autorizzazioni limitate
  È possibile utilizzare la funzionalità Information Rights Management (IRM) di Microsoft Office per limitare le autorizzazioni a un documento o una cartella di lavoro. Per impostazione predefinita, il codice dietro a un documento con limitazioni di Microsoft Office Word o una cartella di lavoro di Microsoft Office Excel non è consentito per l'esecuzione. È possibile modificare il valore predefinito in modo che le estensioni di codice gestito possono accedere il modello a oggetti e la soluzione funzionerà.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 È necessario essere l'autore del documento o cartella di lavoro o disporre di accesso controllo completo per essere in grado di modificare le impostazioni di autorizzazione.  
  
### <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Per consentire di codice sottostante i documenti con autorizzazioni limitate  
  
1.  Aprire la cartella di lavoro o un documento di Word o Excel.  
  
2.  Fare clic su di **File** scheda, scegliere **Prepare**, scegliere **limita le autorizzazioni**, quindi fare clic su **accesso limitato**.  
  
    > [!NOTE]  
    >  Al primo utilizzo, viene chiesto di installare il client Windows Rights Management. Dopo aver installato il client, potrebbe essere necessario ripetere i passaggi.  
  
3.  Nel **autorizzazione** nella finestra di dialogo **Limita autorizzazioni per questo documento**, quindi fare clic su **altre opzioni**.  
  
4.  In **autorizzazioni aggiuntive per gli utenti**selezionare **accedere al contenuto a livello di codice**.  
  
 Word o Excel consentirà l'accesso programmatico al modello a oggetti.  
  
## <a name="see-also"></a>Vedere anche  
 [Information Rights Management e Cenni preliminari sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protezione con password nei documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  