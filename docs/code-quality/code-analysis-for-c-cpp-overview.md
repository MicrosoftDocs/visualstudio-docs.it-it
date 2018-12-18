---
title: Cenni preliminari sull'analisi del codice per C/C++
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 4068b4956d0337a3b3c46693b54b0df165439a7f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="code-analysis-for-cc-overview"></a>Analisi del codice per C/C++ overview

Lo strumento di analisi del codice C/C++ fornisce agli sviluppatori informazioni sui possibili errori nel codice sorgente C/C++. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, la memoria non inizializzata, dereferenziazioni al puntatore null e perdite di memoria e risorse.

## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (Integrated Development Environment)
 Per rendere più naturale per gli sviluppatori di utilizzare lo strumento di analisi, è completamente integrato all'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Durante il processo di compilazione, tutti gli avvisi generati per il codice sorgente vengono visualizzati nell'elenco errori. È possibile passare al codice sorgente che ha provocato l'avviso e, è possibile visualizzare informazioni aggiuntive sulla causa e possibili soluzioni del problema.

## <a name="pragma-support"></a>supporto #pragma
 Gli sviluppatori possono utilizzare il `#pragma` direttiva per considerarli come errori; abilitare o disabilitare gli avvisi e l'esclusione di avvisi per singole righe di codice. Per ulteriori informazioni, vedere [procedura: impostare le proprietà di analisi codice per progetti C/C++ ](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Supporto delle annotazioni
 Annotazioni migliorano l'accuratezza dell'analisi del codice. Annotazioni informazioni aggiuntive sul pre e post-condizioni nei parametri di funzione e tipi restituiscono. Per altre informazioni, vedere [procedura: specificare informazioni aggiuntive di codice utilizzando analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Eseguire lo strumento di analisi come parte di criteri di archiviazione
 Si potrebbe voler richiedono che tutte le origine codice archiviazioni soddisfino determinati criteri. In particolare, si desidera assicurarsi che l'analisi è stata eseguita come un passaggio di compilazione locale più recente. Per ulteriori informazioni sull'abilitazione di criteri di controllo dell'analisi codice, vedere [creazione e utilizzo Check-In Criteri di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integrazione di Team Build
 È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi codice come il [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] processo di compilazione. Per altre informazioni, vedere [Compilazione e versione](/vsts/build-release/index).

## <a name="command-line-support"></a>Supporto della riga di comando
 Oltre all'integrazione completa nell'ambiente di sviluppo, gli sviluppatori possono utilizzare lo strumento di analisi dalla riga di comando, come illustrato nell'esempio seguente:

 `C:\>cl /analyze Sample.cpp`

## <a name="see-also"></a>Vedere anche

[Analisi della qualità del Driver tramite gli strumenti di analisi codice](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
[l'analisi del codice per gli avvisi di driver](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)