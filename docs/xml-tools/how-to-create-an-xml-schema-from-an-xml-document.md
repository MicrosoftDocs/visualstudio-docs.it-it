---
title: 'Procedura: creare uno Schema XML da un documento XML | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0541e89e72670905172129ffbb141ae8ae9e727f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedura: creare uno schema XML da un documento XML
L'editor XML consente di creare uno schema XSD (XML Schema Definition Language) da un documento XML. Il documento di istanza XML determina come viene generato lo schema nel seguente modo:  
  
-   Se al documento XML non è associato alcuno schema o DTD (Document Type Definition), i dati del documento XML vengono usati per inferire un nuovo schema XML.  
  
-   Se al documento XML è associata una DTD, la DTD esterna e il subset interno vengono convertiti in uno schema XML corrispondente.  
  
-   Se il documento XML contiene uno schema XDR (XML-Data Reduced) inline, lo schema XDR viene convertito in uno schema XML corrispondente.  
  
Gli schemi creati vengono quindi usati per fornire IntelliSense al documento XML.  
  
Per ulteriori informazioni sul motore di inferenza dello schema, vedere [deduzione di uno Schema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).  
  
### <a name="to-create-an-xml-schema"></a>Per creare uno schema XML  
  
1.  Caricare un documento di istanza XML nell'editor XML.  
  
2.  Fare clic su di **Create Schema** pulsante il **barra degli strumenti**.  
  
     Viene creato e aperto un documento di schema XML per ogni spazio dei nomi rilevato nel documento di istanza XML. Ogni schema viene aperto come file esterno temporaneo.  
  
     Gli schemi possono essere salvati su disco, aggiunti al progetto oppure eliminati.  
  
    > [!NOTE]
    >  Il **Create Schema** comando è disponibile dal menu di scelta rapida dell'Editor XML e in anche il **XML** menu.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)