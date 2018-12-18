---
title: Registrazione in un ambiente a più processori |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dedf90c51ec2cd4f1864d5573925ed17a0d69b2a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="logging-in-a-multi-processor-environment"></a>Registrazione in un ambiente a più processori
La possibilità di MSBuild di utilizzare più processori può ridurre notevolmente i tempi di compilazione del progetto, ma aggiunge complessità alla registrazione. In un ambiente a processore singolo, il logger può gestire eventi, messaggi, avvisi ed errori in ingresso in modo prevedibile e sequenziale. Tuttavia, in un ambiente a più processori gli eventi di diverse origini possono arrivare contemporaneamente o fuori sequenza. MSBuild offre un nuovo logger compatibile con più processori e consente la creazione di "logger di inoltro" personalizzati.  
  
## <a name="logging-multiple-processor-builds"></a>Registrazione di build a più processori  
 Quando si compilano uno o più progetti in un sistema a più processori o multicore, gli eventi di compilazione di MSBuild per tutti i progetti vengono generati contemporaneamente. Al logger può arrivare una grande quantità di dati degli eventi contemporaneamente o fuori sequenza. Questo può comportare un sovraccarico del logger e, di conseguenza, un aumento dei tempi di compilazione, output del logger non corretti o una compilazione non funzionante. Per risolvere questi problemi, il logger di MSBuild è in grado di elaborare gli eventi fuori sequenza e correlare gli eventi e le relative origini.  
  
 È possibile migliorare ulteriormente l'efficienza della registrazione creando un logger di inoltro personalizzato. Un logger di inoltro personalizzato funziona come un filtro e consente di scegliere, prima della compilazione, gli eventi da monitorare. Quando si usa un logger di inoltro personalizzato, si evita che eventi indesiderati possano sovraccaricare il logger, creare confusione nei log e rallentare i tempi di compilazione.  
  
### <a name="central-logging-model"></a>Modello di registrazione centrale  
 Per le build a più processori MSBuild usa un "modello di registrazione centrale". Nel modello di registrazione centrale un'istanza di MSBuild.exe agisce come processo di compilazione primario o "nodo centrale". Le istanze secondarie di MSBuild.exe, i "nodi secondari", vengono allegate al nodo centrale. Tutti i logger basati su ILogger allegati al nodo centrale sono noti come "logger centrali" e i logger allegati ai nodi secondari sono noti come "logger secondari".  
  
 Durante una compilazione ogni logger secondario indirizza il proprio traffico di eventi ai logger centrali. Poiché gli eventi hanno origine in più nodi secondari, i dati arrivano al nodo centrale contemporaneamente ma con interfoliazione. Per risolvere i riferimenti da evento a progetto e da evento a destinazione, gli argomenti dell'evento includono informazioni aggiuntive sul contesto dell'evento di compilazione.  
  
 Benché sia richiesta solo l'implementazione di <xref:Microsoft.Build.Framework.ILogger> da parte del logger centrale, si consiglia di implementare anche <xref:Microsoft.Build.Framework.INodeLogger> se si vuole che il logger centrale venga inizializzato con il numero dei nodi interessati dalla compilazione. Il seguente overload del metodo <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> viene chiamato quando il motore inizializza il logger:  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Modello di registrazione distribuita  
 Nel modello di registrazione centrale, una quantità eccessiva di traffico di messaggi in ingresso, ad esempio quando si compilano molti progetti in una sola volta, può sovraccaricare il nodo centrale e causare eccessive sollecitazioni del sistema e una riduzione delle prestazioni di compilazione.  
  
 Per ridurre questo problema, MSBuild offre anche un "modello di registrazione distribuita" che estende il modello di registrazione centrale consentendo la creazione di logger di inoltro. Un logger di inoltro è allegato a un nodo secondario e riceve eventi di compilazione in ingresso da tale nodo. Il logger di inoltro è analogo a un logger normale ad eccezione del fatto che è in grado di filtrare gli eventi e quindi inoltra solo quelli selezionati al nodo centrale. In questo modo si riduce il traffico dei messaggi in corrispondenza del nodo centrale e di conseguenza migliorano le prestazioni.  
  
 È possibile creare un logger di inoltro implementando l'interfaccia <xref:Microsoft.Build.Framework.IForwardingLogger>, che deriva da <xref:Microsoft.Build.Framework.ILogger>. L'interfaccia viene definita come segue:  
  
```csharp
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Per inoltrare gli eventi in un logger di inoltro, chiamare il metodo <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> dell'interfaccia <xref:Microsoft.Build.Framework.IEventRedirector>. Passare il valore <xref:Microsoft.Build.Framework.BuildEventArgs> appropriato, o un derivato, come parametro.  
  
 Per altre informazioni, vedere l'articolo relativo alla [creazione dei logger di inoltro](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Allegare un logger distribuito  
 Per allegare un logger distribuito a una build da riga di comando, usare l'opzione `/distributedlogger` (o la forma breve `/dl`). I formati da usare per specificare i nomi dei tipi e delle classi del logger sono identici a quelli usati per l'opzione `/logger`, ad eccezione del fatto che un logger distribuito è costituito da due classi di registrazione: un logger di inoltro e un logger centrale. L'esempio seguente illustra come allegare un logger distribuito:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Un asterisco (*) separa i due nomi di logger nell'opzione `/dl`.  
  
## <a name="see-also"></a>Vedere anche  
 [Logger di compilazione](../msbuild/build-loggers.md)   
 [Creazione di logger di inoltro](../msbuild/creating-forwarding-loggers.md)