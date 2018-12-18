---
title: Mark | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e610644713d630ce4f54befa8535c3b00c7aaf92
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="mark"></a>Contrassegno
L'opzione **Mark** di VSPerfCmd.exe consente di inserire le informazioni specificate nel file di dati di profilatura. L'opzione Mark può essere elencata in un report di VSPerfReport separato o nella visualizzazione Contrassegni dell'interfaccia utente del profiler. È possibile usare **Mark** per specificare i punti di inizio e fine nel report e visualizzare i filtri.  
  
 L'opzione **Mark** deve essere l'unica opzione specificata nella riga di comando.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametri  
 `MarkID`  
 Intero definito dall'utente elencato come ID contrassegno nelle visualizzazioni e nei report del profiler. `MarkID` non deve essere univoco.  
  
 `MarkName`  
 (Facoltativo) Stringa definita dall'utente elencata come Nome contrassegno nelle visualizzazioni e nei report del profiler. Se non si specifica `MarkName`, il campo Nome contrassegno dell'elenco dei contrassegni sarà vuoto. Racchiudere le stringhe che contengono spazi o barre ("/") tra virgolette.  
  
## <a name="example"></a>Esempio  
 Questo esempio inserisce un contrassegno con ID 123 e il nome di contrassegno "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)