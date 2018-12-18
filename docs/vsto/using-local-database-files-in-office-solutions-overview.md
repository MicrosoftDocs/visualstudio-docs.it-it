---
title: Utilizzo di file di Database locale in soluzioni di Office | Documenti Microsoft
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
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1576af3c3fc8a1c7f514a4941eb849df03774c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>Cenni preliminari sull'utilizzo di file di un database locale nelle soluzioni Office
  È possibile includere un file di database, ad esempio un file di SQL Server Express (. mdf) o un file di Microsoft Office Access (mdb), nella soluzione Office. Ciò consente agli utenti finali di gestire un database locale nelle situazioni in cui la gestione di un database centralizzato non necessarie, ad esempio in una soluzione locale di inventario che viene utilizzata solo un singolo computer.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>L'importazione del File di Database in un progetto  
 Per importare il file di database al progetto, utilizzare il **configurazione guidata origine dati** per creare un'origine dati in base al file di database. La procedura guidata aggiunge il file di database e un dataset tipizzato al progetto.  
  
## <a name="deploying-the-database-file"></a>Il File di Database di distribuzione  
 Il **configurazione guidata origine dati** utilizza un percorso relativo per creare connessioni al file di database locale. In questo modo è possibile copiare la soluzione da un computer a un altro, se si gestiscono i percorsi relativi dei file.  
  
 Se si distribuisce la soluzione a un server e quindi distribuire il documento per ogni utente finale, è necessario distribuire il file di database manualmente e installarlo nella stessa posizione relativo al documento. Ciò significa che l'utente finale non è possibile spostare il documento in una nuova posizione nel proprio computer, a meno che non si anche sposta il file di database.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>File di Database locali e la memorizzazione nella cache il set di dati  
 Nelle soluzioni a livello di documento per Microsoft Office Excel e Microsoft Office Word, è possibile memorizzare nella cache set di dati nel documento contrassegnando l'istanza del set di dati con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Quando si aggiunge il file di database al progetto utilizzando il **configurazione guidata origine dati**, un dataset tipizzato viene aggiunto automaticamente al progetto. Raramente è necessario applicare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> per questo set di dati, poiché i dati sono già locali nel computer dell'utente. Per altre informazioni, vedere [Caching Data](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura: popolare documenti con dati da un Database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: aggiornare un'origine dati con i dati da un controllo Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Memorizzazione di dati nella cache](../vsto/caching-data.md)  
  
  