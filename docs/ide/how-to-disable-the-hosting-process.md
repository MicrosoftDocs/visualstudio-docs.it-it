---
title: 'Procedura: Disabilitare il processo di hosting | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b43e285c35601cb0d50536a5f4c499d09ae9bbad
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-disable-the-hosting-process"></a>Procedura: disabilitare il processo di hosting
Le chiamate ad alcune API possono essere influenzate quando il processo di hosting è abilitato. In questi casi è necessario disabilitare il processo di hosting per restituire i risultati corretti.  
  
### <a name="to-disable-the-hosting-process"></a>Per disabilitare il processo di hosting  
  
1.  Aprire un progetto eseguibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. I progetti che non producono file eseguibili (ad esempio librerie di classi o progetti di servizio) non dispongono di questa opzione.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
3.  Fare clic sulla scheda **Debug**.  
  
4.  Deselezionare la casella di controllo **Abilita processo di hosting di Visual Studio**.  
  
 Quando il processo di hosting viene disabilitato, diverse funzionalità di debug non sono disponibili o presentano prestazioni ridotte. Per altre informazioni, vedere [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md).  
  
 In generale, quando il processo di hosting viene disabilitato:  
  
-   Aumenta il tempo necessario per avviare il debug di applicazioni [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   La valutazione dell'espressione della fase di progettazione non è disponibile.  
  
-   Il debug parzialmente attendibile non è disponibile.  
  
## <a name="see-also"></a>Vedere anche

[Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md)   
[Processo di hosting (vshost.exe)](../ide/hosting-process-vshost-exe.md)