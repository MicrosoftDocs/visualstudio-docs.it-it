---
title: Domande frequenti su Esplora test | Microsoft Docs
ms.date: 1/15/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: ghogen
ms.openlocfilehash: 63c1b25ad597dc3d56dfc398ec9c6c463aec200d
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Domande frequenti su Esplora test di Visual Studio

## <a name="test-discovery"></a>Individuazione dei test

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-are-dynamically-defined-for-example-theories-custom-adapters-custom-traits-ifdefs-etc-how-can-i-discover-these-tests"></a>1. Esplora Test non individua i test definiti in modo dinamico. Ad esempio, teorie, adattatori personalizzati, tratti personalizzati, #ifdefs e così via. Come è possibile individuare questi test?

  Compilare il progetto e verificare che l'individuazione basata su assembly sia attivata in **Strumenti > Opzioni > Test**.

  L'[individuazione dei test in tempo reale](https://go.microsoft.com/fwlink/?linkid=862824) è l'individuazione dei test in base all'origine. Questa funzionalità non consente di individuare test che usano teorie, adattatori personalizzati, tratti personalizzati, istruzioni `#ifdef` e così via, perché sono definiti in fase di esecuzione. Per l'individuazione accurata di questi test è necessaria una compilazione. Nelle versioni di anteprima 15.6, l'individuazione basata su assembly (agente di individuazione tradizionale) viene eseguita solo dopo le compilazioni. Questa impostazione significa che l'individuazione dei test in tempo reale consente di individuare il maggior numero possibile di test durante la modifica e che l'individuazione basata su assembly consente la visualizzazione dei test definiti in modo dinamico dopo una compilazione. L'individuazione dei test in tempo reale migliora la velocità di risposta, ma consente comunque di ottenere risultati accurati e completi dopo una compilazione.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. Cosa significa il simbolo '+' (più) visualizzato nella prima riga di Esplora test?

  Il simbolo '+' (più) indica che possono essere individuati ulteriori test dopo una compilazione a condizione che sia attivata l'individuazione basata su assembly. Viene visualizzato se nel progetto vengono rilevati test definiti in modo dinamico.

  ![Riga di riepilogo con segno più](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. L'individuazione basata su assembly non funziona più per un progetto. Come è possibile riattivarla?

  Passare a **Strumenti > Opzioni > Test** e selezionare la casella di controllo **Individua anche i test di assembly compilati dopo le compilazioni**.

  ![Opzione basata su assembly](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. I test vengono ora visualizzati in Esplora test durante la digitazione senza dover compilare il progetto. Cosa è cambiato?

  Questa funzionalità è denominata [individuazione dei test in tempo reale](https://go.microsoft.com/fwlink/?linkid=862824). Usa un analizzatore Roslyn per individuare i test e popolare Esplora test in tempo reale, senza che sia necessario compilare il progetto. Per altre informazioni sul comportamento di individuazione dei test per i test definiti in modo dinamico, ad esempio teorie o tratti personalizzati, vedere la domanda 1.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Quali linguaggi e framework di test possono usare l'individuazione dei test in tempo reale?

  L'[individuazione dei test in tempo reale](https://go.microsoft.com/fwlink/?linkid=862824) funziona solo per i linguaggi gestiti (C# e Visual Basic), perché viene compilata con il compilatore Roslyn. Per il momento, l'individuazione dei test in tempo reale funziona solo per i framework xUnit, NUnit e MSTest.

### <a name="6-how-can-i-turn-on-logs-for-the-test-explorer"></a>6. Come è possibile attivare i log per Esplora test?

  Passare a **Strumenti > Opzioni > Test** e individuare la sezione Registrazione.

### <a name="7-why-are-my-tests-in-uwp-projects-not-discovered-until-i-deploy-my-app"></a>7. Perché i test nei progetti UWP vengono individuati solo dopo la distribuzione dell'app?

  I test UWP usano un runtime diverso come destinazione quando l'app viene distribuita. Questo significa che per individuare i test in modo accurato per i progetti UWP non è sufficiente compilare il progetto, ma è anche necessario distribuirlo.

### <a name="8-how-does-sorting-test-results-work-in-the-hierarchy-view"></a>8. Come funziona l'ordinamento dei risultati di test nella visualizzazione gerarchia?

  Nella visualizzazione gerarchia i test sono disposti in ordine alfabetico anziché in base al risultato. Le altre impostazioni di raggruppamento solitamente dispongono i risultati dei test in base al risultato e poi in ordine alfabetico. Di seguito sono indicate le varie opzioni di raggruppamento per un confronto. È possibile inviare commenti e suggerimenti sulla progettazione [in questo problema GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

## <a name="features"></a>Funzionalità

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Come è possibile attivare i flag di funzionalità per provare le nuove funzionalità di test?

I flag di funzionalità vengono usati per fornire parti del prodotto sperimentali o non completate agli utenti ansiosi di fornire commenti e suggerimenti prima del rilascio ufficiale delle funzionalità. Questi flag potrebbero destabilizzare l'esperienza dell'IDE. Usarli solo in ambienti di sviluppo protetti, come le macchine virtuali. I flag di funzionalità sono sempre impostazioni usate a proprio rischio. È possibile attivare le funzionalità sperimentali con l'[estensione per i flag di funzionalità](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) o tramite il prompt dei comandi per sviluppatori.

![Estensione per i flag di funzionalità](media/testex-featureflag.png)

Per attivare un flag di funzionalità tramite il prompt dei comandi per sviluppatori di Visual Studio, usare il comando seguente. Modificare il percorso in cui è installato Visual Studio nel computer in uso e modificare la chiave del Registro di sistema per il flag di funzionalità desiderato.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> È possibile disattivare il flag con lo stesso comando, usando il valore 0 anziché 1 dopo dword.
  
## <a name="see-also"></a>Vedere anche

<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>  
[Creazione ed esecuzione di unit test per il codice esistente](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
[Eseguire unit test del codice](unit-test-your-code.md)
[Domande frequenti su Live Unit Testing](live-unit-testing-faq.md)
