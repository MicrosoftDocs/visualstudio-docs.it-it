---
title: Motore di debug | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70e572b73f8474f77a17989c790f2e7336f9d7a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debug-engine"></a>Motore di debug
Un motore di debug (DE) funziona con l'interprete o a un sistema operativo per fornire servizi di debug, ad esempio la valutazione di espressioni, i punti di interruzione e controllo di esecuzione. La Germania è responsabile del monitoraggio dello stato di un programma in fase di debug. A tale scopo, la Germania Usa qualsiasi metodi sono disponibili per il processo di runtime supportate, se la CPU o le API fornito dal runtime.  
  
 Ad esempio, common language runtime (CLR) fornisce meccanismi per monitorare un programma in esecuzione tramite le interfacce ICorDebugXXX. Un Germania che supporta CLR Usa le interfacce ICorDebugXXX appropriate per tenere traccia di un programma di codice gestito in fase di debug. Comunica quindi tutte le modifiche dello stato per la gestione di debug di sessione (SDM), che inoltra tali informazioni per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  Un motore di debug destinato a una specifica del runtime, vale a dire, il sistema in cui il programma in fase di debug viene eseguito. CLR è il runtime per il codice gestito e il runtime di Win32 per applicazioni Windows native. Se la lingua è creare possono essere destinati a uno di questi due runtime, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce già i motori di debug necessari. È necessario implementare solo un analizzatore di espressioni.  
  
## <a name="debug-engine-operation"></a>Operazione del motore di debug  
 I servizi di monitoraggio vengono implementati tramite le interfacce DE e possono causare il pacchetto di debug per la transizione tra diverse modalità operative. Per ulteriori informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md). È in genere solo un'implementazione DE per ogni ambiente di runtime.  
  
> [!NOTE]
>  Mentre sono disponibili implementazioni DE separate per Transact-SQL e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] condividono un singolo DE.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Abilita debug motori per eseguire una delle due modalità di debug: uno nello stesso processo come il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] della shell o nello stesso processo del programma di destinazione in corso il debug. Il modulo di quest'ultimo si verifica in genere quando il processo in corso il debug è effettivamente uno script in esecuzione con un interprete, e il motore di debug deve avere conoscenza approfondita dell'interprete per monitorare lo script. Si noti che in questo caso, l'interprete è effettivamente un runtime. motori di debug sono per le implementazioni specifiche di runtime. Inoltre, è possibile dividere l'implementazione di un singolo DE attraverso i limiti di processo e del computer (ad esempio, il debug remoto).  
  
 L'oggetto espone DE la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfacce di debug. Tutte le comunicazioni sono tramite COM. Se la Germania viene caricato in-process, out-of-process o in un altro computer, non si applica la comunicazione dei componenti.  
  
 La Germania funziona con un componente dell'analizzatore di espressioni per abilitare la Germania tale particolare in fase di esecuzione comprendere la sintassi delle espressioni. La Germania funziona anche con un componente gestore di simboli per accedere alle informazioni di debug sui simboli generate dal compilatore di linguaggio. Per ulteriori informazioni, vedere [analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md) e [simbolo Provider](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)   
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)