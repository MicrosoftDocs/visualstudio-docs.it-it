---
title: ToggleHUD | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: baaa776a64d9b778c161ab7e65bb0f15e6c90099
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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