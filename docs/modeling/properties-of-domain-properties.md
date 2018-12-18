---
title: "Le proprietà del dominio | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7d964eb9f0dcabdb8050074121d094245aca9bb7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-domain-properties"></a>Proprietà delle proprietà di dominio
Oggetto *proprietà dominio* è una funzionalità di un elemento del modello che può contenere un valore. Ad esempio, la classe di dominio `Person` potrebbe includere le proprietà `Name` e `BirthDate`. Nella definizione DSL, le proprietà di dominio sono elencate nella casella della classe di dominio sul diagramma e sotto la classe di dominio in DSL Explorer. Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  Il termine"proprietà" ha due utilizzi. Oggetto *proprietà dominio* è una funzionalità che si definisce una classe di dominio. Al contrario, dispone di molti elementi di un linguaggio DSL *proprietà*, elencate nella **proprietà** finestra nella definizione del linguaggio DSL. Ad esempio, ogni proprietà di dominio dispone di un set di proprietà descritte in questo argomento.  
  
 In fase di esecuzione, quando un utente crea un'istanza della classe di dominio, i valori delle proprietà di dominio sono visibili nella finestra Proprietà e possono essere visualizzati sulle forme.  
  
 La maggior parte delle proprietà di dominio è implementata come comuni proprietà CLR. Tuttavia, dal punto di vista della programmazione, le proprietà di dominio sono caratterizzate da funzionalità più avanzate rispetto alle proprietà del programma comuni.  
  
-   È possibile definire regole ed eventi per monitorare lo stato di una proprietà. Per ulteriori informazioni, vedere [propagazione delle modifiche e risposta agli](../modeling/responding-to-and-propagating-changes.md).  
  
-   Le transazioni contribuiscono a prevenire stati incoerenti. Per ulteriori informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Quando si seleziona una Proprietà di dominio in un diagramma o in DSL Explorer, nella Finestra Proprietà vengono visualizzati gli elementi seguenti. Per ulteriori informazioni sull'utilizzo di questi elementi, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Proprietà|Descrizione|Valore predefinito|  
|--------------|-----------------|-------------------|  
|**Descrizione**|Descrizione usata per documentare l'interfaccia utente della finestra di progettazione generata.|\<Nessuno >|  
|**Nome visualizzato**|Nome che verrà visualizzato nella finestra di progettazione generata per questa proprietà di dominio. Può contenere spazi e punteggiatura, ad esempio "Song Title".|\<Nessuno >|  
|**Provider di nomi di elemento**|Applicabile solo se `Is Element Name` è stato impostato su `true`. È possibile scrivere codice per assegnare un nome a un nuovo elemento in una classe di dominio, effettuando un override del comportamento predefinito.<br /><br /> In un file di codice nel progetto DSL, creare una classe derivata da <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> In DSL Explorer fare quindi clic con il pulsante destro del mouse sulla radice del DSL e scegliere Aggiungi tipo esterno. Immettere il nome della classe.<br /><br /> Selezionare di nuovo questa proprietà di dominio e selezionare il nome della classe nell'elenco a discesa.|\<Nessuno >|  
|**Modificatore di accesso get**|Livello di accesso della classe di dominio (`public` o `internal`). In tal modo viene controllato l'ambito nel quale il codice programma può accedere alla proprietà.|`public`|  
|**Parola chiave della Guida**|La parola chiave facoltativa usata per indicizzare la guida F1 per questa proprietà di dominio.|\<Nessuno >|  
|**Può essere esaminato**|Se `True`, la proprietà di dominio è visualizzata dall'utente nella finestra delle proprietà quando i modelli di questo DSL sono aperti.<br /><br /> Se `False`, la proprietà di dominio è nascosta nell'interfaccia utente.<br /><br /> Se si desidera impostare la proprietà dominio visibili ma in sola lettura, impostare **è dell'interfaccia utente di sola lettura**.|`True`|  
|**Nome di elemento**|Se `True`, questa proprietà di dominio verrà visualizzata come nome del relativo elemento modello in DSL Explorer.<br /><br /> I nuovi elementi modello riceveranno un valore predefinito univoco per questa proprietà. Se si desidera controllare la modalità di generazione di questi valori, impostare **il Provider di nomi di elemento**.|`False`|  
|**Interfaccia utente in sola lettura**|Se `True`, il valore della proprietà di dominio non può essere modificato tramite l'interfaccia utente. Può comunque essere impostato da programmi e sarà visibile nella finestra Proprietà.<br /><br /> Se si desidera nascondere le proprietà del dominio da parte dell'utente, impostare **è esplorabile**. Se si desidera controllare l'accesso tramite i programmi, impostare **modificatore di accesso Setter**.|`False`|  
|**Kind**|Il tipo di proprietà di dominio (`Normal`, `Calculated` o `CustomStorage`). Per ulteriori informazioni, vedere [calcolate e le proprietà di archiviazione personalizzato](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Name**|Nome di questa proprietà di dominio. Deve essere un identificatore valido, ad esempio **SongTitle**.|\<Nessuno >|  
|**Note**|Note informali associate alla proprietà di dominio.|\<Nessuno >|  
|**Modificatore di accesso Setter**|Modificatore di accesso per il metodo Set. Consente di controllare l'ambito nel quale il codice programma può impostare la proprietà.|`public`|  
|**Type**|Tipo di proprietà. Per aggiungere all'elenco dei tipi disponibili, la radice del linguaggio DSL in Esplora DSL di mouse e scegliere **aggiungere tipo esterno**.|`String`|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)