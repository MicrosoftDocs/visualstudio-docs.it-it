---
title: Codice misto & informazioni mancanti nella finestra stack di chiamate
description: Nei programmi in modalità mista (nativo e gestito) il debugger non è sempre in grado di visualizzare lo stack di chiamate completo. Informazioni sulle possibili discrepanze quando il codice nativo chiama codice gestito.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 793d60c9bc550b0f29ac48e50a95dab601750ad4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885105"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Codice misto e informazioni mancanti nella finestra Stack di chiamate
A causa delle differenze tra gli stack di chiamate per il codice gestito e il codice nativo, il debugger non è sempre in grado di visualizzare lo stack di chiamate completo in caso di tipi di codice misti. Quando codice nativo chiama codice gestito, nella finestra **Stack di chiamate** potrebbero osservarsi le seguenti discrepanze:

- Il frame nativo situato immediatamente al di sopra del codice gestito potrebbe non essere visualizzato nella finestra **Stack di chiamate**. Per altre informazioni, vedere [procedura: uscire da codice gestito quando nella finestra stack di chiamate mancano frame nativi](how-to-use-the-call-stack-window.md).

- Per le applicazioni in modalità mista avviate all'esterno del debugger, nella finestra **Stack di chiamate** potrebbe essere visualizzato solo il codice gestito ma nessuno dei frame nativi.

  Entrambi i casi sono piuttosto rari. Nella maggior parte delle chiamate native a codice gestito gli stack di chiamate verranno visualizzati in modo corretto.

## <a name="see-also"></a>Vedi anche
- [Procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)