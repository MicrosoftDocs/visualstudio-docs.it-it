---
title: Cenni preliminari sull'analisi del codice per C/C++
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: f7b0e29f6a9a502054b59fc7313c3eff0565f938
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919891"
---
# <a name="code-analysis-for-cc-overview"></a>Cenni preliminari sull'analisi del codice per C/C++

Lo strumento diC++ analisi del codice c/codice fornisce informazioni sui possibili difetti nelC++ codice sorgente c/. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, l'annullamento dell'inizializzazione della memoria, le dereferenziazioni al puntatore null e le perdite di memoria e risorse. Lo strumento può inoltre eseguire controlli sulle [ C++ linee guida di base](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integrazione con IDE (Integrated Development Environment)

Lo strumento di analisi del codice è completamente integrato nell'IDE di Visual Studio.

Durante il processo di compilazione, tutti gli avvisi generati a causa del codice sorgente vengono visualizzati nell'Elenco errori. È possibile passare al codice sorgente che ha causato l'avviso e visualizzare informazioni aggiuntive sulla causa e le possibili soluzioni del problema.

## <a name="command-line-support"></a>Supporto della riga di comando

È anche possibile usare lo strumento di analisi dalla riga di comando, come illustrato nell'esempio seguente:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 versione 15,7 e successive** È possibile eseguire lo strumento dalla riga di comando con qualsiasi sistema di compilazione incluso CMake.

## <a name="pragma-support"></a>supporto #pragma

È possibile utilizzare la `#pragma` direttiva per considerare gli avvisi come errori, abilitare o disabilitare gli avvisi ed eliminare gli avvisi per le singole righe di codice. Per altre informazioni, vedere [Direttive pragma e parola chiave __Pragma](https://docs.microsoft.com/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Supporto delle annotazioni

Le annotazioni rendono più precisa l'analisi del codice, in quanto offrono informazioni aggiuntive sulle pre- e post-condizioni in parametri di funzione e tipi restituiti. Per ulteriori informazioni, vedere [utilizzo delle annotazioni SAL per ridurreC++ i difetti del codice C/](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Eseguire lo strumento di analisi come parte dei criteri di archiviazione

È possibile che tutte le archiviazioni del codice sorgente debbano soddisfare determinati criteri, in particolare, assicurarsi che l'analisi sia stata eseguita come parte del processo di compilazione locale più recente. Per ulteriori informazioni sull'abilitazione di criteri di archiviazione dell'analisi del codice, vedere [creazione e utilizzo di criteri di archiviazione dell'analisi del codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integrazione Team Build

È possibile usare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi del codice come parte del processo di compilazione di [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Vedere anche

- [Avvio rapido: Analisi del codice per C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Procedura dettagliata: Analizza C/C++ codice per i difetti](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Avvisi dell'analisi codice per C/C++](code-analysis-for-c-cpp-warnings.md)
- [Usare gli strumenti di verifica delle Linee guida di base di C++](using-the-cpp-core-guidelines-checkers.md)
- [C++Riferimento di controllo delle linee guida di base](code-analysis-for-cpp-corecheck.md)
- [Usare set di regole per specificare le regole C++ da eseguire](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizzare la qualità del driver usando gli strumenti di analisi del codice](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Avvisi di analisi del codice per i driver](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
