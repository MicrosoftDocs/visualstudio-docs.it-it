---
title: Servizio Essentials | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4db5404ed4cb307064d9d913c240b16051c25977
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="service-essentials"></a>Servizio Essentials
Un servizio è un contratto tra due pacchetti VSPackage. Un VSPackage fornisce un set specifico di interfacce per un altro VSPackage da utilizzare. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]è una raccolta di VSPackage che forniscono servizi agli altri pacchetti VSPackage.  
  
 Ad esempio, è possibile utilizzare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che è possibile utilizzare per scrivere nel log attività. Per ulteriori informazioni, vedere [procedura: utilizzare il registro attività](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce inoltre alcuni servizi predefiniti che non sono registrati. VSPackage possono sostituire incorporati o altri servizi, fornendo un override del servizio. Sostituzione di un solo servizio è consentito per qualsiasi servizio.  
  
 Services non dispone di alcun tipo di individuazione. Pertanto, è necessario conoscere l'ID di servizio (SID) di un servizio che si desidera utilizzare e, è necessario conoscere quali interfacce fornisce. La documentazione di riferimento per il servizio fornisce queste informazioni.  
  
-   Pacchetti VSPackage che forniscono servizi vengono chiamati i provider di servizi.  
  
-   I servizi forniti da altri pacchetti VSPackage sono denominati servizi globali.  
  
-   Servizi sono disponibili solo per il pacchetto VSPackage che li implementa o per qualsiasi oggetto che viene creato, sono denominati servizi locali.  
  
-   Servizi che sostituiscono i servizi predefiniti o i servizi forniti da altri pacchetti, vengono chiamati servizio esegue l'override.  
  
-   I servizi o servizio esegue l'override, vengono caricato su richiesta, vale a dire, il provider del servizio viene caricato quando viene richiesto il servizio fornito da un altro VSPackage.  
  
-   Per supportare il caricamento su richiesta, un provider del servizio registra i servizi globali con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere [procedura: fornire un servizio](../../extensibility/how-to-provide-a-service.md).  
  
-   Dopo aver ottenuto un servizio, utilizzare [QueryInterface](/cpp/atl/queryinterface) (codice non gestito) o cast (codice gestito) per ottenere l'interfaccia desiderata, ad esempio:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    ```  
  
-   Codice gestito si riferisce a un servizio in base al tipo, mentre il codice non gestito si riferisce a un servizio con il relativo GUID.  
  
-   Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica un pacchetto VSPackage, passa un provider di servizi per il pacchetto VSPackage per consentire l'accesso VSPackage a servizi globali. Ciò è detto "posizione" il pacchetto VSPackage.  
  
-   Pacchetti VSPackage possono essere provider di servizi per gli oggetti creati. Ad esempio, un form potrebbe inviare una richiesta per un servizio di colore per il frame, che potrebbe passare alla richiesta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Gli oggetti gestiti che sono molto annidati, o non individuati, possono chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per accedere direttamente ai servizi globali.   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>Usare GetGlobalService  
  
In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o controllo contenitore che non è stato individuato, altrimenti è stato individuato con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere per la registrazione delle attività all'interno di un controllo. Per ulteriori informazioni su questi e altri scenari, vedere [procedura: risolvere i problemi relativi a servizi](../../extensibility/how-to-troubleshoot-services.md).  
  
È possibile ottenere la maggior parte dei servizi di Visual Studio chiamando il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodo.  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>si basa su un servizio memorizzato nella cache viene individuato provider che viene inizializzata la prima volta che un VSPackage è derivato dal pacchetto. È necessario garantire che questa condizione viene soddisfatta, oppure essere preparata per un servizio null.  
  
Fortunatamente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funziona correttamente la maggior parte dei casi.  
  
-   Se un pacchetto VSPackage fornisce un servizio noto solo a un altro VSPackage, viene individuato il pacchetto VSPackage che richiedono il servizio prima il pacchetto VSPackage che fornisce che il servizio sia caricato.  
  
-   Se una finestra degli strumenti viene creata da un pacchetto VSPackage, il pacchetto VSPackage è posizionato prima che venga creata la finestra degli strumenti.  
  
-   Se un contenitore del controllo è ospitato da una finestra degli strumenti creata da un pacchetto VSPackage, il pacchetto VSPackage è posizionato prima che venga creato il contenitore del controllo.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Per ottenere un servizio dall'interno di un contenitore di controllo o finestra dello strumento  
  
-   Inserire questo codice nel costruttore, finestra degli strumenti o contenitore di controlli:  
  
    ```csharp  
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```  
    ```vb  
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```  
    
    Questo codice ottiene un servizio SVsActivityLog ed esegue il cast a un'interfaccia IVsActivityLog, che consente di scrivere nel log attività. Per un esempio, vedere [procedura: utilizzare il registro attività](../../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco dei servizi disponibili](../../extensibility/internals/list-of-available-services.md)   
 [Utilizzando e servizi](../../extensibility/using-and-providing-services.md)   
 [Cast e conversioni di tipi](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Cast](/cpp/cpp/casting)