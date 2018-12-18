---
title: Scelta di una strategia di implementazione del motore di Debug | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fae5211ac270832f07038faafbd6f5bc463d3944
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Scelta di una strategia di implementazione del motore di Debug
Utilizzare l'architettura della fase di esecuzione per determinare la strategia di implementazione (DE) motore di debug. È possibile creare il motore di debug in-process per il programma da sottoporre a debug, in-process nel gestore di debug di Visual Studio sessione (SDM) oppure out-of-process per entrambi gli elementi. Le linee guida seguenti consentono di scegliere fra questi tre strategie.  
  
## <a name="guidelines"></a>Indicazioni  
 Sebbene sia possibile per la Germania sia out-of-process di SDM sia il programma da sottoporre a debug, non è in genere eseguire questa operazione. Le chiamate oltre i limiti di processo sono relativamente lente.  
  
 Eseguire il debug motori sono già forniti per l'ambiente di runtime nativo Win32 e per l'ambiente di common language runtime. Se per uno di questi ambienti, è necessario sostituire la Germania, è necessario creare il DE in-process con il SDM.  
  
 In caso contrario, è possibile scegliere tra la creazione di DE in-process per il SDM o in-process per il programma da sottoporre a debug. È importante prendere in considerazione se l'analizzatore di espressioni della DE accede di frequente per l'archivio dei simboli di programma e indica se l'archivio dei simboli può essere caricata in memoria per l'accesso rapido. Considerare anche quanto segue:  
  
-   Se non sono presenti molte chiamate tra l'analizzatore di espressioni e l'archivio dei simboli o se l'archivio dei simboli può essere letti nello spazio di memoria SDM, creare il DE per il SDM in-process. È necessario restituire il CLSID del motore di debug per il SDM al momento del collegamento al programma. Il SDM Usa questo CLSID per creare un'istanza in-process della DE.  
  
-   Se la Germania deve chiamare il programma per accedere all'archivio di simboli, creare il DE in-process con il programma. In questo caso, il programma crea l'istanza della DE.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)