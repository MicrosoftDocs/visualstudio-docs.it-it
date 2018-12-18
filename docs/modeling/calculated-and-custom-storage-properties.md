---
title: Proprietà di archiviazione calcolate e personalizzate
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1bdf6d413287f75fa57ef80525a43f86cd55c74d
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="calculated-and-custom-storage-properties"></a>Proprietà di archiviazione calcolate e personalizzate
Tutte le proprietà di dominio in un linguaggio specifico di dominio (DSL) possono essere visualizzate all'utente nel diagramma e in Esplora risorse della lingua e sono accessibili da codice programma. Tuttavia, le proprietà variano in modo che i relativi valori vengono archiviati.

## <a name="kinds-of-domain-properties"></a>Tipi di proprietà di dominio
 Nella definizione del linguaggio DSL, è possibile impostare il **tipo** di una proprietà di dominio, come indicato nella tabella riportata di seguito:

|Tipo di proprietà di dominio|Descrizione|
|--------------------------|-----------------|
|**Standard** (predefinito)|Una proprietà di dominio che viene salvata nel *archiviare* e serializzato nel file.|
|**Calcolata**|Proprietà di dominio di sola lettura che non viene salvata nell'archivio, ma viene calcolata da altri valori.<br /><br /> Ad esempio, `Person.Age` può essere calcolato da `Person.BirthDate`.<br /><br /> È necessario fornire il codice che esegue il calcolo. In genere, il calcolo del valore da altre proprietà di dominio. Tuttavia, è possibile utilizzare anche le risorse esterne.|
|**Archiviazione personalizzata**|Proprietà di dominio che non viene salvata direttamente nell'archivio, ma può essere sia get che set.<br /><br /> È necessario fornire i metodi get e set il valore.<br /><br /> Ad esempio, `Person.FullAddress` può essere archiviata `Person.StreetAddress`, `Person.City`, e `Person.PostalCode`.<br /><br /> È inoltre possibile accedere a risorse esterne, ad esempio per ottenere e impostare i valori da un database.<br /><br /> Il codice non necessario impostare i valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Vedere [transazioni e setter personalizzato](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Fornire il codice per una proprietà calcolata o personalizzato di archiviazione
 Se si imposta il tipo di una proprietà dominio calcolato o archiviazione personalizzata, è necessario fornire i metodi di accesso. Quando si compila la soluzione, un report di errore indicherà che cos'è obbligatorio.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Per definire un valore calcolato o una proprietà di archiviazione personalizzato

1.  DslDefinition.dsl, selezionare la proprietà di dominio nel diagramma o in **Esplora DSL**.

2.  Nel **proprietà** finestra, impostare il **tipo** campo **calcolato** o **archiviazione personalizzata**.

     Assicurarsi di aver impostato anche il relativo **tipo** nel modo desiderato.

3.  Fare clic su **Trasforma tutti i modelli** nella barra degli strumenti di **Esplora**.

4.  Scegliere **Compila soluzione** dal menu **Compila**.

     Viene visualizzato il messaggio di errore seguente: "*YourClass* non contiene una definizione di Get*YourProperty*."

5.  Fare doppio clic sul messaggio di errore.

     Dsl\GeneratedCode\DomainClasses.cs o DomainRelationships.cs viene aperto. Sopra la chiamata al metodo evidenziato, un commento viene richiesto di fornire un'implementazione di Get*YourProperty*().

    > [!NOTE]
    >  Questo file viene generato da DslDefinition.dsl. Se si modifica questo file, le modifiche andranno perse la volta successiva che si fa clic su **Trasforma tutti i modelli**. Al contrario, aggiungere il metodo richiesto in un file separato.

6.  Creare o aprire un file di classe in una cartella distinta, ad esempio CustomCode\\*YourDomainClass*. cs.

     Assicurarsi che lo spazio dei nomi è uguale a quello del codice generato.

7.  Nel file di classe, scrivere un'implementazione parziale della classe di dominio. Nella classe, scrivere una definizione per la mancante `Get` metodo che è simile al seguente esempio:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8.  Se si imposta **tipo** a **archiviazione personalizzata**, sarà inoltre necessario fornire un `Set` metodo. Ad esempio:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Il codice non necessario impostare i valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Vedere [transazioni e setter personalizzato](#setters).

9. Compilare ed eseguire la soluzione.

10. Verificare la proprietà. Assicurarsi che si tenta di **Annulla** e **Ripeti**.

##  <a name="setters"></a> Le transazioni e setter personalizzato
 Nel metodo Set della proprietà di archiviazione personalizzata, non è necessario aprire una transazione, poiché il metodo viene chiamato in genere all'interno di una transazione attiva.

 Tuttavia, il metodo Set potrebbe anche essere chiamato se l'utente richiama l'annullamento o ripristino oppure se una transazione è in fase di rollback. Quando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> è true, il metodo Set deve comportarsi come indicato di seguito:

-   Consigliabile non apportare modifiche nell'archivio, ad esempio l'assegnazione di valori di altre proprietà di dominio. Gestione degli annullamenti imposterà i relativi valori.

-   Tuttavia, è necessario aggiornare alcuna risorsa esterna, ad esempio database o il contenuto del file o oggetti di fuori dell'archivio. Questo garantirà che si trovano in synchronism con i valori nell'archivio.

 Ad esempio:

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 Per ulteriori informazioni sulle transazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Proprietà delle proprietà di dominio](../modeling/properties-of-domain-properties.md)
- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)