---
title: 'Procedura: creare una soluzione per un linguaggio specifico di dominio'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 955c8f7a6dbc55d61b1cba77f38b2d394742e49c
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Procedura: creare una soluzione per un linguaggio specifico di dominio
Un linguaggio specifico di dominio (DSL) viene creato utilizzando una versione specializzata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione.

## <a name="prerequisites"></a>Prerequisiti
 Prima di iniziare questa procedura, è innanzitutto necessario installare questi componenti:

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|SDK di visualizzazione e modellazione di Visual Studio||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione di linguaggio specifico di dominio

#### <a name="to-create-a-domain-specific-language-solution"></a>Per creare una soluzione di linguaggio specifico di dominio

1.  Avviare la procedura guidata DSL.

    1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

    2.  Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

    3.  In **tipi di progetto**, espandere il **altri tipi di progetto** nodo e fare clic su **estendibilità**.

    4.  Fare clic su **progettazione linguaggio specifico di dominio**.

    5.  Nel **nome** , digitare un nome per la soluzione. Fare clic su **OK**.

         Il **Domain-Specific Language progettazione guidata** viene visualizzato.

        > [!NOTE]
        >  Preferibilmente, il nome digitato deve essere un Visual identificatore c# valido, poiché può essere utilizzato per generare il codice.

     ![Creare finestra di dialogo DSL](../modeling/media/create_dsldialog.png "Create_DSLDialog")

2.  Scegliere un modello DSL.

     Nel **selezionare le opzioni di linguaggio specifico di dominio** pagina, selezionare uno dei modelli di soluzione, ad esempio **Language minimo**. Scegliere un modello simile a DSL che si desidera creare.

     Per ulteriori informazioni sui modelli di soluzione, vedere [scelta di un modello di soluzione di linguaggio specifico di dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

3.  Immettere un'estensione di file di **estensione** pagina. Deve essere univoco nel computer e in qualsiasi computer in cui si desidera installare del linguaggio DSL. Verrà visualizzato il messaggio **Nessuna applicazione o un editor di Visual Studio utilizzano questa estensione**.

    -   Se è stata utilizzata l'estensione di file in DSL sperimentale precedente che non è stato completamente installato, è comunque possibile cancellarli out utilizzando il **Reimposta l'istanza sperimentale** strumento, è reperibile nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menu SDK.

    -   Se un altro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione che usa l'estensione di file è stato completamente installato nel computer in uso, è consigliabile disinstallarlo. Nel **strumenti** menu, fare clic su **Extension Manager**.

4.  Controllare e modificare se necessario, i campi nelle pagine rimanenti della procedura guidata. Quando si è soddisfatti delle impostazioni, fare clic su **fine**. Per ulteriori informazioni sulle impostazioni, vedere [pagine della procedura guidata Progettazione DSL](#settings).

     La procedura guidata crea una soluzione che include due progetti, sono denominati **Dsl** e **DslPackage**.

    > [!NOTE]
    >  Se viene visualizzato un messaggio che avvisa l'utente non eseguono modelli di testo da origini non attendibili, fare clic su **OK**. È possibile impostare questo messaggio non venga visualizzato nuovamente.

##  <a name="settings"></a> Le pagine della finestra di progettazione DSL
 È possibile lasciare molti dei campi invariati rispetto ai valori predefiniti. Tuttavia, assicurarsi che è impostato il campo dell'estensione di File.

### <a name="solution-settings-page"></a>Pagina Impostazioni soluzione
 **Il modello si desidera basare il linguaggio specifico di dominio?**
Scegliere un modello simile a DSL che si desidera creare. I diversi modelli forniscono punti di partenza ideale. Quando si seleziona un modello di soluzione, la procedura guidata consente di visualizzare una descrizione. Per ulteriori informazioni sui modelli di soluzione, vedere [scelta di un modello di soluzione di linguaggio specifico di dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Ciò che si desidera assegnare un nome di linguaggio specifico di dominio?**
Valore predefinito è il nome della soluzione. Codice viene generato da questo valore. Deve essere valido come nome di classe c#.

### <a name="file-extension-page"></a>Pagina di estensione di file
 **Deve modello quale estensione di file di utilizzo?**
Digitare una nuova estensione di file.

 Verificare che questa estensione di file non già registrata per l'utilizzo in questo computer, come indicato di seguito:

 Cercare in **altri strumenti e applicazioni registrato per gestire questa estensione**. Se viene visualizzato il messaggio **Nessuna applicazione o un editor di Visual Studio utilizzano questa estensione**, è possibile utilizzare questa estensione di file.

 Se viene visualizzato un elenco di strumenti o pacchetti, è necessario eseguire una delle operazioni seguenti:

-   Digitare un'estensione di file diverso.

     \- oppure -

-   Reimpostare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] istanza sperimentale. Annullare tutte DSL che sono creati in precedenza. Nel **avviare** menu, fare clic su **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare il Istanza di Microsoft Visual Studio 2010 sperimentale**. È possibile ricompilare qualsiasi altro DSL che si desidera utilizzare di nuovo.

     \- oppure -

-   Se un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione che usa l'estensione di file è stato completamente installato nel computer in uso, disinstallarla. Nel **strumenti** menu, fare clic su **Extension Manager**.

### <a name="product-settings-page"></a>Pagina Impostazioni di prodotto
 **Che cos'è il nome del prodotto a cui appartiene il nuovo linguaggio specifico di dominio?**
Valore predefinito è il nome del linguaggio DSL.

 Questo valore viene utilizzato in Esplora risorse (o Esplora File) per descrivere i file con estensione di file.

 **Che cos'è il nome della società a cui appartiene il prodotto?**
Il nome della società.

 Questo valore viene incorporato nelle proprietà del pacchetto di DSL AssemblyInfo.

 **Che cos'è lo spazio dei nomi radice per i progetti in questa soluzione?**
L'impostazione predefinita è un nome composto dall'azienda e i nomi di prodotto.

### <a name="signing-page"></a>Pagina firma
 **Creare un file di chiave con nome sicuro** l'opzione predefinita consiste nel creare una nuova chiave per firmare l'assembly DSL.

 **Usare chiave con nome sicuro esistente** utilizzare questa opzione se si desidera integrare tale linguaggio DSL con un altro assembly.

 Per ulteriori informazioni sulla denominazione sicuro, vedere [creazione e uso degli assembly](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Vedere anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
