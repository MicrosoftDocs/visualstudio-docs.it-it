---
title: Creazione e utilizzo di criteri di controllo dell'analisi del codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b7187ef8d3342ad050c66debf939e9c6a6213957
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Creazione e utilizzo di criteri di archiviazione di analisi codice
Quando si utilizza controllo versione di Team Foundation (TFVC), è possibile creare un criterio di controllo dell'analisi codice per .NET Framework e progetti in codice nativo (C/C++) in un progetto team. È possibile utilizzare i criteri di controllo dell'analisi codice per controllare e migliorare la qualità del codice che viene archiviato nella codebase.  
  
 I criteri vengono soddisfatti quando la compilazione sia aggiornata e l'analisi del codice è stato eseguito nel file di origine più recenti. Come minimo, le regole di analisi di codice che sono abilitate nel progetto di codice devono contenere le stesse regole definite nei criteri di controllo del progetto team. Le regole che sono state specificate come errori nelle impostazioni del progetto Team devono anche essere specificate come errori nel progetto di codice  
  
> [!IMPORTANT]
>  Impossibile applicare criteri di controllo dell'analisi del codice per i progetti di sito web. Che possono essere applicati ad progetti applicazione web.  
  
 Per creare codice criteri di archiviazione dell'analisi utilizzando le impostazioni del progetto Team di [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]. Criteri di archiviazione vengono specificati e applicati per un progetto team, ma esecuzioni dell'analisi del codice sono configurate ed eseguite per singoli progetti di codice nei computer di sviluppo locale. In questa sezione viene descritto come specificare i criteri analisi codice controllo-per un progetto team e come implementare i criteri di analisi codice personalizzati per codice gestito.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Vengono illustrati i passaggi che consentono di impostare e modificare i criteri di analisi codice per un progetto team.  
  
 [Implementazione di criteri di archiviazione personalizzati per codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Vengono illustrati i passaggi utilizzati per creare una regola personalizzata impostata per il criterio di archiviazione di un progetto team e per sincronizzare i progetti di codice del progetto team con i criteri di controllo.  
  
 [Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Vengono illustrati i problemi di compatibilità check-in analisi di codice tra le versioni di [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Viene illustrato come aggiungere parole e i token al dizionario in cui viene fatto riferimento nelle regole di denominazione di analisi codice.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)