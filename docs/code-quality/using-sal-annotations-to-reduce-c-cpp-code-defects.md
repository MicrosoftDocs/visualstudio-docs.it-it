---
title: Uso delle annotazioni SAL per ridurre gli errori del codice C/C++
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- annotations
- SAL annotations
- code analysis, annotation
ms.assetid: a16e47d0-6f3e-4ed6-8883-459b2874e9a4
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 506e8516c7a7bbc0ccc610b843763017ae90f547
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807069"
---
# <a name="using-sal-annotations-to-reduce-cc-code-defects"></a>Uso delle annotazioni SAL per ridurre gli errori del codice C/C++
SAL è il linguaggio di annotazione del codice sorgente Microsoft. Usando le annotazioni del codice sorgente, è possibile eseguire l'intento dietro il codice in modo esplicito. Queste annotazioni consentono inoltre agli strumenti di analisi statica automatizzati di analizzare il codice in modo più accurato, con un minor numero di falsi positivi e falsi negativi.

Gli articoli di questa sezione della documentazione illustrano gli aspetti di SAL, forniscono informazioni di riferimento sulla sintassi SAL e forniscono esempi di uso.

- [Informazioni su SAL](../code-quality/understanding-sal.md)

     Vengono fornite informazioni ed esempi che illustrano le annotazioni di base di SAL.

- [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)

     Elenca le annotazioni SAL per le funzioni e i parametri della funzione.

- [Annotazione del comportamento delle funzioni](../code-quality/annotating-function-behavior.md)

     Elenca le annotazioni SAL per le funzioni e il comportamento della funzione.

- [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)

     Elenca le annotazioni SAL per le strutture e le classi.

- [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)

     Viene illustrato come usare le annotazioni SAL con i meccanismi di blocco.

- [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)

     Elenca le annotazioni SAL che specificano la condizione o l'ambito (posizionamento) di altre annotazioni SAL.

- [Funzioni intrinseche](../code-quality/intrinsic-functions.md)

     Elenca le annotazioni SAL intrinseche.

- [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)

     Fornisce esempi che illustrano come usare le annotazioni SAL. Vengono inoltre illustrati i problemi comuni.

## <a name="related-resources"></a>Risorse correlate
[Blog del team di analisi del codice](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>Vedere anche
[Annotazioni SAL 2,0 per driver di Windows](/windows-hardware/drivers/devtest/sal-2-annotations-for-windows-drivers)
