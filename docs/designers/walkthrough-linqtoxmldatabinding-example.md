---
title: 'Procedura dettagliata: Esempio LinqToXmlDataBinding | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bc78fd4331839ce1a55253a719c40f8b19dea491
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Procedura dettagliata: Esempio LinqToXmlDataBinding
In questa procedura dettagliata viene descritto l'esempio LinqToXmlDataBinding e vengono illustrato parte del contenuto più interessante dei due file di origine principali, ovvero L2DBForm.xaml e L2DBForm.xaml.cs.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Prima di leggere questa procedura dettagliata, è consigliabile compilare ed eseguire l'applicazione LinqToXmlDataBinding come descritto in [Procedura: Compilare ed eseguire l'esempio LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).  
  
## <a name="remarks"></a>Note  
 LinqToXmlDataBinding è un'applicazione di Windows Presentation Foundation (WPF) composta da file di origine C# e XAML. Contiene un documento XML incorporato che definisce un elenco di libri e consente all'utente di visualizzare, aggiungere, eliminare e modificare queste voci. È costituita dai due file di origine principali seguenti:  
  
-   L2DBForm.xaml: contiene il codice della dichiarazione XAML per l'interfaccia utente della finestra principale. Include inoltre una sezione di risorse della finestra in cui vengono definiti un provider di dati e un documento XML incorporato per gli elenchi di libri.  
  
-   L2DBForm.xaml.cs: contiene i metodi di inizializzazione e gestione eventi associati all'interfaccia utente.  
  
 La finestra principale è divisa nelle quattro sezioni di interfaccia utente verticali descritte di seguito:  
  
-   **XML**: visualizza l'origine XML non elaborata dell'elenco di libri incorporato.  
  
-   **Book List**: visualizza le voci relative ai libri come testo standard e consente all'utente di selezionare ed eliminare singole voci.  
  
-   **Edit Selected Book**: consente all'utente di modificare i valori associati alla voce attualmente selezionata.  
  
-   **Add New Book**: consente di creare una nuova voce in base ai valori immessi dall'utente.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Codice sorgente di L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Vengono forniti il contenuto e la descrizione del codice XAML del file L2DBForm.xaml.|  
|[Codice sorgente di L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Vengono forniti il contenuto e la descrizione del codice sorgente C# del file L2DBForm.xaml.cs.|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di associazione dati di WPF con LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Procedura: Compilare ed eseguire l'esempio LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)