---
title: Panoramica del data binding WPF con LINQ to XML | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 44f8e1bde92cec70264beea8e9a62205ec0c2e8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>Panoramica del data binding WPF con LINQ to XML
In questo argomento vengono brevemente descritte le funzionalità dinamiche di associazione dati dello spazio dei nomi <xref:System.Xml.Linq>. Queste funzionalità possono essere usate come origine dati per gli elementi dell'interfaccia utente in WPF (Windows Presentation Foundation).  
  
## <a name="xaml-and-linq-to-xml"></a>XAML e LINQ to XML  
 XAML (Extensible Application Markup Language) è un sottolinguaggio XML creato da Microsoft per supportare le tecnologie .NET Framework 3.0. Viene usato in WPF per rappresentare elementi dell'interfaccia utente e funzionalità correlate, ad esempio eventi e data binding. In Windows Workflow Foundation, XAML viene usato per rappresentare la struttura del programma, ad esempio il controllo del programma (*flussi di lavoro*). XAML consente la separazione di aspetti dichiarativi di una tecnologia dal codice procedurale correlato che definisce il comportamento più personalizzato di un programma.  
  
 XAML e LINQ to XML possono interagire in due modi:  
  
-   Poiché i file XAML corrispondono a codice XML ben formato, è possibile eseguirvi query e modificarli tramite tecnologie XML quale LINQ to XML.  
  
-   Poiché le query LINQ to XML rappresentano un'origine dati, possono essere usate come origine dati per l'associazione dati per gli elementi dell'interfaccia utente WPF.  
  
 In questa documentazione viene descritto il secondo scenario.  
  
## <a name="data-binding-in-the-windows-presentation-foundation"></a>Associazione dati in Windows Presentation Foundation  
 L'associazione dati WPF consente a un elemento dell'interfaccia utente di associare una delle proprietà a un'origine dati. Un semplice esempio di questo comportamento è <xref:System.Windows.Controls.Label> il cui testo presenta il valore di una proprietà pubblica in un oggetto definito dall'utente. L'associazione dati WPF si basa sui componenti seguenti:  
  
|Componente|Descrizione|  
|---------------|-----------------|  
|Destinazione di associazione|Elemento dell'interfaccia utente da associare all'origine dati. Gli elementi visivi di WPF sono derivati dalla classe <xref:System.Windows.UIElement>.|  
|Proprietà di destinazione|*Proprietà di dipendenza* della destinazione di associazione che riflette il valore dell'origine del data binding. Le proprietà della dipendenza sono supportate direttamente dalla classe <xref:System.Windows.DependencyObject>, da cui deriva <xref:System.Windows.UIElement>.|  
|Origine di associazione|Oggetto di origine per uno o più valori forniti all'elemento dell'interfaccia utente per la presentazione. In WPF sono automaticamente supportati i seguenti tipi di origini di associazione: oggetti CLR, oggetti dati ADO.NET, dati XML (provenienti da query XPath o LINQ to XML) o un altro oggetto <xref:System.Windows.DependencyObject>.|  
|Percorso di origine|Proprietà dell'origine di associazione che si risolve nel valore o set di valori a cui deve essere associata.|  
  
 Quello della proprietà della dipendenza è un concetto specifico di WPF che rappresenta una proprietà di un elemento dell'interfaccia utente elaborato dinamicamente. Ad esempio, le proprietà di dipendenza includono spesso valori predefiniti o specificati da un elemento padre. Queste proprietà speciali sono supportate da istanze della classe <xref:System.Windows.DependencyProperty> e non da campi come con proprietà standard. Per altre informazioni, vedere [Panoramica sulle proprietà di dipendenza](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
### <a name="dynamic-data-binding-in-wpf"></a>Data binding dinamico in WPF  
 Per impostazione predefinita, il data binding si verifica solo quando viene inizializzato l'elemento dell'interfaccia utente di destinazione. Questo comportamento è denominato associazione *unica*. Nella maggior parte dei casi, si tratta di una soluzione insufficiente. In genere una soluzione di data binding richiede la propagazione dinamica delle modifiche in fase di esecuzione in una delle seguenti modalità:  
  
-   L'associazione *unidirezionale* determina la propagazione automatica delle modifiche apportate a un lato. In generale, le modifiche apportate all'origine si riflettono nella destinazione, ma può essere utile anche l'inverso.  
  
-   Nell'associazione *bidirezionale* le modifiche apportate all'origine vengono automaticamente propagate alla destinazione e viceversa.  
  
 Affinché si verifichi l'associazione unidirezionale o bidirezionale, è necessario che l'origine implementi un meccanismo di notifica delle modifiche, ad esempio tramite l'implementazione dell'interfaccia <xref:System.ComponentModel.INotifyPropertyChanged> o l'uso di un modello *PropertyNameChanged* per ogni proprietà supportata.  
  
 Per altre informazioni sul data binding in WPF, vedere [Associazione dati (WPF)](/dotnet/framework/wpf/data/data-binding-wpf).  
  
## <a name="dynamic-properties-in-linq-to-xml-classes"></a>Proprietà dinamiche nelle classi LINQ to XML  
 La maggior parte delle classi LINQ to XML non è qualificata come origine dati dinamica WPF appropriata. Alcune delle informazioni più utili sono disponibili solo tramite metodi, non tramite proprietà, e le proprietà di queste classi non implementano le notifiche delle modifiche. Per supportare il data binding WPF, in LINQ to XML viene esposto un set di *proprietà dinamiche*.  
  
 Queste proprietà dinamiche sono proprietà speciali di runtime che duplicano la funzionalità dei metodi e delle proprietà esistenti nelle classi <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>. Sono state aggiunte a queste classi unicamente per consentirne l'uso come origini dati dinamiche per WPF. Per soddisfare questa esigenza, tutte queste proprietà dinamiche implementano le notifiche delle modifiche. Un riferimento dettagliato per queste proprietà dinamiche è presentato nella sezione successiva, [Proprietà dinamiche di LINQ to XML](../designers/linq-to-xml-dynamic-properties.md).  
  
> [!NOTE]
>  Molte delle proprietà pubbliche standard, disponibili nelle varie classi nello spazio dei nomi <xref:System.Xml.Linq>, possono essere usate per l'associazione dati unica. Tenere presente, tuttavia, in questo schema non verrà aggiornata né l'origine né la destinazione.  
  
### <a name="accessing-dynamic-properties"></a>Accesso alle proprietà dinamiche  
 Non è possibile accedere alle proprietà dinamiche delle classi <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement> come alle proprietà standard. Ad esempio, nei linguaggi conformi a CLR quale C# non è possibile:  
  
-   Accedere direttamente a queste proprietà in fase di compilazione. Le proprietà dinamiche sono invisibili per il compilatore e per la funzionalità IntelliSense di Visual Studio.  
  
-   Individuare o accedere a queste proprietà tramite reflection .NET. Anche in fase di esecuzione, non si tratta di proprietà nel senso CLR di base.  
  
 In C# è possibile accedere alle proprietà dinamiche solo in fase di esecuzione tramite le funzionalità rese disponibili dallo spazio dei nomi <xref:System.ComponentModel>.  
  
 Al contrario, in un'origine XML è possibile accedere alle proprietà dinamiche tramite una notazione diretta nel seguente formato:  
  
```  
<object>.<dynamic-property>  
```  
  
 Le proprietà dinamiche per queste due classi si risolvono in un valore che può essere usato direttamente o in un indicizzatore che deve essere fornito con un indice per ottenere il valore o la raccolta di valori risultante. Nell'ultimo caso la sintassi ha il seguente formato:  
  
```  
<object>.<dynamic-property>[<index-value>]  
```  
  
 Per altre informazioni, vedere [Proprietà dinamiche di LINQ to XML](../designers/linq-to-xml-dynamic-properties.md).  
  
 Per implementare l'associazione dinamica WPF, le proprietà dinamiche verranno usate con le funzionalità fornite dallo spazio dei nomi <xref:System.Windows.Data>, in particolare la classe <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Data binding WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Proprietà dinamiche in LINQ to XML](../designers/linq-to-xml-dynamic-properties.md)   
 [XAML in WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)   
 [Associazione dati (WPF)](/dotnet/framework/wpf/data/data-binding-wpf)   
 [Utilizzo dei markup del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=98685)