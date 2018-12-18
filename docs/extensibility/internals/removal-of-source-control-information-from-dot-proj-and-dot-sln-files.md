---
title: Rimozione di informazioni sul controllo di origine da. Proj e. Sln (file) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 695a4ccfc5da20bda25c78929488625c244959a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Rimozione di informazioni sul controllo di origine da. Proj e. Sln (file)
Nella versione 1.2 dell'API di plug-in controllo di origine, lo strumento informazioni vengono archiviate in un MSSCCPRJ. File SCC. Il vantaggio di MSSCCPRJ. File SCC è che le informazioni di controllo del codice sorgente non è origine - controllate, come in file con estensione sln e di proj.  
  
## <a name="version-12-changes"></a>Modifiche della versione 1.2  
 In origine plug-in del controllo che si basano sull'API di plug-in del controllo origine versione 1.1, sono archiviate informazioni sul controllo del codice sorgente nel progetto (proj) e i file di soluzione (sln). Il percorso del database delle informazioni di controllo di origine specificato da di AuxPath e la posizione specifica all'interno del database specificata da ProjName. Questo comportamento può causare problemi dopo ramo, divisione o operazioni di copia perché il ProjName in genere risulterà non valido dopo qualsiasi di queste operazioni.  
  
 Nell'API di plug-in del controllo origine versione 1.1, l'IDE utilizzata ~ file SAK per rilevare se un plug-in supportati di MSSCCPRJ. Metodo di controllo del codice sorgente dell'archiviazione delle informazioni di controllo di origine. L'API di plug-in controllo origine versione 1.2 fornisce una nuova funzionalità per il supporto per MSSCCPRJ di rilevamento. File di controllo del codice sorgente senza utilizzare un ~ file SAK. Per ulteriori informazioni, vedere [eliminazione di ~ SAK file](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)