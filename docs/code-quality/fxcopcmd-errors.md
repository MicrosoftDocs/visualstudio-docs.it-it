---
title: Errori di FxCopCmd | Documenti Microsoft
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: "12"
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 48b082f5b00f260d2f8e2519a4551fab23dc1011
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="fxcopcmd-errors"></a>errori di FxCopCmd
FxCopCmd non considera tutti gli errori irreversibili. Se FxCopCmd dispone di informazioni sufficienti per eseguire un'analisi parziale, esegue l'analisi e segnala gli errori che si sono verificati. Il codice di errore è un intero a 32 bit, contiene una combinazione bit per bit di valori numerici che corrispondono agli errori.  
  
 Nella tabella seguente vengono descritti i codici di errore restituiti da FxCopCmd:  
  
|Error|Valore numerico|  
|-----------|-------------------|  
|Senza errori|0x0|  
|Errore di analisi|0x1|  
|Eccezioni alle regole|0x2|  
|Errore di caricamento progetto|0x4|  
|Errore di caricamento assembly|0x8|  
|Errore durante il caricamento della libreria regola|0x10|  
|Errore durante il caricamento report importazione|0x20|  
|Errore di output|0x40|  
|Errore di opzione della riga di comando|0x80|  
|Errore di inizializzazione|0x100|  
|Errore di riferimento ad assembly|0x200|  
|Messaggio di interruzione compilazione|0x400|  
|Errore sconosciuto|0x1000000|  
  
 Viene restituito l'errore di analisi per gli errori irreversibili. Indica che l'analisi non riuscita. Quando applicabile, il codice di errore contiene anche la causa dell'errore irreversibile. Le condizioni seguenti generano errori irreversibili:  
  
-   L'analisi non è riuscito causate da input insufficiente.  
  
-   L'analisi ha generato un'eccezione non gestita da FxCopCmd.  
  
-   Il file di progetto specificato non è stato trovato o è danneggiato.  
  
-   Non è stata specificata l'opzione di output o il file non è stato scritto.  
  
    > [!NOTE]
    >  Il codice restituito di FxCopCmd "Errore di riferimento ad Assembly" 0x200 da se stessa è un avviso anziché un errore. Il codice restituito indica che sono stati rilevati riferimenti indiretti mancanti, ma che FxCopCmd è stato in grado di gestirle. Tratta di un avviso che è possibile che alcuni risultati di analisi potrebbero essere stata compromessa. Prendere in considerazione "Assembly fa riferimento all'errore" il codice restituito come un errore quando viene combinato con qualsiasi altro codice restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)