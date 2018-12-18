---
title: Convalida di documenti XML | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c4be3c2f5428b7b2c246c1649a73ae8584ffe28e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="xml-document-validation"></a>Convalida di documenti XML
L'editor XML verifica la sintassi XML 1.0 ed esegue inoltre la convalida dei dati durante la digitazione. L'editor può eseguire la convalida tramite una DTD (Document Type Definition) o uno schema. Le sottolineature ondulate di colore rosso evidenziano gli errori di formato del codice XML 1.0. Le sottolineature ondulate di colore blu mostrano gli errori di semantica rilevati sulla base della DTD o della convalida dello schema. A ciascun errore è associata una voce nell'elenco degli errori. È possibile inoltre visualizzare il messaggio di errore posizionando per qualche istante il puntatore del mouse sulla sottolineatura ondulata.  
  
 Gli schemi usati nella convalida vengono individuati confrontando il `targetNamespace` di uno schema compilato con la dichiarazione xmlns dell'elemento. Gli schemi compilati vengono caricati da una delle seguenti posizioni, elencate in ordine di priorità:  
  
-   Il nome del file specificato nella **schemi** campo della finestra delle proprietà del documento.  
  
-   Schema inline o DTD.  
  
-   Una DTD esterna o un attributo `xsd:schemaLocation` e `xsd:noNamespaceSchemaLocation`  
  
-   Un URI dello spazio dei nomi dello schema XDR "x-schema".  
  
Gli schemi possono essere rilevati anche nelle seguenti posizioni aggiuntive quando lo schema dispone di uno spazio dei nomi di destinazione non vuoto:  
  
-   Un'altra finestra dell'editor contenente lo schema.  
  
-   Uno schema nella soluzione corrente.  
  
-   Uno schema dalla directory della cache degli schemi.  
  
## <a name="xslt-files"></a>File XSLT  
 Quando si modifica un file XSLT, viene usato per la convalida il file xslt.xsd che si trova nella cache degli schemi. Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu. Gli errori del compilatore XSLT vengono visualizzati con una sottolineatura ondulata di colore rosso.  
  
## <a name="xml-schema-xsd-files"></a>File XSD (XML Schema)  
 Quando si modifica un file di schema XML, viene usato per la convalida il file xsdschema.xsd che si trova nella cache degli schemi. Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu. Anche gli errori di compilazione vengono visualizzati con una sottolineatura ondulata di colore rosso.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)