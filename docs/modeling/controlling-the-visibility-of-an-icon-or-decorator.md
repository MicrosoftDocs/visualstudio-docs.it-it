---
title: Controllo della visibilità di un'icona o di un elemento Decorator
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 070f49b09086d463a13470f389a4857225b7add9
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controllo della visibilità di un'icona o di un elemento Decorator
Oggetto *decorator* è un'icona o una riga di testo che viene visualizzato in una forma in un linguaggio specifico di dominio (DSL). È possibile visualizzare l'elemento decorator e scompaiono a seconda dello stato delle proprietà nel modello. Su una forma che rappresenta una persona, ad esempio, è possibile usare le icone diverse che vengono visualizzate in base al sesso dell'utente, numero di elementi figlio e così via.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controllare la visibilità di un'icona o di un elemento decorator
 La procedura seguente si presuppone che già definito una forma e il relativo mapping a una classe di dominio. Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Per controllare la visibilità di un elemento decorator icona o il testo

1.  Nel diagramma definizione DSL, aggiungere alla classe forma di icone o gli elementi Decorator testo che si desidera visualizzare.

    1.  Fare doppio clic su classe shape, scegliere **Aggiungi**, quindi scegliere il tipo di elemento decorator richiesto.

    2.  Impostare l'elemento decorator **posizione** proprietà. Più di un elemento decorator può avere la stessa posizione. Ad esempio, è possibile usare le icone per maschio e femmina condivisione nella stessa posizione.

    3.  Impostare il **icona predefinita** proprietà di un elemento decorator icona.

2.  Selezionare la mappa di elemento diagramma, ovvero la linea grigia tra la classe di forma e la classe di dominio del diagramma della definizione DSL.

3.  Nella finestra Dettagli DSL nel **Decorator mappe** , selezionare un elemento decorator. Ad esempio, MaleDecorator.

4.  Controllare il **filtro visibilità** casella.

5.  Se la proprietà di dominio che deve controllare la visibilità della classe di dominio immediato, lasciare **percorso proprietà filtro** vuoto.

     In caso contrario, fare clic sul menu a discesa e passare alla classe in cui si trova la proprietà o relazione.

    -   Per evitare una segnalazione errori, non devono passare tramite una relazione contrassegnata con "*" nello strumento di navigazione.

6.  Impostare il **proprietà Filter** a una proprietà di dominio. Ad esempio, il sesso.

7.  Nel **visibilità voci** elenco, aggiungere i valori di questa proprietà di dominio per il quale l'elemento decorator deve essere visibile. Ad esempio, Male.

8.  Ripetere i passaggi per ogni icona.

9. **Trasforma tutti i modelli**, compilare ed eseguire e aprire un diagramma di test.

10. Quando si modifica il valore della proprietà controllo, le espressioni Decorator dovrà essere visualizzato e scompare.

 Spesso si desidera visibilità sia controllata da una formula più complessa rispetto a una semplice serie di valori. Ad esempio, utilizzare un'icona dipendono dal numero di collegamenti di un determinato tipo, o per renderlo variano a seconda che un numero è in un intervallo specifico. In tal caso, utilizzare la procedura seguente.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Per controllare la visibilità di un elemento decorator basate su una formula

1.  Aggiungere una proprietà calcolata dominio per la classe di dominio. Nel **proprietà** finestra, impostare i valori seguenti:

     **IsBrowsable =**`False`**-in tal modo, la proprietà da parte dell'utente** 

     **Tipo =**`Calculated`**-ciò significa che verrà fornito il codice che calcola il relativo valore** 

     **Nome** ad esempio **DecoratorControl**

     **tipo** = `Boolean`

     Per ulteriori informazioni, vedere [calcolate e le proprietà di archiviazione personalizzato](../modeling/calculated-and-custom-storage-properties.md).

2.  Verificare la nuova proprietà di controllare la visibilità decorator.

    1.  Selezionare la mappa di elemento diagramma, ovvero la linea grigia dalla classe di dominio alla forma. Nel **dettagli DSL** finestra, aprire il **DecoratorMap** scheda.

    2.  Controllare il **filtro visibilità** casella.

    3.  In **proprietà Filter**, selezionare la proprietà del controllo **DecoratorControl**.

    4.  In **voci visibilità**, immettere `True`.

3.  Fare clic su **Trasforma tutti i modelli** nella barra degli strumenti Esplora soluzioni.

4.  Fare clic su **Compila soluzione** sul **compilare** menu.

5.  Fare doppio clic sulla segnalazione errori che è presente: "*YourClass* non contiene una definizione per GetDecoratorControlValue...".

     Verrà aperto l'editor di testo in Dsl\GeneratedCode\DomainClasses.cs. Sopra l'errore evidenziato è un commento che richiede di aggiungere un metodo.

6.  Si noti di spazio dei nomi, classe e metodo che non sono presenti.  Ad esempio, Company.FamilyTree.Person.GetDecoratorControlValue().

7.  In un file di codice separato, scrivere una definizione di classe parziale che contiene il metodo mancano. Ad esempio:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Per ulteriori informazioni sulla personalizzazione del modello con il codice del programma, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

8.  Ricompilare ed eseguire la soluzione.

## <a name="see-also"></a>Vedere anche

- [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)
- [Impostazione di un'immagine di sfondo in un diagramma](../modeling/setting-a-background-image-on-a-diagram.md)
- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)