---
title: 'Procedura: creare uno Schema XML da un documento XML | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b19421bf9cb9d974a837f557d8b75ac4d5ba89c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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