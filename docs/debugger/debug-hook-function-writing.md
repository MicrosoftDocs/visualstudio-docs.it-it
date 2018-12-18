---
title: Scrittura di funzioni Hook di debug | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 365196a01ba9e62ef0b26eb3a99278d4d77a4dd4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-hook-function-writing"></a>Scrittura di funzioni hook di debug
In questa sezione vengono descritte alcune funzioni hook di debug personalizzate che consentono di inserire il codice in alcuni punti predefiniti nell'ambito della normale elaborazione del debugger.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Funzioni hook del blocco client](../debugger/client-block-hook-functions.md)  
 Viene fornito materiale sussidiario e un prototipo per la scrittura di funzioni che convalidano o inseriscono nei report il contenuto dei dati archiviati nei blocchi _CLIENT_BLOCK.  
  
 [Funzioni hook di allocazione](../debugger/allocation-hook-functions.md)  
 Viene definita una funzione hook di allocazione, ne vengono esaminati i diversi utilizzi, vengono indicate le restrizioni e viene fornito un prototipo.  
  
 [Hook di allocazione e allocazioni di memoria CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Viene descritta la restrizione sulle funzioni hook di allocazione per ignorare in modo esplicito i blocchi `_CRT_BLOCK` se vengono effettuate chiamate alle funzioni della libreria di runtime del linguaggio C che allocano la memoria interna. Questo argomento vengono anche elencate le conseguenze se la funzione hook di allocazione non ignora `_CRT_BLOCK` blocchi (con esempi) e su come modificare l'allocazione predefinita funzione hook, **CrtDefaultAllocHook**.  
  
 [Funzioni hook per la creazione di report](../debugger/report-hook-functions.md)  
 Viene discussa la funzione `_CrtSetReportHook`, che è possibile utilizzare per filtrare i report in modo da concentrarsi su tipi specifici di allocazioni. In questo argomento viene fornito anche un prototipo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)  
 È possibile collegarsi alle tecniche di debug per la libreria di runtime del linguaggio C, tra cui: utilizzo della libreria di debug CRT, macro per la creazione di report, differenze tra `malloc` e `_malloc_dbg`, scrittura di funzioni hook di debug e heap di debug CRT.