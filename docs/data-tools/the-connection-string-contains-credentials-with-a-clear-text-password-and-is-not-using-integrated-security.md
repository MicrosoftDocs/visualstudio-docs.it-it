---
title: La stringa di connessione contiene credenziali con una password come testo non crittografato e non utilizza la sicurezza integrata | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 1ecca5a69893c92edbeb996606f94cac71e4a3c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La stringa di connessione contiene credenziali con una password in testo non crittografato e non utilizza la sicurezza integrata
Salvare la stringa di connessione nel file DBML corrente e i file di configurazione dell'applicazione con queste informazioni riservate?  Fare clic su No per salvare la stringa di connessione senza le informazioni riservate.  
  
 Quando si usano connessioni dati in cui sono contenute informazioni riservate, ad esempio le password incluse nella stringa di connessione, è possibile salvare la stringa di connessione nel file DBML di un progetto e il file di configurazione dell'applicazione con o senza le informazioni riservate.  
  
> [!WARNING]
>  Impostare in modo esplicito il **connessione** proprietà **le impostazioni dell'applicazione** proprietà **False** la password verrà aggiunta nel file DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Per salvare la stringa di connessione con le informazioni riservate nelle impostazioni dell'applicazione del progetto  
  
-   Scegliere **Sì**.  
  
     La stringa di connessione viene archiviata come impostazione dell'applicazione e include le informazioni riservate in testo normale. Il file DBML non contiene le informazioni riservate.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Per salvare la stringa di connessione senza le informazioni riservate nelle impostazioni dell'applicazione del progetto  
  
-   Fare clic su **No**.  
  
     La stringa di connessione viene archiviata come impostazione dell'applicazione, ma non viene inclusa la password.  
  
## <a name="see-also"></a>Vedere anche
[Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)