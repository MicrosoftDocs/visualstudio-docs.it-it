---
title: ToggleHUD | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86ce582ab49d4d079f01f7231f49aa761baa1069
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="togglehud"></a>ToggleHUD
Attiva o disattiva la diagnostica della grafica *HUD* o disattivazione di sovrapposizione (Head-Up Display).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Note  
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Visualizza informazioni di runtime sull'applicazione e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando il [AddMessage](addmessage.md) funzione membro.  
  
 Per attivare o disattivare l'HUD, non è necessario essere attivamente acquisizione di informazioni grafiche, vale a dire, può essere modificato tramite un'istanza del `VsgDbg` (classe), ma la [Init](init.md) funzione membro non deve essere chiamato per primo.