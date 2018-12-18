---
title: "Procedura: configurare l'analisi codice per un'applicazione Web ASP.NET in Visual Studio"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 4d950846811cf1792bf2ee302d37ebd686107fe6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Procedura: configurare l'analisi del codice per un'applicazione Web ASP.NET

In Visual Studio, è possibile selezionare da un elenco di analisi del codice *set di regole* da applicare al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione Web. Il set di regole predefinito è regole minime consigliate di Microsoft. È possibile selezionare un altro set di regole da applicare al sito Web.

1. Selezionare il sito Web in **Esplora**.

2. Nel **Analizza** menu, fare clic su **Configura analisi codice per il sito Web**.

3. Se è stata selezionata la soluzione e la soluzione contiene più di un progetto, selezionare il sistema operativo di destinazione e di configurazione compilazione dal **configurazione** e **piattaforma** Elenca.

4. Per ogni progetto nella soluzione, scegliere il **del Set di regole** colonna e quindi scegliere il nome della regola impostata per l'esecuzione.

5. Per impostazione predefinita, l'analisi del codice viene eseguito in tutti i progetti nella soluzione. Per disabilitare o abilitare l'analisi del codice per un particolare progetto, seguire questi passaggi:

    1. Fare doppio clic sul nome del progetto e quindi fare clic su proprietà.

    2. Selezionare o deselezionare il **Attiva analisi codice** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice selezionando **Esegui analisi del codice sul sito Web** dal **Analizza** menu.

6. Nel **eseguire il set di regole** elenco a discesa, attenersi alla procedura seguente:

    - Selezionare il set di regole che si desidera utilizzare.

    - Selezionare  **\<Sfoglia >** per specificare set di una regola personalizzata esistente non è presente nell'elenco.

    - Definire un [set di regole personalizzate](../code-quality/how-to-create-a-custom-rule-set.md).