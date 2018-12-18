---
title: "Compatibilità tra versioni per i criteri di controllo dell'analisi del codice | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 323024cdb420d48c40b7a676bc4e698af7622b67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Criteri di archiviazione relativi alla compatibilità delle versioni per l'analisi del codice
Se è necessario valutare e creare check-in Criteri di analisi codice utilizzano versioni diverse di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], è necessario conoscere le differenze nelle modalità [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] e [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] valutare i criteri di controllo.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilità tra versioni per la valutazione di criteri di archiviazione  
  
-   Quando vengono valutati i criteri di controllo dell'analisi del codice [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], tutte le regole esistenti in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ma non esistono nel [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vengono ignorati.  
  
-   Quando vengono valutati i criteri di controllo dell'analisi del codice [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], tutte le regole che sono esclusive di [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] vengono ignorati.  
  
-   Se i criteri di controllo dell'analisi del codice specificano gli assembly di regole, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] Ignora tutte le regole specificate dagli assembly che non riconosce.  
  
-   Se i criteri di controllo dell'analisi del codice specificano gli assembly di regole che [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] non viene riconosciuto, viene visualizzato un messaggio.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilità tra versioni per la creazione di criteri di archiviazione  
  
-   Se è stato creato un criterio di controllo dell'analisi codice utilizzando il [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] versione di [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], non è possibile utilizzare il [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] versione [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] per modificarlo. E inoltre [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] non è possibile valutare i criteri.  
  
-   Se è stato creato un criterio di controllo dell'analisi codice utilizzando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], è possibile utilizzare [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] per modificarlo, quindi i criteri possa anche essere valutato [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Dopo aver modificato i criteri tramite [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], non è più, è possibile modificare il criterio utilizzando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] può valutare i criteri senza problemi con i nomi sicuri non corrispondenti.  
  
-   Per creare un criterio di controllo dell'analisi codice con impostazioni delle regole valide per entrambi [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] e [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], è necessario creare i criteri in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], apportare tutte le modifiche necessarie e salvare il criterio. Se le modifiche alle regole sono presenti solo in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], modificare e salvare i criteri in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
     Dopo aver salvato il criterio in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], non è possibile modificare le impostazioni per le regole che esistono in [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] solo.