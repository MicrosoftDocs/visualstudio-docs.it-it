---
title: 'Procedura: configurare l''analisi codice per un progetto di codice gestito | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 575b81e9c213e4025cd38921ad467869686d867c
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procedura: Configurare l'analisi codice per un progetto di codice gestito

In Visual Studio, è possibile scegliere da un elenco di analisi del codice *set di regole* da applicare a un progetto di codice gestito. Il set di regole predefinito è regole minime consigliate di Microsoft. È possibile applicare un altro set di regole a un progetto o a tutti i progetti in una soluzione.  
  
> [!NOTE]
> Per informazioni su come configurare una set di regole per le applicazioni Web ASP.NET, vedere [come: Configura analisi codice per un'applicazione Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Per configurare una set di regole per un progetto .NET Framework  
  
1.  In **Esplora**, fare clic sul progetto.  
  
2.  Nel **Analizza** menu, fare clic su **Configura analisi codice per** *ProjectName*.  
  
3.  Nel **configurazione** e **piattaforma** gli elenchi, scegliere la piattaforma di destinazione e configurazione di compilazione.  
  
4.  Per eseguire l'analisi codice ogni volta che il progetto viene compilato con la configurazione selezionata, selezionare il **Attiva analisi codice in fase di compilazione** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice aprendo il **Analizza** menu e scegliere * * Esegui analisi del codice su * ProjectName * * *.  
  
5.  Per impostazione predefinita, l'analisi del codice non segnala gli avvisi del codice generato automaticamente da strumenti esterni. Per visualizzare gli avvisi del codice generato, deselezionare il **Elimina i risultati dal codice generato** casella di controllo.  
  
    > [!NOTE]
    > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un form o un modello, senza che venga sovrascritto.
  
6.  Nel **eseguire il set di regole** elenco, effettuare una delle operazioni seguenti:  
  
    -   Fare clic su set di regole che si desidera utilizzare.  
  
    -   Fare clic su  **\<Sfoglia... >** per specificare set di una regola personalizzata esistente non è presente nell'elenco.  
  
    -   Definire un set di regole personalizzato.  
  
         Per ulteriori informazioni, vedere [la creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Vedere anche

[Procedura dettagliata: configurazione e uso di un set di regole personalizzate](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)