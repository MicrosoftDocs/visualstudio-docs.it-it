---
title: Azioni di compilazione
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 78b0e715ca44c613b6a7ee839c0656e301308588
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2017
---
# <a name="build-actions"></a>Azioni di compilazione 

A tutti i file di un progetto Visual Studio per Mac è associata un'azione di compilazione che controlla cosa accade al file durante la compilazione. Per impostare questa azione, è possibile fare clic con il pulsante destro del mouse sul file e scegliere **Azione di compilazione**, come illustrato di seguito:

![](media/projects-and-solutions-image1.png)

Ecco alcune azioni di compilazione comuni per progetti C#:

* **Nessuna**: il file non fa parte della compilazione in alcun modo, è incluso nel progetto solo per facilitarne l'accesso dall'IDE.
* **Compilazione**: il file verrà passato al compilatore C# come file di origine.
* **EmbeddedResource**: il file verrà passato al compilatore C# come una risorsa da incorporare nell'assembly. Sarà quindi possibile usare lo spazio dei nomi `System.Reflection` per leggere il file dall'assembly.
* **Contenuto**: per i progetti ASP.NET, questi file vengono inclusi come parte del sito quando questo viene distribuito. Per i progetti Xamarin.iOS e Xamarin.Mac sono inclusi nel bundle dell'app.

È possibile selezionare più file in Esplora soluzioni. Ciò consente di impostare l'azione di compilazione per più file in una sola volta.

Sono anche disponibili azioni di compilazione per progetti specifici. Per i progetti Xamarin.iOS, ad esempio, esiste l'azione di compilazione **BundleResource**, che aggiunge il file al bundle dell'app. Per informazioni sulle azioni di compilazione specifiche per Xamarin.Android, vedere la guida al [processo di compilazione](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions) in developer.xamarin.com.