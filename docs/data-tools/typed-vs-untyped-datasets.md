---
title: Tipizzati e DataSet non tipizzati
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5819a208a54a5a4235330216e46b5e17f1260fa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="typed-vs-untyped-datasets"></a>Tipizzati e DataSet non tipizzati
Un dataset tipizzato è un set di dati prima di tutto è derivata dalla base <xref:System.Data.DataSet> classe e quindi utilizza le informazioni dal **Progettazione Dataset**, che viene archiviato in un file XSD, per generare un nuovo fortemente tipizzate classe dataset. Informazioni dello schema (tabelle, colonne e così via) viene generate e compilate in questa nuova classe dataset come un set di proprietà e oggetti di primaria importanza. Poiché un dataset tipizzato erediterà dalla base <xref:System.Data.DataSet> (classe), la classe tipizzata si presuppone che tutte le funzionalità del <xref:System.Data.DataSet> e può essere utilizzata con metodi che accettano un'istanza di un <xref:System.Data.DataSet> classe come parametro.

 Un set di dati non tipizzati, invece, dispone di alcuno schema di incorporata corrispondente. Come in un dataset tipizzato, un dataset tipizzato contiene tabelle, colonne e così via, ma vengono esposti solo come raccolte. (Tuttavia, dopo aver creato manualmente le tabelle e altri elementi di dati in un dataset non tipizzato, è possibile esportare la struttura del set di dati come uno schema tramite il set di dati <xref:System.Data.DataSet.WriteXmlSchema%2A> metodo.)

## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Accesso ai dati nei dataset tipizzati e non tipizzati
 La classe di un dataset tipizzato presenta un modello a oggetti in cui le relative proprietà hanno i nomi effettivi delle tabelle e colonne. Ad esempio, se si lavora con un dataset tipizzato, è possibile fare riferimento una colonna utilizzando codice analogo al seguente:

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 Al contrario, se si lavora con un set di dati non tipizzati, è l'equivalente del codice:

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 Accesso tipizzato non solo più facile da leggere, ma anche completamente supportata da IntelliSense nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Editor di codice**. Oltre a essere più facile lavorare con, la sintassi per il dataset tipizzato consente un controllo in fase di compilazione, riducendo notevolmente la possibilità di errori nell'assegnazione dei valori ai membri del set di dati. Se si modifica il nome di una colonna del <xref:System.Data.DataSet> classe e quindi compilare l'applicazione, viene visualizzato un errore di compilazione. Facendo doppio clic su errore di compilazione nel **elenco attività**, è possibile passare direttamente alla riga o le righe di codice che fa riferimento il nome della colonna precedente. Accesso a tabelle e colonne in una classe tipizzata set di dati è leggermente più veloce in fase di esecuzione anche quanto viene determinato in fase di compilazione, non tramite le raccolte in fase di esecuzione.

 Anche se i dataset tipizzati offrono molti vantaggi, un set di dati non tipizzato è utile in diverse circostanze. Lo scenario più ovvio è quando è disponibile per il set di dati alcuno schema. Questo potrebbe verificarsi, ad esempio, se l'applicazione interagisce con un componente che restituisce un set di dati, ma non si conosce in anticipo qual è la struttura. Analogamente, vi sono casi quando si lavora con i dati che non dispone di una struttura statica e prevedibile. In tal caso, è poco pratica per utilizzare un dataset tipizzato, perché è necessario rigenerare la classe dataset tipizzato con ogni modifica della struttura di dati.

 Esistono più in generale, più volte quando è possibile creare un set di dati in modo dinamico senza la necessità di uno schema disponibile. In tal caso, il set di dati è semplicemente una struttura semplice in cui è possibile mantenere informazioni, purché i dati possono essere rappresentati in modo relazionale. Allo stesso tempo, è possibile usufruire di funzionalità del set di dati, ad esempio la possibilità di serializzare le informazioni da passare a un altro processo o per scrivere un file XML.

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati](../data-tools/dataset-tools-in-visual-studio.md)