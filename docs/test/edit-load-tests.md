---
title: Modifica di un test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6e79dd964593e79c69ec6ec8ab44f10ff4c9ca99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="edit-load-tests"></a>Modificare i test di carico

I test di carico eseguono test delle prestazioni Web o unit test per simulare l'accesso di molti utenti a un server nello stesso momento. Un test di carico consente di accedere a dati relativi a stress e prestazioni delle applicazioni. È possibile configurare un test di carico per emulare diverse condizioni di carico, ad esempio carichi utente e tipi di rete.

> [!NOTE]
> Il test di carico è disponibile solo nell'edizione di Visual Studio Enterprise 2017.

Un test di carico è definito da *scenari*, *insiemi di contatori* e *impostazioni di esecuzione del test*. Nella figura seguente vengono illustrate le differenze tra [scenari](../test/edit-load-test-scenarios.md), [insiemi di contatori](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md) e [impostazioni esecuzione test](../test/load-test-run-settings-properties.md):

![Architettura del test di carico](../test/media/load_test_editor.png)

## <a name="edit-load-test-scenario-settings"></a>Modificare le impostazioni dello scenario di test di carico

Si usa uno scenario per definire le modalità di interazione di un gruppo di utenti con un'applicazione server. Uno scenario è composto da un modello di carico, un modello di combinazione di test, una combinazione di browser e una combinazione di reti. Un test di carico può includere più di uno scenario e un singolo scenario può contenere test Web e unit test. Uno scenario raggruppa impostazioni simili e permette quindi di raggruppare ed eseguire test simili.

Per altre informazioni, vedere [Modifica di scenari di test di carico](../test/edit-load-test-scenarios.md) e [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Configurare e gestire gli insiemi di contatori delle prestazioni

I test di carico rendono disponibili insiemi di contatori denominati, organizzati in base alla tecnologia, che risultano utili per analizzare i dati dei contatori delle prestazioni. Gli insiemi di contatori includono Test di carico, IIS, ASP.NET e SQL. Quando si crea un test di carico con la Creazione guidata test di carico, viene configurato un insieme iniziale di contatori importanti e predefiniti per i computer che devono essere specificati per il test di carico. I contatori vengono gestiti nell'Editor test di carico.

Per altre informazioni, vedere [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Configurare e gestire le impostazioni di esecuzione del test di carico

Le impostazioni di esecuzione sono proprietà che determinano la modalità di esecuzione di un test di carico. Sono organizzate in categorie nella finestra Proprietà.

Per altre informazioni, vedere [Configurazione delle impostazioni esecuzione test di carico](../test/configure-load-test-run-settings.md) e [Proprietà delle impostazioni di esecuzione del test di carico](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analisi delle violazioni delle regole di soglia](../test/analyze-threshold-rule-violations-in-load-tests.md)