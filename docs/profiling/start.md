---
title: Start | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf374c03f7918e48c57f221ada22e43b435c0a78
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="start"></a>Start
L'opzione **Start** è un'opzione di VSPerfCmd.exe che consente di inizializzare il profiler con il metodo di profilatura specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Method`  
 Deve essere una delle parole chiave seguenti:  
  
-   **TRACE**: specifica il metodo di strumentazione.  
  
-   **SAMPLE**: specifica il metodo di campionamento.  
  
-   **COVERAGE**: specifica il code coverage.  
  
-   **CONCURRENCY**: specifica il metodo di conflitto di risorse.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 È necessario specificare l'opzione **Output** quando nella riga di comando viene specificato **Start**.  
  
 **Output:** `filename`  
 Specifica il nome del file di output.  
  
## <a name="exclusive-options"></a>Opzioni esclusive  
 È possibile usare le opzioni seguenti solo con l'opzione **Start** nella riga di comando.  
  
 **CrossSession**&#124;**CS**  
 Abilita la profilatura tra processi. Sono supportati entrambi i nomi dell'opzione **CrossSession** e **CS**.  
  
 **User:**[`domain\`]`username`  
 Consente l'accesso client al monitor con l'account specificato.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** specifica un contatore delle prestazioni di Windows da includere come contrassegno nel file di dati di profilatura. **AutoMark** specifica l'intervallo in millisecondi tra le raccolte del file di dati.  
  
## <a name="invalid-options"></a>Opzioni non valide  
 Non è possibile usare le opzioni seguenti con l'opzione **Start** nella riga di comando.  
  
 **Status**  
 **Status** viene applicato ai processi profilati. Questa opzione elenca i processi e i thread insieme al relativo stato di profilatura corrente (On/Off). Ad esempio, se un processo viene arrestato, **Status** non indica questo stato nel rapporto. **Status** mostra che il processo è profilato o non profilato.  
  
 **Shutdown**[**:**`Timeout`]  
 Disattiva il profiler.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare l'opzione **Start** di VSPerfCmd.exe per l'inizializzazione del profiler.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)