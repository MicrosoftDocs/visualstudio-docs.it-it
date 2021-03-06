---
description: Usare il DIA SDK per accedere alle informazioni di debug Microsoft.
title: Panoramica (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c505216cd38b5321f291515794fc07ff58e8d698
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155362"
---
# <a name="overview-debug-interface-access-sdk"></a>Panoramica (Debug Interface Access SDK)
Usare il DIA SDK per accedere alle informazioni di debug Microsoft. Il DIA SDK fornisce un set di API basato su COM che elimina la necessità di riscrivere il codice ogni volta che il formato delle informazioni di debug viene modificato da Microsoft. Il DIA SDK consente inoltre di leggere da un set selezionato di versioni precedenti delle informazioni di debug, che si trovano nei file con estensione PDB e DBG generati dalle [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] versioni 5,0 e successive.

 Ogni interfaccia nel DIA SDK rappresenta un oggetto COM diverso, tranne se diversamente specificato. Le interfacce aggiuntive e quindi gli oggetti aggiuntivi vengono creati tramite query esplicite, ad esempio [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), anziché chiamando `QueryInterface` sui puntatori di interfaccia esistenti.

## <a name="see-also"></a>Vedi anche
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
