---
title: I gestori eventi propagano le modifiche al di fuori del modello
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ba210e73d6adc3df2c4f584c5612d5642038ee8f
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>I gestori eventi propagano le modifiche al di fuori del modello

In Visualization and Modeling SDK, è possibile definire i gestori di eventi di archivio per propagare le modifiche alle risorse all'esterno di archivio, ad esempio non archiviare variabili, i file, i modelli in altri archivi o altri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensioni. Dopo la fine della transazione in cui si è verificato l'evento trigger vengono eseguiti i gestori di eventi di archivio. Vengono inoltre eseguite in un'operazione di annullamento o ripetizione. Diversamente dalle regole di archivio, di conseguenza, gli eventi di archiviazione sono più utili per l'aggiornamento dei valori che non rientrano nell'archivio. A differenza degli eventi di .NET, gestori di eventi di archivio vengono registrati per l'ascolto su una classe: non è necessario registrare un gestore separato per ogni istanza. Per ulteriori informazioni su come scegliere tra diversi modi per gestire le modifiche, vedere [propagazione delle modifiche e risposta agli](../modeling/responding-to-and-propagating-changes.md).

L'area con interfaccia grafica e altri controlli dell'interfaccia utente sono esempi di risorse esterne che possono essere gestiti dall'archivio eventi.

### <a name="to-define-a-store-event"></a>Per definire un evento di archiviazione

1.  Scegliere il tipo di evento che si desidera monitorare. Per un elenco completo, esaminare le proprietà di <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Ogni proprietà corrisponde a un tipo di evento. Utilizzato con maggiore frequenza sono tipi di evento:

    -   `ElementAdded` -attivata quando un elemento del modello, viene creato il collegamento di relazione, forma o il connettore.

    -   ElementPropertyChanged - attivato quando il valore di un `Normal` viene modificata la proprietà dominio. L'evento viene generato solo se i valori nuovi e precedenti non sono uguali. L'evento non può essere applicato alle proprietà di archiviazione calcolate e personalizzate.

         Non può essere applicato alle proprietà del ruolo che corrispondono ai collegamenti delle relazioni. Utilizzare invece `ElementAdded` per monitorare la relazione di dominio.

    -   `ElementDeleted` -attivata dopo un elemento del modello, relazione, forma o il connettore è stato eliminato. È comunque possibile accedere i valori delle proprietà dell'elemento, ma non avrà Nessuna relazione agli altri elementi.

2.  Aggiungere una definizione di classe parziale per *YourDsl * * * DocData** in un file di codice separato nella **DslPackage** progetto.

3.  Scrivere il codice dell'evento come un metodo, come nell'esempio seguente. Può essere `static`, a meno che non si desidera accedere a `DocData`.

4.  Eseguire l'override `OnDocumentLoaded()` per registrare il gestore. Se si dispone di più di un gestore, è possibile registrare tutti nella stessa posizione.

Il percorso del codice di registrazione non critico. `DocView.LoadView()` è un percorso alternativo.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Utilizzare gli eventi per gli adeguamenti annullabili nell'archivio

Gli eventi di archiviazione non vengono utilizzati in genere per la propagazione delle modifiche all'interno dell'archivio, perché il gestore dell'evento viene eseguito dopo che viene eseguito il commit della transazione. Utilizzare invece una regola di archivio. Per ulteriori informazioni, vedere [propagare le modifiche all'interno di modello di regole](../modeling/rules-propagate-changes-within-the-model.md).

Tuttavia, è possibile utilizzare un gestore eventi per eseguire aggiornamenti aggiuntivi, l'archivio, se si desidera che l'utente la possibilità di annullare gli aggiornamenti aggiuntivi separatamente dall'evento originale. Si supponga, ad esempio, di caratteri minuscoli convenzione abituale per i titoli degli album. È possibile scrivere un gestore eventi di archivio che corregge il titolo in lettere minuscole, dopo che l'utente ha digitato in lettere maiuscole. Ma l'utente potrebbe usare il comando Annulla per annullare la correzione, ripristino i caratteri maiuscoli. Modifica dell'utente rimuove una seconda fase di rollback.

Al contrario, se si scrive una regola di archivio per eseguire la stessa operazione, la modifica dell'utente e la correzione sarebbe nella stessa transazione, in modo che l'utente non è riuscito ad annullare la regolazione senza perdere le modifiche originali.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Se si scrive un evento che aggiorna l'archivio:

-   Utilizzare `store.InUndoRedoOrRollback` per evitare di apportare modifiche agli elementi del modello di annullamento. Il gestore delle transazioni verrà impostato tutti gli elementi nell'archivio allo stato originale.

-   Utilizzare `store.InSerializationTransaction` per evitare di apportare modifiche, mentre il modello viene caricato dal file.

-   Le modifiche provochino ulteriormente gli eventi deve essere attivata. Assicurarsi di evitare un ciclo infinito.

## <a name="store-event-types"></a>Archiviare i tipi di evento

Ogni tipo di evento corrisponde a una raccolta in Store.EventManagerDirectory. È possibile aggiungere o rimuovere i gestori eventi in qualsiasi momento, ma è normale per aggiungerle quando il documento viene caricato.

|`EventManagerDirectory` Nome della proprietà|È stata eseguita quando|
|-------------------------------------------|-------------------|
|ElementAdded|Viene creata un'istanza di classe di dominio, relazione di dominio, forma, connettore o diagramma.|
|ElementDeleted|Un elemento del modello è stato rimosso dalla directory degli elementi dell'archivio e non è più l'origine o la destinazione di una relazione. L'elemento non viene eliminata dalla memoria, ma verrà mantenuto in caso di un annullamento future.|
|ElementEventsBegun|Chiamato alla fine di una transazione esterna.|
|ElementEventsEnded|Richiamato quando sono stati elaborati tutti gli altri eventi.|
|ElementMoved|Un elemento del modello è stato spostato dalla partizione di un archivio a un altro.<br /><br /> Non è correlato alla posizione di una forma nel diagramma.|
|ElementPropertyChanged|Il valore di una proprietà di dominio è stato modificato. Questa operazione venga eseguita solo se i valori nuovi e precedenti sono uguali.|
|RolePlayerChanged|Uno dei due ruoli (estremità) di una relazione fa riferimento a un nuovo elemento.|
|RolePlayerOrderChanged|In un ruolo con molteplicità maggiore di 1, è stata modificata la sequenza di collegamenti.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Vedere anche

- [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
- [Codice di esempio: diagrammi circuito](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]