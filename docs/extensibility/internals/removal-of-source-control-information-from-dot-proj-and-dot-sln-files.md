---
title: Rimozione di informazioni sul controllo di origine da. Proj e. Sln (file) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4131e3d5139911c6a1bb9b44d8d8acaefa6cb632
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Rimozione di informazioni sul controllo di origine da. Proj e. Sln (file)
Nella versione 1.2 dell'API di plug-in controllo di origine, lo strumento informazioni vengono archiviate in un MSSCCPRJ. File SCC. Il vantaggio di MSSCCPRJ. File SCC è che le informazioni di controllo del codice sorgente non è origine - controllate, come in file con estensione sln e di proj.  
  
## <a name="version-12-changes"></a>Modifiche della versione 1.2  
 In origine plug-in del controllo che si basano sull'API di plug-in del controllo origine versione 1.1, sono archiviate informazioni sul controllo del codice sorgente nel progetto (proj) e i file di soluzione (sln). Il percorso del database delle informazioni di controllo di origine specificato da di AuxPath e la posizione specifica all'interno del database specificata da ProjName. Questo comportamento può causare problemi dopo ramo, divisione o operazioni di copia perché il ProjName in genere risulterà non valido dopo qualsiasi di queste operazioni.  
  
 Nell'API di plug-in del controllo origine versione 1.1, l'IDE utilizzata ~ file SAK per rilevare se un plug-in supportati di MSSCCPRJ. Metodo di controllo del codice sorgente dell'archiviazione delle informazioni di controllo di origine. L'API di plug-in controllo origine versione 1.2 fornisce una nuova funzionalità per il supporto per MSSCCPRJ di rilevamento. File di controllo del codice sorgente senza utilizzare un ~ file SAK. Per ulteriori informazioni, vedere [eliminazione di ~ SAK file](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)