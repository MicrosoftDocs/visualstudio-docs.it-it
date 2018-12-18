---
title: Eliminazione di ~ SAK file | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61227652bf191280f69466f127c4a400ea43856e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="elimination-of-sak-files"></a>Eliminazione di ~ SAK file
1.2 API di plug-in controllo di origine, il ~ SAK file sono stati sostituiti da flag di capacità e nuove funzioni di rilevare se un plug-in controllo del codice sorgente supporta il file MSSCCPRJ estrazioni condivise.  
  
## <a name="sak-files"></a>~ Il file SAK  
 Visual Studio .NET 2003 creati i file temporanei con preceduti ~ SAK. Questi file vengono usati per determinare se un plug-in controllo del codice sorgente supporta:  
  
-   Il MSSCCPRJ. File SCC.  
  
-   Estrazioni multiple (condivise).  
  
 Per i plug-in che supportano le funzioni avanzate disponibili nella 1.2 di API plug-in controllo origine, l'IDE è possibile rilevare queste funzionalità senza creare file temporanei tramite l'utilizzo di nuove funzionalità, flag e funzioni, dettagliate nelle sezioni seguenti.  
  
## <a name="new-capability-flags"></a>Nuovo flag di capacità  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nuove funzioni  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Se un plug-in controllo del codice sorgente supporta più estrazioni (condivise), quindi dichiara il `SCC_CAP_MULTICHECKOUT` funzionalità e implementa il `SccIsMultiCheckOutEnabled` (funzione). Questa funzione viene chiamata ogni volta che si verifica un'operazione di estrazione in uno dei progetti di controllo del codice sorgente.  
  
 Se un plug-in controllo del codice sorgente supporta la creazione e utilizzo di un MSSCCPRJ. File SCC, quindi si dichiara il `SCC_CAP_SCCFILE` funzionalità e implementa il [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Questa funzione viene chiamata con un elenco di file. La funzione restituisce `TRUE/FALSE` per ogni file indicare se un MSSCCPRJ deve essere usata da Visual Studio. File SCC relativo. Se il plug-in controllo del codice sorgente sceglie di non supportare queste nuove funzionalità e funzioni, è possibile utilizzare la seguente chiave del Registro di sistema per disabilitare la creazione di questi file:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = DWORD: 00000001  
  
> [!NOTE]
>  Se questa chiave del Registro di sistema è impostata su DWORD: 00000000, è equivalente alla chiave da inesistente e Visual Studio continua a tentare di creare file temporanei. Tuttavia, se la chiave del Registro di sistema è impostata su DWORD: 00000001, Visual Studio non tenta di creare i file temporanei. In alternativa, si presuppone che il plug-in controllo del codice sorgente non supporta il MSSCCPRJ. File di controllo del codice sorgente e non supporta estrazioni condivise.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)