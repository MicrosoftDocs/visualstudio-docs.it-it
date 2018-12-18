---
title: DONT_SAVE_VSGLOG_TO_TEMP | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b70ddf2933b8bd2d96db1636612cb35a6a759a1a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Valore  
 Un simbolo del preprocessore che per la presenza o assenza determina se un file di log di grafica viene salvato nella directory di file temporanei dell'utente. Se questo simbolo è definito, quindi il nome di file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory corrente dell'applicazione acquisita o è un percorso assoluto; in caso contrario, il nome di file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.  
  
## <a name="remarks"></a>Note  
 A seconda dei privilegi dell'utente, il file di log di grafica potrà non essere in grado di essere salvata in una posizione arbitraria. È consigliabile che si vuole salvare i log di grafica in directory dei file temporanei dell'utente o un altro percorso funzionante, se non si è certi se è possibile scrivere il percorso in cui che la scelta dall'utente.  
  
 Per impedire che il file di log di grafica viene salvato nella directory di file temporanei, è necessario definito `DONT_SAVE_VSGLOG_TO_TEMP` prima di includere `vsgcapture.h`.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come salvare il file di log di grafica in un percorso assoluto nel computer host.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)