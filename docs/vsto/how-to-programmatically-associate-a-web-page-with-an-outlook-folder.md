---
title: 'Procedura: associare una pagina Web una cartella di Outlook a livello di codice | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5495066b05ded6fc49dfe92ed489932d8c75b24d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Procedura: associare una pagina Web a una cartella di Outlook a livello di codice
  In questo esempio cerca una cartella denominata `HtmlView` in Microsoft Office Outlook. Se la cartella non esiste, il codice viene creata la cartella e assegna una pagina Web. Se la cartella esiste, il codice visualizza il contenuto della cartella.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle cartelle](../vsto/working-with-folders.md)   
 [Procedura: recuperare a livello di codice una cartella per nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: Creare cartelle personalizzate a livello di codice](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  