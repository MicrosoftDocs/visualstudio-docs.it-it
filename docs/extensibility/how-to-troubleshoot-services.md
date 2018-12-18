---
title: 'Procedura: risolvere i problemi relativi a servizi | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9efe3c1c7032f1db41272a03cf689e015a79522
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-troubleshoot-services"></a>Procedura: risolvere i problemi relativi a servizi
Esistono alcuni problemi comuni che possono verificarsi quando si tenta di ottenere un servizio:  
  
-   Il servizio non è registrato con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Il servizio è richiesto dal tipo di interfaccia e non dal tipo di servizio.  
  
-   Il pacchetto VSPackage che richiedono il servizio non è stato individuato.  
  
-   Viene utilizzato il provider del servizio non corretto.  
  
 Se non è possibile ottenere il servizio richiesto, la chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> restituisce null. È necessario verificare sempre null dopo la richiesta di un servizio:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Per risolvere i problemi relativi a un servizio  
  
1.  Esaminare il Registro di sistema per vedere se il servizio è stato registrato correttamente. Per ulteriori informazioni, vedere [procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md).  
  
     Nel seguente frammento di file con estensione reg Mostra come potrebbe essere registrato il servizio SVsTextManager:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     Nell'esempio precedente, il numero di versione è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ad esempio 12.0 o 14.0, la chiave {F5E7E71D-1401-11d1-883B-0000F87579D2} è l'identificatore di servizio (SID) del servizio, SVsTextManager e il {valore predefinito F5E7E720-1401-11D1-883B-0000F87579D2} è il GUID della gestione testo VSPackage, che fornisce il servizio del pacchetto.  
  
2.  Quando si chiama GetService, utilizzare il tipo di servizio e non il tipo di interfaccia. Quando si richiede un servizio da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> estrae il GUID dal tipo. Un servizio non verrà trovato in presenza delle condizioni seguenti:  
  
    1.  Un tipo di interfaccia viene passato al metodo GetService anziché il tipo di servizio.  
  
    2.  Nessun GUID viene assegnato in modo esplicito all'interfaccia. Pertanto, il sistema crea un GUID predefinito per un oggetto in base alle esigenze.  
  
3.  Assicurarsi che il pacchetto VSPackage che richiedono il servizio è stato individuato. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i siti di un pacchetto VSPackage al termine della creazione e prima di chiamare <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Se si dispone di codice in un costruttore di VSPackage che è un servizio, spostarla il metodo Initialize.  
  
4.  Assicurarsi che si utilizza il provider del servizio corretto.  
  
     Non tutti i provider di servizio sono simili. Il provider di servizi che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passa a una finestra degli strumenti è diversa da quella passa a un VSPackage. Il provider di servizi di finestra strumento conosce <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, ma non conosce <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi di VSPackage all'interno di una finestra degli strumenti.  
  
     Se una finestra degli strumenti ospita un controllo utente o qualsiasi altro contenitore di controllo, il contenitore verrà individuato dal modello di componente di Windows e non sarà possibile accedere a qualsiasi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] servizi. È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi VSPackage da un contenitore di controlli.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco dei servizi disponibili](../extensibility/internals/list-of-available-services.md)   
 [Utilizzando e servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)