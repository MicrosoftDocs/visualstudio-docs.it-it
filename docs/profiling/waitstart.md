---
title: WaitStart | Microsoft Docs
description: Informazioni che l'opzione WaitStart fa sì che il sottocomando VSPerfCmd.exe Start venga restituito solo quando il profiler è stato inizializzato o quando è trascorso il numero di secondi specificato.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b883ae215854994918419fb311d94ad921989740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911472"
---
# <a name="waitstart"></a>WaitStart
Con l'opzione WaitStart, il sottocomando Start di *VSPerfCmd.exe* restituisce il controllo solo quando il profiler è stato inizializzato o dopo il numero di secondi specificato. Per impostazione predefinita, il comando Start restituisce il controllo immediatamente. Se il sottocomando Start restituisce il controllo senza inizializzare il profiler, viene restituito un errore. Se non viene specificato il numero di secondi, il comando Start attende per un periodo di tempo illimitato.

 L'opzione WaitStart è utile in file batch per assicurarsi che il profiler sia stato inizializzato.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametri
 `Seconds` Numero di secondi di attesa prima che il sottocomando Start restituisca il controllo.

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione WaitStart può essere usata solo con il sottocomando Start.

 **Output:** `filename` Specifica il nome del file di output.

## <a name="remarks"></a>Commenti

## <a name="example"></a>Esempio
 In questo esempio di file batch, il comando Start attenderà per 5 secondi l'inizializzazione del profiler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
