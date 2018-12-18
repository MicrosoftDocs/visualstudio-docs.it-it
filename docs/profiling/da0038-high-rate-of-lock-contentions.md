---
title: 'DA0038: Frequenza elevata di conflitti di blocco | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.38
- vs.performance.rules.DA0038
- vs.performance.DA0038
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7ea9e12b32052169d6fb87b927735da071c96fb6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: Frequenza elevata di conflitti di blocco
|||  
|-|-|  
|ID regola|DA0038|  
|Category|Uso di .NET Framework|  
|Metodo di profilatura|Campionamento<br /><br /> Strumentazione<br /><br /> Memoria .NET|  
|Messaggio|È stata rilevata una frequenza elevata di conflitti di blocco .NET. Per determinare la causa, eseguire un profilo della concorrenza.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 25 campioni per attivare questa regola.  
  
## <a name="cause"></a>Causa  
 I dati sulle prestazioni di sistema raccolti con i dati di profilatura indicano che si è verificata una frequenza significativamente elevata di conflitti di blocco durante l'esecuzione dell'applicazione. È consigliabile eseguire di nuovo la profilatura usando il metodo di profilatura della concorrenza per individuare la causa dei conflitti.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I blocchi vengono usati per proteggere sezioni critiche di codice che devono essere eseguite in serie un thread alla volta in un'applicazione multithreading. Common Language Run-time (CLR) di Microsoft .NET offre un set completo di primitive di sincronizzazione e blocco. Ad esempio, il linguaggio C# supporta un'istruzione lock (SyncLock in Visual Basic). Un'applicazione gestita può chiamare i metodi Monitor.Enter e Monitor.Exit nello spazio dei nomi System.Threading per acquisire e rilasciare direttamente un blocco. .NET Framework supporta primitive di sincronizzazione e blocco aggiuntive, includendo classi che supportano mutex, blocchi ReaderWriter e semafori. Per altre informazioni, vedere [Panoramica delle primitive di sincronizzazione](http://go.microsoft.com/fwlink/?LinkId=177867) nella Guida per gli sviluppatori di .NET Framework nel sito Web MSDN. Le classi .NET Framework sono sovrapposte ai servizi di sincronizzazione di livello inferiore incorporati nel sistema operativo Windows. Includono oggetti sezione critica e molte funzioni diverse di segnalazione eventi e attesa. Per altre informazioni, vedere la sezione [Synchronization](http://go.microsoft.com/fwlink/?LinkId=177869) (Sincronizzazione) della documentazione relativa allo sviluppo Win32 e COM in MSDN Library  
  
 I percorsi di memoria condivisi sottostanti le classi .NET Framework e gli oggetti Windows nativi usati per la sincronizzazione e il blocco devono essere modificati tramite operazioni interlock. Le operazioni interlock usano istruzioni specifiche dell'hardware che agiscono sui percorsi di memoria condivisi per modificare il proprio stato tramite operazioni atomiche. La coerenza delle operazioni atomiche è garantita attraverso tutti i processori del computer. Blocchi e WaitHandle sono gli oggetti .NET che usano automaticamente operazioni interlock quando vengono impostati o reimpostati. Nell'applicazione possono essere presenti anche altre strutture dei dati della memoria condivisa che richiedono l'uso di operazioni interlock per essere aggiornate in modo thread-safe. Per altre informazioni, vedere [Operazioni interlock](http://go.microsoft.com/fwlink/?LinkId=177870) nella sezione relativa a .NET Framework della MSDN Library  
  
 Sincronizzazione e blocco sono meccanismi usati per assicurare che tali applicazioni multithreading vengano eseguite correttamente. Ogni thread di un'applicazione multithreading è un'unità di esecuzione indipendente, pianificata indipendentemente dal sistema operativo. Si verifica un conflitto di blocco quando un thread che sta tentando di acquisire un blocco viene ritardato perché il blocco è trattenuto da un altro thread.  
  
 I blocchi sono spesso annidati. L'annidamento si verifica quando un thread che esegue una sezione critica esegue una funzione che a sua volta richiede un altro blocco. Una certa quantità di annidamento del blocco è inevitabile. È possibile che la sezione critica chiami un metodo .NET Framework che si basa su blocchi per garantire che sia thread-safe. Una chiamata da una sezione critica nell'applicazione a un metodo Framework, che a sua volta usa un blocco tramite un handle di blocco diverso, causa l'annidamento dei blocchi. Condizioni del blocco annidate possono causare problemi di prestazioni che sono notoriamente difficili da individuare e correggere.  
  
 Questa regola viene attivata quando misure adottate durante l'esecuzione di una profilatura indicano la presenza di quantità eccessivamente elevata di conflitti di blocco. I conflitti di blocco ritardano l'esecuzione di thread in attesa del blocco. È consigliabile analizzare anche quantità abbastanza limitate di conflitti di blocco in unit test o in test di carico eseguiti su hardware di fascia più bassa.  
  
> [!NOTE]
>  Quando la frequenza dei conflitti di blocco indicata nei dati di profilatura è eccessivamente elevata, viene attivato il messaggio di avviso [DA0039: Frequenza molto elevata di conflitti di blocco](../profiling/da0039-very-high-rate-of-lock-contentions.md) anziché questo messaggio informativo.  
  
## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso  
 Fare doppio clic sul messaggio per passare alla visualizzazione [Contrassegni](../profiling/marks-view.md) dei dati di profilatura.  Individuare la colonna **LocksAndThreads CLR .NET\Conflitti/sec**. Determinare se sono presenti fasi specifiche di esecuzione del programma in cui i conflitti di blocco sono maggiori rispetto ad altre fasi.  
  
 Questa regola viene attivata solo quando non si usa il metodo di profilatura della concorrenza. Il metodo di profilatura della concorrenza è lo strumento migliore da usare per diagnosticare i problemi di prestazioni correlati ai conflitti di blocco nell'applicazione. Per comprendere il comportamento di blocco dell'applicazione, raccogliere dati di profilatura della concorrenza. Questa operazione consente di individuare i blocchi con il maggior numero di conflitti, per quanto tempo viene ritardato il tempo di esecuzione del thread in attesa dei blocchi in conflitto e il codice specifico interessato. I profili di concorrenza raccolgono dati su tutti i conflitti di blocco, incluso il comportamento di blocco di funzionalità di Windows native, classi .NET Framework e qualsiasi altra libreria di terze parti a cui fa riferimento l'applicazione. Per informazioni sulla profilatura della concorrenza dall'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [Collecting Thread and Process Concurrency Data](../profiling/collecting-thread-and-process-concurrency-data.md) (Raccolta di dati di concorrenza di thread e processi). Per collegamenti a informazioni sulla profilatura della concorrenza dalla riga di comando, vedere la sezione **Using the Concurrency Method to Collect Resource Contention and Thread Activity Data** (Uso del metodo di concorrenza per raccogliere i dati su attività dei thread e dei conflitti delle risorse) di [Using Profiling Methods From the Command Line](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md) (Uso di metodi di profilatura dalla riga di comando).