---
title: "Proprietà dinamiche in LINQ to XML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bf92d22b3c27d23fa90b6d9be13cf4fa6604384a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-xml-dynamic-properties"></a>Proprietà dinamiche in LINQ to XML
Contenuto della sezione vengono fornite informazioni di riferimento relative alle proprietà dinamiche di LINQ to XML. In particolare, queste proprietà vengono esposte dalle classi <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>, incluse nello spazio dei nomi <xref:System.Xml.Linq>.  
  
 Come illustrato nell'argomento [Panoramica del data binding di WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), ogni proprietà dinamica è equivalente a una proprietà o a un metodo pubblico della stessa classe. Questi membri standard devono essere usati per la maggior parte degli scopi. Le proprietà dinamiche vengono fornite specificamente per gli scenari di data binding LINQ to XML. Per altre informazioni sui membri standard di queste classi, vedere gli argomenti di riferimento <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>.  
  
 Relativamente ai valori risolti, le proprietà dinamiche descritte in questa sezione rientrano in due categorie:  
  
-   Proprietà semplici, ad esempio le proprietà `Value` nelle classi <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>, che vengono risolte in un singolo valore.  
  
-   Valori indicizzati, ad esempio le proprietà [Elements](../designers/elements-xelement-dynamic-property.md) e [Descendants](../designers/descendants-xelement-dynamic-property.md) di <xref:System.Xml.Linq.XElement>, che vengono risolti in un tipo di indicizzatore. Affinché i tipi di indicizzatori vengano risolti nel valore o nella raccolta desiderata, è necessario passare un parametro di nome espanso.  
  
 Tutte le proprietà dinamiche che restituiscono un valore indicizzato di tipo <xref:System.Collections.Generic.IEnumerable%601> usano l'esecuzione posticipata. Per altre informazioni sull'esecuzione posticipata, vedere [Introduzione alle query LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Proprietà dinamiche della classe XAttribute](../designers/xattribute-class-dynamic-properties.md)|Vengono forniti dettagli sulle proprietà dinamiche esposte dalla classe <xref:System.Xml.Linq.XAttribute>.|  
|[Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)|Vengono forniti dettagli sulle proprietà dinamiche esposte dalla classe <xref:System.Xml.Linq.XElement>.|  
  
## <a name="reference"></a>Riferimenti  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Vedere anche  
 [Data binding WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Panoramica di associazioni dati WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduzione alle query LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)