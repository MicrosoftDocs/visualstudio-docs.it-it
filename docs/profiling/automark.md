---
title: AutoMark | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9a482d3ed09f12c623986e604951b7d7855e6e8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="automark"></a>AutoMark
L'opzione **AutoMark** specifica il numero di millisecondi tra diverse raccolte di eventi del contatore delle prestazioni del software Windows. I contatori delle prestazioni di Windows sono specificati nell'opzione **WinCounter**.  
  
 Nella riga di comando può essere specificata una sola opzione **AutoMark**. Si noti che l'intervallo di campionamento di **WinCounter** specificato da **AutoMark** è indipendente dell'intervallo di campionamento principale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Parametri  
 `Milliseconds`  
 Specifica il numero di millisecondi tra le raccolte di eventi dei contatori delle prestazioni di Windows.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 **WinCounter:** `Path`  
 Specifica il contatore delle prestazioni di Windows da raccogliere. Quando si usa il metodo di strumentazione è possibile specificare più contatori di Windows. Quando si usa il metodo di campionamento è possibile specificare solo un contatore del software. L'opzione **WinCounter** deve essere specificata in una riga di comando che contiene l'opzione **Start**.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene impostato un intervallo di campionamento di 1000 millisecondi per due contatori delle prestazioni di Windows.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)