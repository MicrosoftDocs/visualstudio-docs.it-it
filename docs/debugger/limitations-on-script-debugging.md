---
title: Limitazioni del debug di Script | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6679e781e564a58d6a98b7d0190f2f2b4e9fa74
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="limitations-on-script-debugging"></a>Limitazioni del debug di script
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supporta il debug di script lato client, soggetto alle limitazioni trattate in questo argomento.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Limitazioni sul mapping dei punti di interruzione con script lato client  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di impostare un punto di interruzione in un file HTML o ASPX lato server trasformato in un file lato client in fase di esecuzione. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] esegue il mapping del punto di interruzione dal file lato server a un punto di interruzione corrispondente nel file lato client, soggetto alle seguenti limitazioni:  
  
-   I punti di interruzione devono essere impostati all'interno di blocchi `<script>`. Non è possibile eseguire il mapping di punti di interruzione in script inline o blocchi `<% %>`.  
  
-   L'URL del browser per la pagina deve contenere il nome della pagina. Ad esempio http://microsoft.com/default.apsx. I punti di interruzione in grado di riconoscere un reindirizzamento da un indirizzo, ad esempio http://microsoft.com alla pagina predefinita.  
  
-   Il punto di interruzione deve essere impostato nella pagina specificata nell'URL del browser, non in un file di controllo (ascx) ASPX, in una pagina master o in un altro file incluso dalla pagina. Non è possibile eseguire il mapping dei punti di interruzione impostati nelle pagine incluse.  
  
-   Non è possibile eseguire il mapping dei punti di interruzione impostati nei blocchi `<script defer=true>`.  
  
-   Per i punti di interruzione impostati nei blocchi `<script id="">`, l'attributo `id` viene ignorato dal mapping dei punti di interruzione.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Mapping dei punti di interruzione e righe duplicate  
 Per trovare la posizione corrispondente negli script lato server e lato client, l'algoritmo di mapping dei punti di interruzione esamina il codice su ogni riga. L'algoritmo presuppone che ogni riga sia univoca. Se due o più righe contengono lo stesso codice e si imposta un punto di interruzione su una delle righe duplicate, l'algoritmo di mapping dei punti di interruzione potrebbe selezionare il duplicato errato nel file lato client. Per evitare questo problema, aggiungere un commento alla riga in cui è stato impostato il punto di interruzione. Ad esempio:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```