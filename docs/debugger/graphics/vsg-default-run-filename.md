---
title: VSG_DEFAULT_RUN_FILENAME | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7fe31b96911329089174772094784c0d0f3371c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Definisce il nome file predefinito del file di log di grafica.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parametri  
 `filename`  
 Nome file assegnato per impostazione predefinita al file di log di grafica quando le informazioni grafiche vengono acquisite a livello di codice.  
  
## <a name="value"></a>Valore  
 Valore letterale stringa che rappresenta il nome del file di log di grafica. Per impostazione predefinita, L"default.vsglog".  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Note  
 Se viene definito il simbolo del preprocessore `DONT_SAVE_VSGLOG_TO_TEMP`, il nome del file è relativo alla directory corrente dell'applicazione acquisita o è un percorso assoluto; in caso contrario, è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.  
  
 Per modificare il nome file definito, è necessario ridefinirlo prima di includere `vsgcapture.h` nel programma.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come modificare il nome file predefinito del file di acquisizione:  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)