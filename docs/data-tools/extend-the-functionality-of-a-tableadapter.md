---
title: Estendere la funzionalità di un oggetto TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9b5884ff140097010c90fbf2208fecd95980f2fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estendere la funzionalità di un oggetto TableAdapter
È possibile estendere la funzionalità di un oggetto TableAdapter aggiungendo codice al file di classe parziale dell'oggetto TableAdapter.

 Il codice che definisce un oggetto TableAdapter viene rigenerato quando vengono apportate modifiche all'oggetto TableAdapter nel **Progettazione Dataset**, o quando una procedura guidata consente di modificare la configurazione di un oggetto TableAdapter. Per impedire che il codice da eliminare durante la rigenerazione di un oggetto TableAdapter, aggiungere codice al file di classe parziale dell'oggetto TableAdapter.

 Classi parziali consentono al codice per una classe specifica da dividere tra più file fisici. Per ulteriori informazioni, vedere [parziale](/dotnet/visual-basic/language-reference/modifiers/partial) o [parziale (tipo)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Individuare gli oggetti TableAdapter nel codice
 Mentre gli oggetti TableAdapter sono progettate con la **Progettazione Dataset**, le classi TableAdapter generate non sono classi annidate di <xref:System.Data.DataSet>. Gli oggetti TableAdapter si trovano in uno spazio dei nomi in base al nome del set di dati associato dell'oggetto TableAdapter. Ad esempio, se l'applicazione contiene un set di dati denominato `HRDataSet`, gli oggetti TableAdapter potrebbe trovarsi nel `HRDataSetTableAdapters` dello spazio dei nomi. (La convenzione di denominazione segue questo modello: *DatasetName* + `TableAdapters`).

 Nell'esempio seguente si presuppone un oggetto TableAdapter denominato `CustomersTableAdapter`in un progetto con `NorthwindDataSet`.

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Per creare una classe parziale per un oggetto TableAdapter

1.  Aggiungere una nuova classe al progetto selezionando il **progetto** menu e selezionando **Aggiungi classe**.

2.  Assegnare alla classe il nome `CustomersTableAdapterExtended`.

3.  Selezionare **aggiungere**.

4.  Sostituire il codice con il nome di classe parziale per il progetto e un spazio dei nomi corretto come indicato di seguito:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)