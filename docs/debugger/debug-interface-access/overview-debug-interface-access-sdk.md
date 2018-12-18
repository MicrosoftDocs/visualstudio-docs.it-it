---
title: Panoramica (Debug Interface Access SDK) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb13b9a77bcd34b22a7a82182a63440cb02a4e76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="overview-debug-interface-access-sdk"></a>Panoramica (Debug Interface Access SDK)
Per accedere alle informazioni di debug Microsoft, utilizzare il DIA SDK. Il DIA SDK fornisce una COM basato su set di API che elimina la necessità di riscrivere il codice ogni volta che Microsoft cambia il formato delle informazioni di debug. Il DIA SDK consente inoltre di leggere da un insieme di versioni precedenti di informazioni di debug si trova nel file con estensione pdb e DBG generati da [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 5.0 e versioni successive.  
  
 Ogni interfaccia in DIA SDK rappresenta un oggetto COM diverso, salvo dove diversamente. Altre interfacce, quindi oggetti aggiuntivi, creati tramite query esplicita, ad esempio [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), anziché chiamando `QueryInterface` sui puntatori di interfaccia esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)