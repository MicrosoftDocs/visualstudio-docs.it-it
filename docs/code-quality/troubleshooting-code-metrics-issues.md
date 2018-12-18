---
title: Risoluzione dei problemi relativi alla metrica codice
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8c5dfd9c388e8c2ab4ce83ca0c952851616835c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="troubleshooting-code-metrics-issues"></a>Risoluzione dei problemi relativi alla metrica codice
Quando si esegue la raccolta della metrica di codice, è possibile che si verifichino alcuni dei problemi seguenti:

-   [Modifiche nei calcoli di complessità del codice di Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Modifiche nei calcoli di complessità del codice di Visual Studio 2010
 È possibile che, per la stessa funzione, la metrica di complessità del codice calcolata in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] sia diversa dalla metrica calcolata da versioni precedenti di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] nelle situazioni seguenti:

-   La funzione contiene uno o più blocchi catch. Nelle versioni precedenti di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] i blocchi catch non erano inclusi nel calcolo. In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] la complessità di ogni blocco catch è stata aggiunta alla complessità della funzione.

-   La funzione contiene un'istruzione switch (Select Case in VB). Il compilatore distingue [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] dalle versioni precedenti è può generare codice MSIL diverso per alcune istruzioni switch che contengono casi di fallthrough.

## <a name="see-also"></a>Vedere anche
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)