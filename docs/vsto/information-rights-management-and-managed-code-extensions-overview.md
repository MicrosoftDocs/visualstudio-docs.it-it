---
title: Cenni preliminari sulle estensioni di codice gestito e di Information Rights Management | Documenti Microsoft
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
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c70f5667cf7b2d795083589db9d9e4d5ca92193d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Cenni preliminari sul servizio Information Rights Management e sulle estensioni di codice gestito
  Microsoft Office Word e Microsoft Office Excel forniscono Information Rights Management (IRM), una funzionalità che consentono di evitare che utenti non autorizzati di visualizzare o modificare le informazioni riservate. Per informazioni dettagliate sul funzionamento di Information Rights Management, vedere la Guida dell'applicazione di Office specifica.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>Esecuzione di codice sottostante i documenti con autorizzazioni limitate  
 Se la soluzione contiene un documento o una cartella di lavoro che utilizza IRM, per impostazione predefinita, Word ed Excel che consentono di eseguire qualsiasi codice. Se l'autore del documento o di accesso controllo completo, è possibile modificare il valore predefinito in modo che la soluzione funzioni. Per ulteriori informazioni, vedere [procedura: esecuzione di codice sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM impedisce l'uso di <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> per recuperare o modificare i dati memorizzati nella cache del documento.  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>Utenti finali autorizzazioni limitate per i documenti che usano le estensioni di codice gestito  
 Chiunque abbia accesso completo alla cartella di lavoro o al documento nella soluzione possa utilizzare IRM per limitare le autorizzazioni. Ad esempio, se un utente finale del reparto contabilità Usa una soluzione che popola automaticamente un foglio di lavoro con i dati da un database, potrebbe essere che l'utente consentire la modifica accesso solo agli utenti del proprio reparto e accesso in lettura ad altri utenti. Quando l'utente aggiunge le autorizzazioni limitate, per impostazione predefinita, non è possibile eseguire il code-behind del foglio di lavoro e il foglio di lavoro non verrà popolato con dati.  
  
 Per risolvere il problema, un utente con accesso completo alla cartella di lavoro o al documento necessario modificare le impostazioni di autorizzazione predefinita per consentire l'accesso programmatico al modello a oggetti. Per ulteriori informazioni, vedere [procedura: esecuzione di codice sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protezione con password nei documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  