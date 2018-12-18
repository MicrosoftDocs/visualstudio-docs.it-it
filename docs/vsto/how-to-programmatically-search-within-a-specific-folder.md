---
title: "Procedura: eseguire la ricerca a livello di codice all'interno di una cartella specifica | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aedddb0eab79e66d9d5a41d70a4907a2f22951ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Procedura: eseguire la ricerca in una cartella specifica a livello di codice
  Nell'esempio viene utilizzata la `Find` e `FindNext` metodi per cercare testo nel campo soggetto di messaggi di posta elettronica presenti il **posta in arrivo**. Questo metodo utilizza un filtro di stringa per verificare la lettera T come lettera iniziale del `Subject` testo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle cartelle](../vsto/working-with-folders.md)   
 [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)   
 [Procedura: Recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  