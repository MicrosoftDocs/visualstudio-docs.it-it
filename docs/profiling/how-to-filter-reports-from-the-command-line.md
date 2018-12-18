---
title: 'Procedura: Filtrare report tramite la riga di comando | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 27309a459128e6ed9ebb17d295bc39c6c621dcd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedura: filtrare rapporti tramite la riga di comando
Usando le opzioni del comando **VSPerfReport** è possibile filtrare i report per un intervallo di tempo specifico del file dei dati di profilatura o limitare i dati a uno o più processi o thread. Per altre informazioni su questo comando, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**StartTime:**[*Valore*]|Mostra solo i dati raccolti dopo il valore (in millisecondi).|  
|**EndTime:**[*Valore*]|Mostra solo i dati raccolti prima del valore (in millisecondi).|  
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file di filtro generato dalla finestra **Visual Studio Performance Report**.|  
|**MsFilter:**[*OraInizio,Durata*]|Mostra solo i dati di `StartTime` fino alla lunghezza di `Duration` (in millisecondi).|  
|**Process:**[*IDprocesso*]|Mostra solo i dati del processo specificato.|  
|**Thread:**[*IDthread*]|Mostra solo i dati del thread specificato.|  
|**Thread:**[*IDthread,IDprocesso*]|Mostra solo i dati del thread specificato associato al processo specificato.|