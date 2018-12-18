---
title: Configurazione di destinazioni e attività | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f71ef4a5b2471dd8b15ac96b61a67dd159b12833
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="configuring-targets-and-tasks"></a>Configurazione di destinazioni e attività
È possibile configurare le destinazioni e le attività di MSBuild per l'esecuzione out-of-process con MSBuild, in modo che sia possibile specificare come destinazione contesti che differiscono da quello corrente in cui è in esecuzione l'applicazione. Ad esempio, è possibile specificare come destinazione un'applicazione .NET Framework 2.0 a 32 bit mentre nel computer di sviluppo è in esecuzione un sistema operativo .NET Framework 4.5 a 64 bit. Inoltre, è possibile specificare come destinazione computer in cui viene eseguito .NET Framework 4 o versione precedente. La combinazione tra 32 o 64 bit e la versione specifica di .NET Framework viene definita *contesto di destinazione*.  
  
## <a name="installation"></a>Installazione  
 In .NET Framework 4.5 e 4.5.1 il Common Language Runtime (CLR), le destinazioni, le attività e gli strumenti di .NET Framework 4 vengono sostituiti senza relativa ridenominazione. .NET Framework 4.5.1 viene installato come parte di [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
 Per installare MSBuild separatamente da Visual Studio, è possibile scaricare il pacchetto di installazione dalla pagina di [download di MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745). È inoltre necessario installare anche le versioni di .NET Framework che si desidera utilizzare.  
  
## <a name="targets-and-tasks"></a>Destinazioni e attività  
 In MSBuild vengono eseguite alcune attività di compilazione out-of-process per specificare come destinazione un set più ampio di contesti.  Ad esempio, in un'istanza di MSBuild a 32 bit è possibile eseguire un'attività di compilazione in un processo a 64 bit destinato a un computer a 64 bit. Questa funzionalità è controllata dagli argomenti `UsingTask` e dai parametri `Task`. Questi argomenti e parametri vengono impostati dalle destinazioni installate da .NET Framework 4.5 e non è necessaria alcuna modifica per compilare applicazioni per i vari contesti di destinazione.  
  
 Se si desidera creare un contesto di destinazione personalizzato, è necessario impostare questi argomenti e parametri in modo appropriato. Esaminare il file di .NET Framework 4.5 Microsoft.Common.targets e il file Microsoft.Common.Tasks per gli esempi.  Per informazioni su come creare un'attività personalizzata in grado di funzionare in più contesti di destinazione o come modificare le attività esistenti, vedere [Procedura: Configurare destinazioni e attività](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)