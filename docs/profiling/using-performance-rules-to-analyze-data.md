---
title: Uso di regole per le prestazioni per analizzare dati | Microsoft Docs
description: Informazioni su come gli avvisi sulle prestazioni di Visual Studio Strumenti di profilatura indicano problemi in un'applicazione profilata che può rallentare l'esecuzione del programma.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 49d0b5f3c2aade0c6cdf4bd83735de2ba1c888ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885963"
---
# <a name="use-performance-rules-to-analyze-data"></a>Usare le regole per le prestazioni per analizzare dati
Gli avvisi di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] segnalano i problemi che possono rallentare l'esecuzione di un'applicazione sottoposta a profilatura. Gli avvisi possono anche indicare che potrebbe essere necessario modificare i metodi di raccolta per raccogliere dati più utili. Gli avvisi di prestazioni sono generati automaticamente in una sessione di profilatura. Gli avvisi vengono visualizzati nella finestra **Elenco errori** quando viene aperto un file di dati di profilatura in Visual Studio. Dalla finestra **Elenco errori** è possibile individuare il codice sorgente del problema e visualizzare informazioni dettagliate sull'errore, ad esempio informazioni su come risolvere il problema. È inoltre possibile disabilitare gli avvisi a cui non si è interessati.

> [!NOTE]
> Gli avvisi di prestazioni del profiler vengono generati dall'analisi dinamica dell'esecuzione del programma e sono indipendenti dagli avvisi di Analisi codice. Analisi codice può inoltre generare avvisi di prestazioni per il codice gestito in base all'analisi statica del codice sorgente. Per altre informazioni, vedere [Analisi della qualità del codice gestito](../code-quality/code-analysis-for-managed-code-overview.md) e [Avvisi di prestazioni](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings).

## <a name="in-this-section"></a>Contenuto della sezione
- [Procedura: Visualizzare gli avvisi di prestazioni](../profiling/how-to-view-performance-warnings.md)

 Fornisce informazioni su come aprire la finestra **Elenco errori** per visualizzare gli avvisi di prestazioni del profiler.

- [Procedura: configurare le regole per le prestazioni](../profiling/how-to-configure-performance-rules.md)

 Fornisce informazioni su come attivare o disattivare i singoli avvisi di prestazioni.

- [Tabella di riferimento delle regole di prestazioni](../profiling/performance-rules-reference.md)

 Fornisce informazioni dettagliate sugli avvisi di prestazioni del profiler.
