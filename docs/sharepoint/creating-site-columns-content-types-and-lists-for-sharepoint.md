---
title: Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1025884bb23290c616a42a8cbbdcbad1d5814b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-site-columns-content-types-and-lists-for-sharepoint"></a>Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint
  Visual Studio fornisce modelli di elemento di progetto per numerosi elementi fondamentali di SharePoint, tra cui *Elenca* e *tipi di contenuto*, che può incorporare le colonne del sito (o  *campi*). Grazie alle nuove finestre di progettazione per i tipi di contenuto e gli elenchi, la creazione di questi elementi non è mai stata più facile.  
  
## <a name="site-columns"></a>Colonne del sito  
 Le colonne del sito sono uno degli elementi più semplici che si possono aggiungere a un progetto di SharePoint. Una colonna del sito rappresenta un tipo di dati, ad esempio un numero di telefono, un commento o il nome della città di un contatto in un elenco di contatti.  
  
 Grazie al nuovo modello per gli elementi di progetto delle colonne del sito, la creazione di queste colonne è più semplice rispetto alle versioni precedenti di Visual Studio. Dopo aver creato una nuova colonna del sito, è possibile modificare il codice XML nel file Elements.xml della colonna del sito per includere le informazioni desiderate, ad esempio il nome visualizzato, il tipo di dati e il gruppo nel quale si desidera venga visualizzata la colonna del sito in SharePoint. Per ulteriori informazioni sulle colonne del sito, vedere [Introduzione alle colonne](http://go.microsoft.com/fwlink/?LinkId=224996).  
  
## <a name="content-types-and-lists"></a>Tipi di contenuto ed elenchi  
 I tipi di contenuto e gli elenchi sono tra gli elementi più frequentemente utilizzati in SharePoint.  
  
 Con un tipo di contenuto vengono definiti i metadati, il flusso di lavoro e il comportamento di una categoria di elementi in un elenco o in una raccolta documenti di SharePoint. Ad esempio, è possibile creare un tipo di contenuto per le informazioni in un elenco di contatti o in un elenco di attività. In un tipo di contenuto del contatto possono essere incluse colonne come quelle relative al nome, alla posta elettronica, al numero di telefono e all'indirizzo. Un tipo di contenuto definito a livello di sito è indipendente da qualsiasi elenco o raccolta documenti nel sito. È possibile utilizzare lo stesso tipo di contenuto con diversi elenchi o raccolte documenti nel sito di SharePoint. È inoltre possibile utilizzare diversi tipi di contenuto nello stesso elenco o raccolta documenti.  
  
 Un elenco è una raccolta di informazioni in SharePoint condivisibile con altri utenti. Gli elenchi sono costituiti da righe di colonne contenenti i dati. Alcuni esempi di elenchi prevedono un elenco di attività, un elenco di contatti e un elenco di annunci.  
  
 Grazie alle nuove finestre di progettazione per il tipo di contenuto e per l'elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], la creazione dei tipi di contenuto e degli elenchi è molto più facile e intuitiva rispetto alle versioni precedenti di Visual Studio. Con l'interfaccia utente è possibile creare visivamente i tipi di contenuto e gli elenchi in modo comune, consentendo di ordinare e raggruppare i dati in elenchi e utilizzare le intestazioni di gruppo. Per ulteriori informazioni sui tipi di contenuto, vedere [tipi di contenuto](http://go.microsoft.com/fwlink/?LinkId=224997). Per ulteriori informazioni sugli elenchi, vedere [moduli elenco](http://go.microsoft.com/fwlink/?LinkId=224998) e [visualizzazioni elenco](http://go.microsoft.com/fwlink/?LinkId=224999).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Viene illustrato come creare colonne del sito utilizzate in un tipo di contenuto personalizzato. Il tipo di contenuto viene quindi utilizzato in un elenco personalizzato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Imparare a sviluppare in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  