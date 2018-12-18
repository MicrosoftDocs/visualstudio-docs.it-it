---
title: "Scrittura di logger compatibili con più processori | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f01842f0b194a2e8ee426944fc361c10d5bfb7ea
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="writing-multi-processor-aware-loggers"></a>Scrittura di logger compatibili con più processori
La possibilità di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di sfruttare più processori può ridurre i tempi di compilazione del progetto, ma aggiunge complessità alla registrazione dell'evento di compilazione. In un ambiente a processore singolo gli eventi, i messaggi, gli avvisi e gli errori arrivano al logger in modo prevedibile e sequenziale. Tuttavia, in un ambiente a più processori gli eventi di diverse origini possono arrivare contemporaneamente o fuori sequenza. A tale scopo, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] offre un logger compatibile con più processori e un nuovo modello di registrazione e consente di creare "logger di inoltro" personalizzati.  
  
## <a name="multi-processor-logging-challenges"></a>Sfide della registrazione con più processori  
 Quando si compilano uno o più progetti in un sistema a più processori o multicore, gli eventi di compilazione di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per tutti i progetti vengono generati contemporaneamente. Al logger può arrivare una grande quantità di messaggi sugli eventi contemporaneamente o fuori sequenza. Poiché un logger di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 non è stato progettato in modo da gestire questa situazione, si può avere un sovraccarico del logger e, di conseguenza, un aumento dei tempi di compilazione, output del logger non corretti o una compilazione non funzionante. Per risolvere questi problemi, il logger, a partire da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, è in grado di elaborare gli eventi fuori sequenza e correlare gli eventi e le relative origini.  
  
 È possibile migliorare ulteriormente l'efficienza della registrazione creando un logger di inoltro personalizzato. Un logger di inoltro personalizzato funziona come un filtro e consente di scegliere, prima della compilazione, solo gli eventi da monitorare. Quando si usa un logger di inoltro personalizzato, si evita che eventi indesiderati sovraccarichino il logger, creando confusione nei log e rallentando i tempi di compilazione.  
  
## <a name="multi-processor-logging-models"></a>Modelli di registrazione con più processori  
 Per affrontare i problemi di compilazione correlati a più processori, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] supporta due modelli di registrazione, centrale e distribuito.  
  
### <a name="central-logging-model"></a>Modello di registrazione centrale  
 Nel modello di registrazione centrale una singola istanza di MSBuild.exe agisce come "nodo centrale" e le istanze figlio del nodo centrale ("nodi secondari") vengono allegate al nodo centrale per agevolare le attività di compilazione.  
  
 ![Modello di logger centrale](../msbuild/media/centralnode.png "CentralNode")  
  
 I logger di vario tipo che vengono allegati al nodo centrale sono noti come "logger centrali". Solo un'istanza di ogni tipo di logger può essere allegata al nodo centrale in un dato momento.  
  
 Durante una compilazione i nodi secondari indirizzano i propri eventi di compilazione al nodo centrale. Il nodo centrale indirizza tutti i propri eventi e quelli dei nodi secondari a uno o più dei logger centrali allegati. I logger quindi creano i file di log in base ai dati in ingresso.  
  
 Benché sia richiesta solo l'implementazione di <xref:Microsoft.Build.Framework.ILogger> da parte del logger centrale, si consiglia di implementare anche <xref:Microsoft.Build.Framework.INodeLogger> in modo che il logger centrale venga inizializzato con il numero dei nodi interessati dalla compilazione. Il seguente overload del metodo <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> richiama quando il motore inizializza il logger.  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Eventuali logger preesistenti basati su <xref:Microsoft.Build.Framework.ILogger>possono fungere da logger centrali ed essere allegati alla compilazione. Tuttavia, i logger centrali scritti senza supporto esplicito per gli scenari di registrazione con più processori e gli eventi in ordine non corretto possono interrompere una compilazione o produrre output non significativo.  
  
### <a name="distributed-logging-model"></a>Modello di registrazione distribuita  
 Nel modello di registrazione centrale una quantità eccessiva di traffico di messaggi in ingresso può sovraccaricare il nodo centrale, ad esempio quando si compilano molti progetti contemporaneamente. Questo può comportare un'eccessiva sollecitazione delle risorse di sistema e un peggioramento delle prestazioni di compilazione. Per attenuare questo problema, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] supporta un modello di registrazione distribuito.  
  
 ![Modello di registrazione distribuita](../msbuild/media/distnode.png "DistNode")  
  
 Il modello di registrazione distribuita estende il modello di registrazione centrale consentendo la creazione di un logger di inoltro.  
  
#### <a name="forwarding-loggers"></a>Logger di inoltro  
 Un logger di inoltro è un logger secondario e leggero con un filtro eventi che viene allegato a un nodo secondario e riceve gli eventi di compilazione in ingresso da quel nodo. Filtra gli eventi in ingresso e inoltra al nodo centrale solo quelli specificati dall'utente. Questo riduce il traffico di messaggi inviato al nodo centrale e migliora complessivamente le prestazioni di compilazione.  
  
 Esistono due modi per usare la registrazione distribuita, come indicato di seguito:  
  
-   Personalizzare il logger di inoltro preimpostato denominato <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.  
  
-   Scrivere il proprio logger di inoltro personalizzato.  
  
 È possibile modificare ConfigurableForwardingLogger in base alle proprie esigenze. A tale scopo, chiamare il logger nella riga di comando usando MSBuild.exe e indicare gli eventi di compilazione che il logger dovrà inoltrare al nodo centrale.  
  
 In alternativa, è possibile creare un logger di inoltro personalizzato. Creando un logger di inoltro personalizzato, è possibile ottimizzare il comportamento del logger. Tuttavia, la creazione di un logger di inoltro personalizzato è più complessa rispetto alla personalizzazione di ConfigurableForwardingLogger. Per altre informazioni, vedere l'articolo relativo alla [creazione dei logger di inoltro](../msbuild/creating-forwarding-loggers.md).  
  
## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Uso di ConfigurableForwardingLogger per la registrazione distribuita semplice  
 Per allegare un oggetto ConfigurableForwardingLogger o un logger di inoltro personalizzato, usare l'opzione `/distributedlogger` (`/dl` per brevità) in una compilazione da riga di comando di MSBuild.exe. Il formato da usare per specificare i nomi dei tipi e delle classi del logger è identico a quello usato per l'opzione `/logger`, ad eccezione del fatto che un logger distribuito ha sempre due classi di registrazione anziché una sola, il logger di inoltro e il logger centrale. Di seguito è riportato un esempio di come allegare un logger di inoltro personalizzato denominato XMLForwardingLogger.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  I due nomi di logger nell'opzione `/dl` devono essere separati da un asterisco (*).  
  
 L'uso di ConfigurableForwardingLogger è simile all'uso di qualsiasi altro logger, come descritto in [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md), ad eccezione del fatto che si allega il logger ConfigurableForwardingLogger anziché il tipico logger [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] e si specificano come parametri gli eventi che ConfigurableForwardingLogger deve passare al nodo centrale.  
  
 Ad esempio, per ricevere una notifica solo all'inizio e alla fine di una compilazione e quando si verifica un errore, è necessario passare `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` e `ERROREVENT` come parametri. Per passare più parametri, separarli con punti e virgola. L'esempio che segue spiega come usare ConfigurableForwardingLogger per inoltrare solo gli eventi `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` e `ERROREVENT`.  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 Di seguito è riportato un elenco dei parametri di ConfigurableForwardingLogger disponibili.  
  
|Parametri di ConfigurableForwardingLogger|  
|---------------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|COMMANDLINE|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di logger di inoltro](../msbuild/creating-forwarding-loggers.md)