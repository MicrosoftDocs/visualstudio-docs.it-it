---
title: Recupero di una porta | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5f6065c91845df020325e279a1fa3858a4f75505
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="getting-a-port"></a>Recupero di una porta
Una porta rappresenta una connessione a un computer in cui i processi in esecuzione. Tale computer potrebbe essere il computer locale o un computer remoto (quale un sistema operativo non basato su Windows potrebbe eventualmente essere in esecuzione, vedere [porte](../../extensibility/debugger/ports.md) per altre informazioni).  
  
 Rappresentato da una porta di [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia. Consente di ottenere informazioni sui processi in esecuzione nel computer a che la porta è connessa.  
  
 Un motore di debug deve accedere a una porta per registrare i nodi di programma con la porta e soddisfare le richieste per le informazioni sul processo. Ad esempio, se il motore di debug implementa il [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) per l'implementazione dell'interfaccia di [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metodo può chiedere la porta per il processo necessario informazioni da restituire.  
  
 Visual Studio fornisce la porta necessaria per il motore di debug e questa porta viene ottenuto da un fornitore di porta. Se un programma è collegato a (o all'interno del debugger a causa di un'eccezione è stata generata, che attiva la finestra di dialogo [JIT] Just-in-Time), l'utente viene offerta la possibilità di trasporto (un altro nome per un fornitore di porta) da utilizzare. In caso contrario, se l'utente avvia il programma all'interno del debugger, il sistema del progetto specifica il fornitore della porta da utilizzare. In tutti i casi, Visual Studio crea il fornitore della porta, rappresentato da un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia e richiede una nuova porta chiamando [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con un [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interfaccia. Questa porta viene quindi passata motore di debug in un form o a un'altra.  
  
## <a name="example"></a>Esempio  
 Questo frammento di codice viene illustrato come utilizzare la porta fornita a [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) per registrare un nodo di programma in [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parametri non direttamente correlati a questo concetto sono stati omessi per maggiore chiarezza.  
  
> [!NOTE]
>  In questo esempio utilizza la porta per avviare e riprendere il processo e si presuppone che il [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interfaccia viene implementata sulla porta. Si tratta in alcun modo l'unico modo per eseguire queste attività, ed è possibile che la porta potrebbe non anche essere coinvolto diverso per il programma [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) forniti.  
  
```cpp  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Il programma di registrazione](../../extensibility/debugger/registering-the-program.md)   
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)   
 [Porte](../../extensibility/debugger/ports.md)