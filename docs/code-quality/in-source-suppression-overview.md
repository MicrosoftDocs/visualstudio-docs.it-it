---
title: Esclusione di avvisi di analisi codice in Visual Studio
ms.date: 01/29/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 1b057b13697fe1ec41fdca1bef27ccb03637f696
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="suppress-code-analysis-warnings"></a>Esclusione di avvisi di analisi codice

Spesso è utile indicare che un messaggio di avviso non è applicabile. Indica ai membri del team che il codice è stato rivisto e che l'avviso può essere eliminato. Eliminazione (ISS) viene utilizzato in origine il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo per eliminare un avviso. L'attributo può essere posizionato vicino il segmento di codice che ha generato l'avviso. È possibile aggiungere il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo del file di origine digitando, oppure è possibile utilizzare il menu di scelta rapida su un avviso nel **elenco errori** per aggiungerlo automaticamente.

Il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo è un attributo condizionale incluso nei metadati dell'assembly del codice gestito, solo se il simbolo di compilazione CODE_ANALYSIS è definito in fase di compilazione.

In C + + CLI, utilizzare le macro CA\_Elimina\_messaggio o CA\_globale\_SUPPRESS_MESSAGE nel file di intestazione per aggiungere l'attributo.

> [!NOTE]
> Non utilizzare eliminazioni nell'origine nelle build di rilascio, per evitare che i metadati di eliminazione nell'origine di spedizione accidentalmente. Inoltre, a causa del costo di elaborazione dell'eliminazione nell'origine, è possano ridotte le prestazioni dell'applicazione.

> [!NOTE]
> Se si esegue la migrazione di un progetto di Visual Studio 2017, possono incontrare improvvisamente con un numero eccessivo di avvisi di analisi codice. Se non si è pronti per risolvere gli avvisi e disattivare temporaneamente l'analisi del codice, aprire pagine delle proprietà del progetto (**progetto** > ***progetto* Properties...** ) e passare al **analisi del codice** scheda. Deselezionare **Attiva analisi codice in fase di compilazione**e quindi ricompilare il progetto. In alternativa, è possibile selezionare un diversa, più piccolo set di regole per eseguire il codice. È necessario attivare l'analisi del codice in quando si è pronti per risolvere gli avvisi.

## <a name="suppressmessage-attribute"></a>SuppressMessage (attributo)

Quando si sceglie **Elimina** dal menu di un avviso di analisi codice nel contesto o il pulsante destro del mouse il **elenco errori**, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo viene aggiunto nel codice o di eliminazione globale del progetto file.

Il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> presenta il formato seguente:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Le proprietà dell'attributo includono:

- **Categoria della regola** -la categoria in cui la regola è definita. Per ulteriori informazioni sulle categorie di regole di analisi codice, vedere [gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Id regola** -l'identificatore della regola. Il supporto include sia un nome breve e a lungo per l'identificatore della regola. Il nome breve è CAXXXX: NOMETIPODESCRITTIVO; il nome lungo è CAXXXX:FriendlyTypeName.

- **Giustificazione** -il testo che consente di documentare il motivo dell'eliminazione del messaggio.

- **Id messaggio** -identificatore univoco di un problema per ogni messaggio.

- **Ambito** -la destinazione in cui è stato eliminato l'avviso. Se la destinazione non è specificata, cui è impostata la destinazione dell'attributo. Gli ambiti supportati includono:

    - Modulo

    - Spazio dei nomi

    - Risorsa

    - Tipo

    - Member

- **Destinazione** - un identificatore che consente di specificare la destinazione in cui è stato eliminato l'avviso. Deve contenere un nome completo di elementi.

## <a name="suppressmessage-usage"></a>Utilizzo di SuppressMessage

Avvisi dell'analisi del codice vengono eliminati al livello a cui il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> è applicato l'attributo. Ad esempio, l'attributo può essere applicato a livello di assembly, modulo, tipo, membro o parametro. Lo scopo di questo è strettamente accoppiato le informazioni di eliminazione per il codice in cui si verifica la violazione.

Il formato generale dell'eliminazione include la categoria della regola e un identificatore di regola, che contiene una rappresentazione leggibile facoltativa del nome della regola. Ad esempio:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Se esistono motivi di prestazioni strict per ridurre al minimo i metadati di eliminazione nell'origine, il nome della regola può essere omessa. La categoria della regola e il relativo ID regola insieme costituiscono un sufficientemente identificatore univoco della regola. Ad esempio:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Per ragioni di manutenibilità, omettere il nome della regola non è consigliabile.

## <a name="suppress-selective-violations-within-a-method-body"></a>Esclusione di violazioni selettive all'interno di un corpo del metodo

Gli attributi di eliminazione possono essere applicati a un metodo, ma non possono essere incorporati all'interno di un corpo del metodo. Ciò significa che tutte le violazioni di una particolare regola vengono soppressi se si aggiunge il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo al metodo.

In alcuni casi, si potrebbe essere necessario eliminare una particolare istanza della violazione, ad esempio, in modo che non è codice futuro automaticamente esenti dalla regola di analisi del codice. Alcune regole di analisi del codice consentono di eseguire questa operazione utilizzando il `MessageId` proprietà del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo. In generale, le regole per le violazioni di riguardo un simbolo specifico (una variabile locale o un parametro) legacy di `MessageId` proprietà. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) è riportato un esempio di una regola. Tuttavia, non rispettano le regole precedenti per le violazioni di codice eseguibile (non-simbolo) di `MessageId` proprietà. Inoltre, gli analizzatori di .NET Compiler Platform ("Roslyn") non rispettano la `MessageId` proprietà.

Per eliminare una violazione di un simbolo specifico di una regola, specificare il nome del simbolo per il `MessageId` proprietà del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo. L'esempio seguente mostra il codice con due violazioni di [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;uno per il `name` variabile e uno per il `age` variabile. Solo la violazione per il `age` simbolo viene eliminato.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Codice generato

I compilatori di codice gestito e alcuni strumenti di terze parti generano codice per facilitare lo sviluppo rapido del codice. Codice generato dal compilatore che viene visualizzato nel file di origine in genere è contrassegnato con il `GeneratedCodeAttribute` attributo.

È possibile scegliere se eliminare gli avvisi dell'analisi del codice e gli errori per il codice generato. Per informazioni sull'eliminazione di tali avvisi ed errori, vedere [procedura: esclusione di avvisi per il codice generato](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Analisi del codice ignora `GeneratedCodeAttribute` quando applicato a un intero assembly o un singolo parametro.

## <a name="global-level-suppressions"></a>Eliminazioni a livello globale

Lo strumento di analisi codice gestito viene esaminato `SuppressMessage` gli attributi applicati a livello di assembly, modulo, tipo, membro o parametro. Viene inoltre generato violazioni risorse e gli spazi dei nomi. Tali violazioni devono essere applicate a livello globale e hanno come ambite e di destinazione. Ad esempio, il messaggio seguente elimina una violazione dello spazio dei nomi:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quando si elimina un avviso con ambito spazio dei nomi, viene eliminato l'avviso sullo spazio dei nomi stesso. Non elimina l'avviso con i tipi nello spazio dei nomi.

Qualsiasi eliminazione può essere espresso specificando un ambito esplicito. Queste eliminazioni devono avvenire a livello globale. È possibile specificare a livello di membro eliminazione tramite la decorazione di un tipo.

Eliminazioni a livello globale sono l'unico modo per eliminare i messaggi che fanno riferimento al codice generato dal compilatore che non eseguono il mapping a un'origine utente specificato in modo esplicito. Ad esempio, il codice seguente elimina una violazione in un costruttore emesso dal compilatore:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` contiene sempre il nome completo dell'elemento.

## <a name="global-suppression-file"></a>File eliminazione globale

Il file eliminazione globale gestisce le eliminazioni a livello globale o le eliminazioni che non si specificano una destinazione. Ad esempio, in questo file vengono archiviate le eliminazioni per le violazioni a livello di assembly. Inoltre, alcune eliminazioni ASP.NET vengono memorizzate in questo file perché le impostazioni a livello di progetto non sono disponibili per un modello code-behind. Un file di eliminazione globale viene creato e aggiunto al progetto la prima volta che si seleziona il **File di eliminazione In progetto** opzione del **Elimina** comando il **elenco errori**finestra.

## <a name="see-also"></a>Vedere anche

- <xref:System.Diagnostics.CodeAnalysis>
- [Usare gli analizzatori di Roslyn](../code-quality/use-roslyn-analyzers.md)