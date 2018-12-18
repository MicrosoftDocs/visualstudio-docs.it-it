---
title: Strumenti di Entity Framework in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 906176ebf782a537dffad1deddb41c71739e8a5e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="entity-framework-tools-in-visual-studio"></a>Strumenti di Entity Framework in Visual Studio
Entity Framework è una tecnologia di mapping relazionale a oggetti che consente agli sviluppatori .NET di lavorare con dati relazionali utilizzando oggetti specifici del dominio. In questo modo la maggior parte del codice di accesso ai dati che in genere gli sviluppatori devono scrivere non è più necessaria. Entity Framework è il mapping relazionale a oggetti consigliato (ORM) tecnologia per le nuove applicazioni .NET.

Strumenti di Entity Framework sono progettati per facilitare la compilazione di applicazioni Entity Framework (EF). La documentazione completa per Entity Framework è qui: [EF Core e 6 EF](/ef/).

Con strumenti di Entity Framework, è possibile creare un *modello concettuale* da un oggetto esistente del database e quindi graficamente visualizzare e modificare il modello concettuale. È inoltre possibile creare prima graficamente un modello concettuale e successivamente generare un database di supporto al modello. In entrambi i casi, è possibile aggiornare automaticamente il modello quando viene modificato il database sottostante e generare automaticamente codice del livello oggetti per l'applicazione. La generazione del database e del codice del livello oggetti è personalizzabile.

Strumenti di Entity Framework vengono installati come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer. È inoltre possibile installarli come componente singoli sotto il **SDK, librerie e Framework** categoria.

Questi sono gli strumenti specifici che costituiscono gli strumenti di Entity Framework in Visual Studio:

-   È possibile utilizzare il [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] progettazione** (**Entity Designer**) per creare visivamente e modificare le entità, associazioni, mapping e le relazioni di ereditarietà. Il **Entity Designer** genera inoltre [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] codice del livello oggetti.

-   È possibile utilizzare il  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] guidata** per generare un modello concettuale da un database esistente e aggiungere informazioni di connessione di database per l'applicazione.

-   È possibile utilizzare il **procedura guidata Crea Database** per creare un modello concettuale prima e quindi creare un database che supporta il modello.

-   È possibile utilizzare il **procedura guidata Aggiorna modello** per aggiornare il modello concettuale, un modello di archiviazione e i mapping quando sono state apportate modifiche al database sottostante.

    > [!NOTE]
    >  A partire da Visual Studio 2010, gli strumenti di Entity Framework non supportano [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Gli strumenti generano o modificare un file con estensione edmx. Questo file con estensione edmx contiene informazioni che descrivono il modello concettuale, il modello di archiviazione e i mapping tra di essi. Per ulteriori informazioni, vedere [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

[Strumenti di Entity Framework Power](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) consentono di compilare applicazioni che utilizzano Entity Data Model. Gli strumenti avanzati possono generare un modello concettuale, convalidare un modello esistente, produrre file del codice sorgente contenenti classi di oggetti basate sul modello concettuale e produrre file del codice sorgente contenenti visualizzazioni che genera il modello. Per informazioni dettagliate, vedere [Pre-Generated Mapping viste](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Viene descritto come utilizzare [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] strumenti, che [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] fornisce, per creare applicazioni.|
|[Entity Data Model](/dotnet/framework/data/adonet/entity-data-model)|Vengono forniti collegamenti e informazioni per l'utilizzo di dati utilizzati dalle applicazioni compilate in [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|
|[Documentazione di Entity Framework (EF))](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|Fornisce un indice di video, esercitazioni e documentazione avanzata che consentono di sfruttare al meglio di Entity Framework.|
|[ASP.NET 5 dell'applicazione nel nuovo Database](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Viene descritto come creare una nuova applicazione ASP.NET 5 con Entity Framework 7.|

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)