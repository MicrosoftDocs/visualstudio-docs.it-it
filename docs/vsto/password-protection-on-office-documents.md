---
title: Protezione con password nei documenti di Office | Documenti Microsoft
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
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 52cadcec85580a9214da844bf887323227490f22
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="password-protection-on-office-documents"></a>Sicurezza tramite password di documenti di Office
  È possibile impostare una password per i documenti di Microsoft Office Word e cartelle di lavoro di Microsoft Office Excel, in modo che non può essere aperto da un utente che non conoscono la password. Questa opzione è denominata **Password all'apertura**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 È possibile creare progetti a livello di documento utilizzando documenti esistenti e le cartelle di lavoro che hanno **Password all'apertura** abilitato. Il comportamento in Visual Studio è diverso per i documenti di Word ed Excel con **Password all'apertura** abilitato.  
  
 Per informazioni sull'abilitazione **Password all'apertura**, vedere la Guida di Word o Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Comportamento di Excel e Word  
 Ogni volta che si apre una cartella di lavoro di Excel in Visual Studio con **Password all'apertura** abilitata, viene richiesta la password. Quando si compila la soluzione verrà richiesto per la password, perché il documento viene aperto durante la compilazione.  
  
 La prima volta che si apre un documento di Word in Visual Studio con **Password all'apertura** abilitata, viene richiesta la password. Dopo aver immesso la password, **Password all'apertura** viene rimosso dal documento e aprire il documento non è più necessaria una password. Se si desidera che il documento nella soluzione per richiedere una password prima che può essere aperto, è necessario abilitare **Password all'apertura** dopo la compilazione finale e prima di distribuire la soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Cenni preliminari sulle estensioni di codice gestito e di Information Rights Management](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Procedura: consentire codice per l'esecuzione sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  