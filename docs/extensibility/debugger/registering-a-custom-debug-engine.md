---
title: Motore di Debug di registrazione personalizzato | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 50903d9b45828725da03c0fcb0db0f08d7f884eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-custom-debug-engine"></a>Registrazione di un motore di Debug personalizzati
Il motore di debug deve registrarsi come una class factory segue le convenzioni COM, nonché registrare con Visual Studio tramite la sottochiave del Registro di sistema di Visual Studio.  
  
> [!NOTE]
>  Un esempio di come registrare un motore di debug, vedere l'esempio TextInterpreter, che viene compilato come parte di [esercitazione: creazione di un Debug motore utilizzando ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processo del Server di DLL  
 In genere, un motore di debug viene implementato nella propria DLL come server COM. Ciò significa che il motore di debug deve registrarsi il CLSID della relativa class factory COM prima di Visual Studio è possibile accedervi. Quindi il motore di debug deve registrarsi con Visual Studio per poter valutare tutte le proprietà, in caso contrario denominata anche metriche, il debug supporta del motore. La scelta delle metriche vengono scritti nella sottochiave del Registro di sistema di Visual Studio per il motore di debug dipende dalle funzionalità che supporta il motore di debug.  
  
 [Helper di SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrive non solo le posizioni del Registro di sistema necessarie per la registrazione di un motore di debug; vengono inoltre descritte la libreria dbgmetric.lib, che contiene un numero di funzioni utili e le dichiarazioni per gli sviluppatori di C++ che rendono la modifica del Registro di sistema più semplice.  
  
### <a name="example"></a>Esempio  
 Ecco un esempio tipico (tratto dall'esempio TextInterpreter) in cui viene illustrato come utilizzare il `SetMetric` funzione (dbgmetric.lib), per registrare un motore di debug con Visual Studio. Le metriche passate sono definite anche nel dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter è un motore di debug di base; non implementa e pertanto non consente di registrare, tutte le altre caratteristiche. Un motore di debug più completato avrebbe un intero elenco dei `SetMetric` supporta chiamate o i rispettivi equivalenti, uno per ogni funzionalità, il motore di debug.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di Debug personalizzati](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Esercitazione: Creazione di un motore di Debug tramite COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)