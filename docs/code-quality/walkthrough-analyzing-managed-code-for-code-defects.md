---
title: Procedura dettagliata di analisi del codice gestito per errori del codice | Documenti Microsoft
ms.date: 01/29/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 98d1bbd347870bd704a0d17d7ae559da00e9adb5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Procedura dettagliata: Errori di analisi codice gestito per il codice

In questa procedura dettagliata, si sarà esaminato un progetto gestito per errori del codice utilizzando lo strumento di analisi codice.

In questa procedura dettagliata è illustrato il processo di utilizzo dell'analisi del codice per analizzare gli assembly di codice gestito .NET per conformità con la finestra di progettazione Microsoft .NET Framework.

## <a name="create-a-class-library"></a>Creare una libreria di classi

### <a name="to-create-a-class-library"></a>Per creare una libreria di classi

1. Nel menu **File** scegliere **Nuovo** > **Progetto**.

1. Nel **nuovo progetto** finestra di dialogo espandere **installato** > **Visual c#** e quindi scegliere **Windows Desktop classico**.

1. Scegliere il **libreria di classi (.NET Framework)** modello.

1. Nel **nome** nella casella di testo **CodeAnalysisManagedDemo** e quindi fare clic su **OK**.

1. Dopo aver creato il progetto, aprire il *Class1.cs* file.

1. Sostituire il testo esistente in Class1.cs con il codice seguente:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Salvare il file Class1.cs.

## <a name="analyze-the-project"></a>Analizzare il progetto

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Per analizzare un progetto gestito per errori del codice

1. Selezionare il progetto CodeAnalysisManagedDemo in **Esplora**.

1. Scegliere **Proprietà** dal menu **Progetto**.

     Verrà visualizzata la pagina proprietà CodeAnalysisManagedDemo.

1. Scegliere il **analisi del codice** scheda.

1. Assicurarsi che **Attiva analisi codice in fase di compilazione** è selezionata.

1. Dal **eseguire il set di regole** elenco a discesa, seleziona **tutte le regole Microsoft**.

1. Nel **File** menu, fare clic su **Salva elementi selezionati**e quindi chiudere le pagine delle proprietà.

1. Nel **compilare** menu, fare clic su **compilare CodeAnalysisManagedDemo**.

    Cui vengono visualizzati gli avvisi di compilazione progetto CodeAnalysisManagedDemo il **elenco errori** e **Output** windows.

## <a name="correct-the-code-analysis-issues"></a>Correggere i problemi di analisi codice

### <a name="to-correct-code-analysis-rule-violations"></a>Per correggere le violazioni di regole di analisi codice

1. Nel **vista** menu, scegliere **elenco errori**.

    In base al profilo di sviluppo scelto, potrebbe essere necessario scegliere **altre finestre** nel **vista** menu, quindi scegliere **elenco errori**.

1. In **Esplora**, scegliere **Mostra tutti i file**.

1. Espandere il nodo di proprietà e quindi aprire il *AssemblyInfo.cs* file.

1. Per correggere gli avvisi, utilizzare i suggerimenti seguenti:

   [CA1014: Contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: "demo" deve essere contrassegnato con CLSCompliantAttribute e il relativo valore deve essere true.

   1. Aggiungere il codice `using System;` al file AssemblyInfo.cs.

   1. Successivamente, aggiungere il codice `[assembly: CLSCompliant(true)]` alla fine del file AssemblyInfo.cs.

   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il seguente costruttore per questa classe: public demo (String)

   1. Aggiungere il costruttore `public demo (String s) : base(s) { }` alla classe `demo`.

   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il seguente costruttore per questa classe: public demo (String, eccezione)

   1. Aggiungere il costruttore `public demo (String s, Exception e) : base(s, e) { }` alla classe `demo`.

   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il seguente costruttore per questa classe: protetto demo (SerializationInfo, StreamingContext)

   1. Aggiungere il codice `using System.Runtime.Serialization;` all'inizio del file Class1.

   1. Successivamente, aggiungere il costruttore `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il seguente costruttore per questa classe: public demo)

   1. Aggiungere il costruttore `public demo () : base() { }` alla classe `demo` **.**

   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole del nome dello spazio dei nomi 'testCode' modificandolo in 'TestCode'.

   1. Modifica le maiuscole e minuscole dello spazio dei nomi `testCode` a `TestCode`.

   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole nome del tipo 'demo' modificandolo in 'Demo'.

   1. Modificare il nome del membro da `Demo`.

   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole nome di membro 'item' modificandolo in 'Item'.

   1. Modificare il nome del membro da `Item`.

   [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming: Rinomina 'testCode.demo' terminare con 'Exception'.

   1. Modificare il nome della classe e i relativi costruttori in `DemoException`.

   [CA2210: Gli assembly devono avere nomi sicuri validi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): firmare 'CodeAnalysisManagedDemo' con una chiave con nome sicuro.

   1. Nel **progetto** menu, scegliere **CodeAnalysisManagedDemo proprietà**.

      Vengono visualizzate le proprietà del progetto.

   1. Scegliere la scheda **Firma** .

   1. Selezionare il **firmare l'assembly** casella di controllo.

   1. Nel **scegliere un file chiave con nome sicuro** elenco, selezionare  **\<nuovo … >**.

      Il **Crea chiave con nome sicuro** viene visualizzata la finestra di dialogo.

   1. Nel **nome file di chiave**, digitare TestKey.

   1. Immettere una password e quindi scegliere **OK**.

   1. Nel **File** menu, scegliere **Salva elementi selezionati**, quindi chiudere le pagine delle proprietà.

   [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: aggiungere un attributo [Serializable] nel tipo 'demo' poiché questo tipo implementa ISerializable.

   1. Aggiungere il `[Serializable ()]` attributo alla classe `demo`.

   Dopo aver completato le modifiche, il file Class1.cs dovrebbe essere simile al seguente:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Ricompilare il progetto.

## <a name="exclude-code-analysis-warnings"></a>Escludere gli avvisi dell'analisi codice

### <a name="to-exclude-code-defect-warnings"></a>Per escludere gli avvisi degli errori di codice

1. Per ogni avviso rimanenti, eseguire le operazioni seguenti:

    1. Selezionare l'avviso nel **elenco errori**.

    1. Scegliere dal menu del pulsante destro del mouse o contesto, **Elimina** > **File di eliminazione**.

1. Ricompilare il progetto.

     Il progetto venga compilato senza errori o avvisi.

## <a name="see-also"></a>Vedere anche

[Analisi del codice per il codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)