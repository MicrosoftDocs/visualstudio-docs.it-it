---
title: Usare e configurare gli analizzatori di Roslyn in Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2eeebb1fb631c0890c7bcb11160109813a31eef1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Configurare e usare le regole dell'analizzatore Roslyn

Le regole dell'analizzatore .NET compiler Platform ("Roslyn"), oppure *diagnostica*, analizzare il codice c# o Visual Basic durante la digitazione. Ogni dato diagnostico ha uno stato di gravità e la soppressione predefinito che può essere sovrascritto per il progetto. Questo articolo descrive impostazione regola livello di gravità, utilizzando set di regole e disattivazione dei violazioni.

## <a name="analyzers-in-solution-explorer"></a>Analizzatori in Esplora soluzioni

È possibile eseguire gran parte della personalizzazione di dati diagnostici analyzer dal **Esplora soluzioni**. Se si [installare analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet, un **analizzatori** nodo viene visualizzato sotto il **riferimenti** o **dipendenze** nodo  **Esplora soluzioni**. Se si espande **analizzatori**e quindi espandere uno degli assembly analyzer, vedrai tutti i dati diagnostici nell'assembly.

![Nodo analizzatori in Esplora soluzioni](media/analyzers-expanded-in-solution-explorer.png)

È possibile visualizzare le proprietà di una diagnostica, inclusi la descrizione e alla gravità predefinito, nelle **proprietà** finestra. Per visualizzare le proprietà, fare clic sulla regola e selezionare **delle proprietà**, oppure selezionare la regola e quindi premere **Alt**+**invio**.

![Proprietà diagnostica nella finestra proprietà](media/analyzer-diagnostic-properties.png)

Per visualizzare la documentazione online per la diagnostica, fare clic su diagnostica e selezionare **Visualizza la Guida**.

Le icone accanto a ogni dato diagnostico in **Esplora soluzioni** corrispondono alle icone vedono la regola impostata quando si apre nell'editor:

- "i" in un cerchio indica un [gravità](#rule-severity) di **Info**
- il "!" in un triangolo indica un [gravità](#rule-severity) di **avviso**
- la "x" in un cerchio indica un [gravità](#rule-severity) di **errore**
- "i" in un cerchio su sfondo colore chiaro indica un [gravità](#rule-severity) di **Hidden**
- la freccia rivolta verso il basso in un cerchio indica che viene eliminata la diagnostica

![Icone di diagnostica in Esplora soluzioni](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Set di regole

Un [set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) è un file XML che archivia lo stato della gravità ed eliminazione per la diagnostica singoli. Set di regole si applicano a un singolo progetto e un progetto può avere più set di regole. Per visualizzare la regola attiva impostata nell'editor, fare clic sul **analizzatori** nodo **Esplora** e selezionare **aprire Active del Set di regole**. Impostato se questa è la prima volta che si accede alla regola, un file denominato  *\<projectname > estensione ruleset* viene aggiunto al progetto e visualizzato in **Esplora**.

> [!NOTE]
> Set di regole includono analisi statica del codice (binario) sia le regole dell'analizzatore Roslyn.

È possibile modificare la regola attiva impostata per un progetto nel **analisi del codice** scheda delle proprietà del progetto. Selezionare il set di regole nel **eseguire il set di regole** elenco a discesa. È inoltre possibile aprire il set di regole dal **analisi del codice** pagina delle proprietà selezionando **aprire**.

## <a name="rule-severity"></a>Gravità regola

È possibile configurare il livello di gravità delle regole di Analizzatore, o *diagnostica*, se si [installare gli analizzatori](../code-quality/install-roslyn-analyzers.md) come pacchetto NuGet. Nella tabella seguente illustra le opzioni di gravità per diagnostica:

|Gravità|Comportamento in fase di compilazione|Comportamento dell'editor|
|-|-|-|
|Error|Le violazioni vengono visualizzati come *errori* nel **elenco errori** nella riga di comando output di compilazione e causare compilazioni esito negativo.|Problema di codice è sottolineato con una rossa ondulata e contrassegnata da una piccola casella rossa nella barra di scorrimento.|
|Avviso|Le violazioni vengono visualizzati come *gli avvisi* nel **elenco errori** e nella riga di comando output di compilazione, ma non le compilazioni per avere esito negativo.|Problema di codice è sottolineato con una verde ondulata e contrassegnata da un quadratino verde nella barra di scorrimento.|
|Info|Le violazioni vengono visualizzati come *messaggi* nel **elenco errori**e non è affatto nell'output di compilazione da riga di comando.|Problema di codice è sottolineato con un grigio Ondulato e contrassegnato da una piccola casella grigia nella barra di scorrimento.|
|Hidden|Non visibili all'utente.|Non visibili all'utente. La diagnostica viene segnalata al motore di diagnostica di IDE, tuttavia.|
|Nessuno|Eliminato completamente.|Eliminato completamente.|

Inoltre, è possibile "Reimposta" gravità della regola impostandolo su **predefinito**. Ogni dato diagnostico con gravità predefiniti che possono essere visualizzate nel **proprietà** finestra.

Nella schermata seguente mostra tre diverse violazioni di diagnostica nell'editor di codice, con tre diversi livelli di gravità. Si noti il colore dell'ondulate, così come la casella di piccole dimensioni nella barra di scorrimento a destra.

![Violazione di errore, avviso e info nell'editor di codice](media/diagnostics-severity-colors.png)

La seguente schermata Mostra violazioni di tre stesso come appaiono nel **elenco errori**:

![Violazione di errore, avviso e info nell'elenco errori](media/diagnostics-severities-in-error-list.png)

È possibile modificare il livello di gravità di una regola da **Esplora soluzioni**, o il  *\<projectname > estensione ruleset* file che viene aggiunto alla soluzione dopo aver modificato il livello di gravità di una regola in  **Esplora soluzioni**.

![File di set di regole in Esplora soluzioni](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Per impostare la gravità di regola da Esplora soluzioni

1. In **Esplora soluzioni**, espandere **riferimenti** > **analizzatori** (**dipendenze**  >  **Analizzatori** per i progetti .NET Core).

1. Espandere l'assembly che contiene la regola che si desidera impostare la gravità per.

1. Pulsante destro del mouse sulla regola e selezionare **impostare regola imposta gravità**. Nel menu a comparsa, selezionare una delle opzioni di gravità.

   Il livello di gravità per la regola viene salvata nel file di set di regole attivo.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Per impostare regola gravità nella regola di set di file

1. Aprire il set di regole file facendovi doppio clic in **Esplora soluzioni**, se si seleziona **Apri Set di regole attivo** nel menu di scelta rapida del **analizzatori** nodo, o selezionando **Open** sul **analisi del codice** pagina delle proprietà per il progetto.

1. Selezionare la regola espandendo l'assembly che lo contiene.

1. Nel **azione** colonna, selezionare il valore per aprire un elenco a discesa e selezionare il livello di gravità desiderato dall'elenco.

   ![File di set di regole aperto nell'editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Escludere le violazioni

Esistono diversi modi per eliminare delle violazioni delle regole:

- Per eliminare tutte le violazioni corrente, selezionare **Analizza** > **Esegui analisi del codice ed Elimina problemi attivi** nella barra dei menu. Ciò è talvolta detta "base".

- Esclusione di un oggetto diagnostic dal **Esplora soluzioni**, impostare la gravità **Nessuno**.

- Per eliminare la diagnostica dall'editor set di regole, deselezionare la casella accanto al relativo nome o impostare **azione** alla **Nessuno**.

- Per eliminare la diagnostica dall'editor di codice, posizionare il cursore nella riga di codice con la violazione e premere **Ctrl**+**.** Per aprire la **azioni rapide** menu. Selezionare **esclusione CAXXXX: NomeTipoDescrittivo** > **nell'origine** oppure **esclusione CAXXXX: NomeTipoDescrittivo** > **nel File di eliminazione**.

   ![Esclusione di diagnostica dal menu Azioni rapide](media/suppress-diagnostic-from-editor.png)

- Esclusione di un oggetto diagnostic dal **elenco errori**, fare clic sul messaggio, errore o avviso e selezionare **Suppress** > **In origine** o**Esclusione** > **file di eliminazione**.

   - Se si seleziona **In origine**, la **Anteprima modifiche** verrà visualizzata la finestra di dialogo e viene visualizzata un'anteprima del linguaggio c# [#pragma avviso](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic [#Disable avviso](/dotnet/visual-basic/language-reference/directives/directives) direttiva che viene aggiunto al codice sorgente.

      ![Anteprima di aggiunta #pragma avviso nel file di codice](media/pragma-warning-preview.png)

   - Se si seleziona **File di eliminazione**, la **Anteprima modifiche** verrà visualizzata la finestra di dialogo e viene visualizzata un'anteprima del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo che viene aggiunto al file di eliminazioni globali.

      ![Anteprima di aggiungere file di eliminazione SuppressMessage (attributo)](media/preview-changes-in-suppression-file.png)

   Nel **Anteprima modifiche** finestra di dialogo, seleziona **applica**.

> [!NOTE]
> In un progetto .NET Core, se si aggiunge un riferimento a un progetto che contiene gli analizzatori di NuGet, tali analizzatori vengono aggiunti automaticamente al progetto dipendente troppo. Per disabilitare questo comportamento, ad esempio se il progetto dipendente è un progetto di unit test, contrassegnare il pacchetto NuGet come privata nel *csproj* oppure *vbproj* file del progetto cui si fa riferimento:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>Vedere anche

- [Panoramica di Roslyn analizzatori in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Inviare un bug analyzer Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Utilizzare set di regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Esclusione di avvisi di analisi codice](../code-quality/in-source-suppression-overview.md)