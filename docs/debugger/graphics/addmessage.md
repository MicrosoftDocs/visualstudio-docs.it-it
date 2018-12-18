---
title: AddMessage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de3460a345dba21e3a8f481adb510b9e3bdd4990
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="addmessage"></a>AddMessage
Aggiunge un messaggio personalizzato alla diagnostica della grafica *HUD* (Head-Up Display).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `szMessage`  
 Messaggio da aggiungere a HUD.  
  
## <a name="remarks"></a>Note  
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Vengono visualizzate le informazioni di runtime sull'applicazione e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando questa funzione.  
  
 Per aggiungere un messaggio a HUD, non è necessario essere attivamente acquisizione di informazioni grafiche, vale a dire, è possibile aggiungere un messaggio tramite un'istanza del `VsgDbg` (classe), ma la [Init](init.md) funzione membro non in modo da non essere chiamato per primo. I messaggi vengono visualizzati solo in HUD, non vengono registrati nei file di log di grafica.