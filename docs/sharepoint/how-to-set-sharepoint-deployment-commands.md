---
title: 'Procedura: impostare i comandi di distribuzione di SharePoint | Documenti Microsoft'
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
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2f465deaaca406c28aab177434e72de9746fb101
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procedura: impostare i comandi di distribuzione di SharePoint
  È possibile personalizzare il processo di distribuzione mediante l'impostazione di comandi pre-distribuzione e post-distribuzione. Questi comandi vengono eseguiti prima e dopo le altre azioni di distribuzione durante il debug di soluzioni di SharePoint da Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Per aggiungere un comando di pre-distribuzione  
  
1.  Sulla barra dei menu scegliere **Progetto**, *Proprietà***NomeProgetto**.  
  
2.  Scegliere il **SharePoint** scheda.  
  
3.  Nel **riga di comando pre-distribuzione** testo immettere comandi MS-DOS o MSBuild per personalizzare questo passaggio.  
  
     Ad esempio, per elencare il contenuto della directory prima della distribuzione è stata completata, immettere **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Per aggiungere un comando di post-distribuzione  
  
1.  Sulla barra dei menu scegliere **Progetto**, *Proprietà***NomeProgetto**.  
  
2.  Scegliere il **SharePoint** scheda.  
  
3.  Nel **riga di comando post-distribuzione** testo immettere comandi MS-DOS o MSBuild per personalizzare questo passaggio.  
  
     Ad esempio, per elencare il contenuto della directory dopo la distribuzione è completata, immettere **dir**. Per utilizzare una variabile di MSBuild per copiare l'assembly dalla directory di compilazione, immettere **copiare $ (TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  