---
title: Sviluppare per .NET Framework in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e4b68e5d7b7e63e76a2291eba6d81eb581756845
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="visual-studio-multi-targeting-overview"></a>Panoramica del multitargeting di Visual Studio

In Visual Studio è possibile specificare la versione o il profilo di .NET Framework per cui si vuole sviluppare il progetto. Per un'applicazione da eseguire in un altro computer, la versione di .NET Framework per cui viene sviluppata l'applicazione deve essere compatibile con quella installata nel computer.

È anche possibile creare una soluzione contenente progetti destinati a versioni diverse di .NET Framework. Sviluppare per .NET Framework consente di garantire che l'applicazione usi solo le funzionalità disponibili nella versione specificata di .NET Framework.

> [!TIP]
> È anche possibile definire la destinazione delle applicazioni per piattaforme diverse. Per altre informazioni, vedere [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funzionalità per la definizione di .NET Framework come destinazione

La definizione della destinazione del framework include le seguenti funzionalità:

- Quando si apre un progetto destinato a una versione precedente di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], con Visual Studio è possibile aggiornare automaticamente la versione di destinazione o lasciarla invariata.

- Quando si crea un progetto, è possibile specificare la versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] che si vuole usare come destinazione.

- È possibile modificare la versione del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a cui è destinato un progetto esistente.

- È possibile definire la destinazione di una versione diversa del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in ognuno dei numerosi progetti nella stessa soluzione.

- Quando si modifica la versione del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a cui è destinato un progetto, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] effettua tutte le modifiche necessarie ai riferimenti e ai file di configurazione.

Quando si lavora su un progetto destinato a una versione precedente del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio modifica in modo dinamico l'ambiente di sviluppo, come indicato di seguito:

- Vengono filtrati gli elementi delle finestre di dialogo **Nuovo progetto**, **Aggiungi nuovo elemento**, **Aggiungi nuovo riferimento** **Aggiungi riferimento al servizio** per omettere scelte che non sono disponibili nella versione di destinazione.

- Vengono filtrati i controlli personalizzati nella **Casella degli strumenti** per rimuovere quelli che non sono disponibili nella versione di destinazione e per visualizzare solo i controlli più aggiornati quando sono disponibili più controlli.

- Vengono applicati i filtri IntelliSense per omettere funzionalità del linguaggio che non sono disponibili nella versione di destinazione.

- Vengono filtrate le proprietà nella finestra **Proprietà** per omettere quelle che non sono disponibili nella versione di destinazione.

- Vengono filtrate le opzioni di menu per omettere opzioni che non sono disponibili nella versione di destinazione.

- Per le compilazioni, vengono usate la versione e le opzioni del compilatore appropriate per la versione di destinazione.

> [!NOTE]
> La definizione della destinazione del framework non garantisce che l'applicazione verrà eseguita correttamente. È necessario testare l'applicazione per assicurarsi che venga eseguita la versione di destinazione. Non è possibile usare come destinazione versioni di framework precedenti a .NET Framework 2.0.

## <a name="selecting-a-target-framework-version"></a>Selezione di una versione di destinazione di .NET Framework

Quando si crea un progetto, selezionare la versione [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] di destinazione nella finestra di dialogo **Nuovo progetto**. L'elenco dei modelli di progetto disponibili viene filtrato in base alla selezione. In un progetto esistente, è possibile modificare la versione [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] di destinazione nella finestra di dialogo delle proprietà del progetto. Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolving-system-and-user-assembly-references"></a>Risoluzione dei riferimenti ad assembly di sistema e utente

Per impostare come destinazione una versione di .NET Framework, è necessario prima installare i riferimenti dell'assembly appropriato. È possibile scaricare Developer Pack per versioni diverse di .NET Framework dalla pagina [.NET downloads](https://www.microsoft.com/net/download/windows) (Download di .NET).

La finestra di dialogo **Aggiungi riferimento** disabilita gli assembly di sistema non pertinenti alla versione di destinazione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in modo che non possano essere aggiunti a un progetto inavvertitamente. (Gli assembly di sistema sono file con estensione dll inclusi in una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].) I riferimenti che appartengono a una versione del framework successiva alla versione di destinazione non verranno risolti e i controlli che dipendono da un riferimento di questo tipo non possono essere aggiunti. Se si vuole abilitare questo riferimento, reimpostare la destinazione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] del progetto su una in cui sia incluso il riferimento.  Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Per altre informazioni sui riferimenti ad assembly, vedere [Risoluzione di assembly in fase di progettazione](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>Attivazione di LINQ

Quando si definisce la destinazione di .NET Framework 3.5 o versioni successive, vengono aggiunti automaticamente un riferimento a System.Core e un'importazione a livello di progetto per System.Linq (solo in Visual Basic). Per usare le funzionalità LINQ, è necessario attivare anche Option Infer (solo in Visual Basic). Se si passa a una versione precedente di .NET Framework, il riferimento e l'importazione vengono rimossi automaticamente. Per altre informazioni, vedere [Uso di LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Vedere anche

[Multitargeting (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)  
[Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)  
[Platform compatibility and system requirements](http://www.microsoft.com/visualstudio/eng/products/compatibility) (Requisiti di sistema e compatibilità delle piattaforme)
