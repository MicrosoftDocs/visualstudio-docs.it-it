---
title: 'Procedura: fornire un servizio | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70d16085bc6cbc7f01a991a1eca731b8abed2b0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-a-service"></a>Procedura: fornire un servizio
Un pacchetto VSPackage può fornire servizi che è possibile utilizzare altri pacchetti VSPackage. Per fornire un servizio, un pacchetto VSPackage deve registrare il servizio con Visual Studio e aggiungere il servizio.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Package> classe implementa sia <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> e <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> contiene i metodi di callback che forniscono servizi su richiesta.  
  
 Per ulteriori informazioni sui servizi, vedere [servizio Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Quando un pacchetto VSPackage sta per essere scaricato, Visual Studio attende fino a quando non sono state recapitate tutte le richieste per i servizi che fornisce un pacchetto VSPackage. Non consente nuove richieste per tali servizi. Non è necessario chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo revocare un servizio, quando lo scaricamento.  
  
#### <a name="implementing-a-service"></a>Implementazione di un servizio  
  
1.  Creare un progetto VSIX (**File > Nuovo > progetto > c# > estendibilità > progetto VSIX**).  
  
2.  Aggiungere al progetto un pacchetto VSPackage. Selezionare il nodo del progetto nel **Esplora** e fare clic su **Aggiungi > Nuovo elemento > elementi di Visual c# > estendibilità > pacchetto di Visual Studio**.  
  
3.  Per implementare un servizio, è necessario creare tre tipi:  
  
    -   Un'interfaccia che descrive il servizio. Molte di queste interfacce sono vuoti, che è non disponibile alcun metodo.  
  
    -   Un'interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include i metodi da implementare.  
  
    -   Una classe che implementa il servizio e l'interfaccia del servizio.  
  
     Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe del servizio deve impostare il provider del servizio.  
  
    ```csharp  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### <a name="registering-a-service"></a>La registrazione di un servizio  
  
1.  Per registrare un servizio, aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al pacchetto VSPackage che fornisce il servizio. Ecco un esempio:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Questo attributo registra `SMyService` con Visual Studio.  
  
    > [!NOTE]
    >  Per registrare un servizio che sostituisce un altro servizio con lo stesso nome, utilizzare il <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Si noti che solo un override di un servizio è consentito.  
  
### <a name="adding-a-service"></a>Aggiunta di un servizio  
  
1.  Nell'inizializzatore VSPackage, aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Ecco la modifica da apportare al <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementare il metodo di callback, che deve creare e restituire il servizio oppure null se non può essere creata.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new MyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio è possibile rifiutare una richiesta per fornire un servizio. Esegue l'operazione se un altro VSPackage fornisce già il servizio.  
  
3.  È ora possibile ottenere il servizio e utilizzare i relativi metodi. Nell'esempio seguente viene illustrato l'utilizzo del servizio nell'inizializzatore, ma è possibile ottenere il servizio in qualsiasi punto che si desidera utilizzare il servizio.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.Goodbye();  
  
        base.Initialize();  
    }  
    ```  
  
     Il valore di `helloString` deve essere "Hello".  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md)   
 [Utilizzando e servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)
