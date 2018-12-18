---
title: 'Procedura: eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 83f80e9fe0bf68f5d10d8f3b76840b55de025f33
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Procedura: eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione
È possibile eseguire la migrazione di progetti che definiscono e utilizzano il linguaggio specifico di dominio per [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] dalla versione di [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] che è stata distribuita con [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Uno strumento di migrazione viene fornito come parte di [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Lo strumento converte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti e soluzioni che utilizzano o definiscono strumenti DSL.

 È necessario eseguire lo strumento di migrazione in modo esplicito: non viene avviato automaticamente quando si apre una soluzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Lo strumento e istruzioni dettagliate fornite nel documento è reperibile in questo percorso:

 **% Programma Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Prima che si esegue la migrazione dei progetti di DSL
 Lo strumento di migrazione modifica [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] file di progetto (**csproj**) e i file di soluzione (**sln**).

#### <a name="to-prepare-projects-for-migration"></a>Per preparare i progetti di migrazione.

-   Verificare che il **csproj** e **sln** possono essere scritti i file. Se sono sotto controllo del codice sorgente, assicurarsi che sono estratti.

-   Creare una copia delle cartelle di cui che si intende eseguire la migrazione.

## <a name="migrating-a-collection-of-projects"></a>La migrazione di una raccolta di progetti

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Per eseguire la migrazione di DSL progetti e soluzioni di Visual Studio 2010

1.  Avviare lo strumento di migrazione DSL.

    -   È possibile fare doppio clic su strumento in Esplora risorse (o Esplora File) o avviare lo strumento da un prompt dei comandi. Lo strumento è in questo percorso:

         **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2.  Scegliere una cartella che contiene le soluzioni e progetti che si desidera convertire.

    -   Immettere il percorso nella casella nella parte superiore dello strumento oppure fare clic su **Sfoglia**.

     Lo strumento di migrazione viene visualizzato un albero di progetti che definiscono o utilizzare DSL. La struttura ad albero include ogni progetto che utilizza il **Microsoft.VisualStudio.Modeling.Sdk** o **TextTemplating** assembly.

3.  Esaminare la struttura dei progetti e deselezionare i progetti che non si desidera convertire.

    -   Selezionare un progetto o una soluzione per visualizzare un elenco di modifiche che verrà apportate lo strumento.

        > [!NOTE]
        >  Le caselle di controllo da visualizzare accanto ai nomi di cartella non hanno effetto. È necessario espandere le cartelle da controllare i progetti e soluzioni.

4.  Convertire i progetti.

    1.  Fare clic su **convertire**.

         Prima di ogni file di progetto viene convertito, una copia della *progetto * * * con estensione csproj** viene salvato come *progetto * * *.vs2008.csproj**

         Una copia di ogni *soluzione * * *. sln** viene salvato come *soluzione * * *.vs2008.sln**

    2.  Provare a utilizzare le conversioni non riuscite che vengono segnalate.

         Gli errori vengono segnalati nella finestra di testo. Inoltre, la visualizzazione albero mostra un contrassegno rosso in ogni nodo che non è riuscito a convertire. È possibile fare clic sul nodo per ottenere ulteriori informazioni su questo tipo di errore.

5.  **Trasforma tutti i modelli** nelle soluzioni contenente correttamente convertire progetti.

    1.  Aprire la soluzione.

    2.  Fare clic su di **Trasforma tutti i modelli** pulsante nell'intestazione di Esplora soluzioni.

        > [!NOTE]
        >  È possibile rendere questo passaggio non necessari. Per ulteriori informazioni, vedere [come automatizzare Trasforma tutti i modelli](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6.  Aggiornare il codice personalizzato nei progetti convertiti.

    -   Tentativo di compilare i progetti e individuare eventuali errori.

    -   Test della finestra di progettazione.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche

- [Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)