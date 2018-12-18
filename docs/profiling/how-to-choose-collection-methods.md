---
title: 'Procedura: Scegliere un metodo di raccolta | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55e801404fbf3356b597471d7c3dda23264eb0c5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-choose-collection-methods"></a>Procedura: Scegliere un metodo di raccolta

Gli strumenti di profilatura di Visual Studio supportano tre metodi di raccolta dei dati relativi alle prestazioni: campionamento, strumentazione e concorrenza. È anche possibile usare il metodo di campionamento o di strumentazione per raccogliere dati di durata e allocazione di memoria .NET.

È possibile usare la proprietà **Metodo** della sessione di prestazioni per specificare il metodo di raccolta più appropriato per un'applicazione. Il metodo di raccolta può essere impostato dalla Creazione guidata sessione di prestazioni, da Esplora prestazioni o dalle pagine delle proprietà di una sessione di prestazioni. Se si usano gli strumenti della riga di comando, vedere [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md) per altre informazioni.

## <a name="performance-wizard"></a>Creazione guidata sessione di prestazioni

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Per selezionare un metodo di raccolta usando la Creazione guidata sessione di prestazioni

- Nella prima pagina della procedura guidata selezionare una delle opzioni seguenti:

|Opzione|Descrizione|
|------------|-----------------|
|**Campionamento CPU**|Consente di raccogliere le statistiche dell'applicazione utili per l'analisi iniziale e per l'analisi dei problemi relativi all'uso della CPU.|
|**Strumentazione**|Consente di raccogliere i dati di intervallo dettagliati utili per l'analisi mirata e per l'analisi dei problemi relativi alle prestazioni di input/output.|
|**Allocazione della memoria .NET**|Consente di raccogliere i dati relativi all'allocazione della memoria [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usando il metodo di profilatura del campionamento.|
|**Concorrenza**|Consente di raccogliere i dati numerici sui conflitti di risorse.|

## <a name="performance-explorer"></a>Esplora prestazioni

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Per selezionare un metodo di raccolta usando Esplora prestazioni

1. Nella barra degli strumenti di **Esplora prestazioni** fare clic sulla freccia accanto all'elenco a discesa **Metodo**.

2. Fare clic sul metodo di raccolta preferito.

## <a name="performance-session-property-pages"></a>Pagine delle proprietà della sessione di prestazioni

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Per selezionare il metodo di campionamento o di strumentazione usando le proprietà della sessione di prestazioni

1. In **Esplora prestazioni** selezionare la sessione di prestazioni.

     L'estensione del nome di un file di sessione di prestazioni è psess.

2. Fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.

3. In **Pagine delle proprietà** fare clic su **Generale**.

4. Fare clic sul metodo di raccolta preferito.

    - Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di campionamento, vedere [Raccolta di statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md).

    - Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di campionamento, vedere [Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Per selezionare la raccolta dei dati di memoria .NET usando le proprietà della sessione di prestazioni

1. In **Esplora prestazioni** selezionare la sessione di prestazioni.

     L'estensione del nome di un file di sessione di prestazioni è psess.

2. Fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.

3. In **Pagine delle proprietà** fare clic su **Generale**.

4. Fare clic su **Campionamento** o **Strumentazione**.

5. Fare clic su **Raccogliere le informazioni sull'allocazione dell'oggetto .NET** per raccogliere le dimensioni e il numero delle allocazioni degli oggetti [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

6. (Facoltativo) Fare clic su **Raccogliere anche le informazioni sulla durata dell'oggetto .NET** per raccogliere dati sulle generazioni di Garbage Collection in cui è stata recuperata la memoria dell'oggetto.

     Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di memoria .NET, vedere [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Per selezionare la raccolta dei dati di concorrenza usando le proprietà della sessione di prestazioni

1. In **Esplora prestazioni**fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.

2. In **Pagine delle proprietà** fare clic su **Generale**.

3. Fare clic su **Concorrenza**.

## <a name="see-also"></a>Vedere anche

[Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)  
[Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)  
[Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)