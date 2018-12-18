---
title: Gli enumeratori | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84102435092096b7154a46100e9d857a31537482
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enumerators"></a>Enumeratori
In questa sezione sono elencati i tipi di dati di enumeratore nell'API di plug-in controllo di origine che è necessario conoscere il plug-in controllo del codice sorgente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Codice di comando](../extensibility/command-code-enumerator.md)  
 Enumera le opzioni per il [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) funzioni.  
  
 [Messaggio](../extensibility/message-enumerator.md)  
 Enumera i flag utilizzati per il callback di stampato, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Codice di stato file](../extensibility/file-status-code-enumerator.md)  
 Contiene valori costanti denominati che specificano lo stato di un file di controllo del codice sorgente.  
  
 [Codice di stato di directory](../extensibility/directory-status-code-enumerator.md)  
 Contiene valori costanti denominati che specificano lo stato di una directory nel controllo del codice sorgente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definisce il SDK di plug-in controllo di origine e descrive le risorse incluse.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Richiede all'utente per le opzioni avanzate per il comando specificato.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Esamina l'elenco di file per il relativo stato corrente. Inoltre, viene utilizzato il `pfnPopulate` funzione per segnalare al chiamante quando un file non corrispondono ai criteri per il `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Viene descritta la funzione di callback che viene utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in tramite l'IDE di controllo del codice sorgente.  
  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)  
 Fornisce un elenco completo di tutti gli elementi nell'API di plug-in del controllo origine.