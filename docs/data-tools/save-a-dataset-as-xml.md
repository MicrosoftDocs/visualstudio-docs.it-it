---
title: Salvare un dataset come XML | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c6176b1d7e9f18ce08fddf21f199cd21304ca8a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="save-a-dataset-as-xml"></a>Salvataggio di un set di dati in formato XML
I dati XML in un set di dati sono accessibili chiamando i metodi XML disponibili nel set di dati. Per salvare i dati in formato XML, è possibile chiamare il <xref:System.Data.DataSet.GetXml%2A> metodo o <xref:System.Data.DataSet.WriteXml%2A> metodo di un <xref:System.Data.DataSet>.  
  
 La chiamata di <xref:System.Data.DataSet.GetXml%2A> metodo restituisce una stringa che contiene i dati da tutte le tabelle di dati nel set di dati in formato XML.  
  
 La chiamata di <xref:System.Data.DataSet.WriteXml%2A> metodo invia i dati in formato XML in un file specificato.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Per salvare i dati in un set di dati come XML in una variabile  
  
-   Il <xref:System.Data.DataSet.GetXml%2A> metodo restituisce un <xref:System.String>. Ciò significa che si dichiara una variabile di tipo <xref:System.String> e assegna il risultato di <xref:System.Data.DataSet.GetXml%2A> (metodo).  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Per salvare i dati in un set di dati come XML in un file  
  
-   Il <xref:System.Data.DataSet.WriteXml%2A> metodo dispone di diversi overload. Il codice seguente viene illustrato come salvare i dati in un file. Dichiarare una variabile e assegnare un percorso valido in cui salvare il file.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)