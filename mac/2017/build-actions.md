---
title: Azioni di compilazione
description: Questo articolo descrive le varie azioni di compilazione che possono essere usate per i progetti C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d55ab6aea15dbad7f1cbd718136fba261dfa1c69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74983256"
---
# <a name="build-actions"></a>Azioni di compilazione

Tutti i file di un progetto Visual Studio per Mac possiedono un'azione di compilazione, che controlla cosa accade al file durante una compilazione. Questo comportamento può essere impostato facendo clic con il pulsante destro del mouse sul file e scegliendo **Azione di compilazione**, come illustrato di seguito:

![Selezione dell'azione di compilazione da Esplora soluzioni](media/projects-and-solutions-image1.png)

Ecco alcune azioni di compilazione comuni per progetti C#:

* **Nessuna**: il file non fa parte della compilazione in alcun modo, è incluso nel progetto solo per facilitarne l'accesso dall'IDE.
* **Compilazione**: il file verrà passato al compilatore C# come file di origine.
* **EmbeddedResource**: il file verrà passato al compilatore C# come una risorsa da incorporare nell'assembly. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), sarà quindi possibile usare lo spazio dei nomi `System.Reflection` per leggere il file dall'assembly.
* **Contenuto**: per i progetti ASP.NET, questi file vengono inclusi come parte del sito quando questo viene distribuito. Per i progetti Xamarin.iOS e Xamarin.Mac, sono inclusi nel bundle dell'app.

È possibile selezionare più file in Esplora soluzioni. Ciò consente di impostare l'azione di compilazione per più file in una sola volta.

Sono anche disponibili azioni di compilazione per progetti specifici. Per i progetti Xamarin.iOS esiste l'azione di compilazione **BundleResource**, che aggiunge il file al bundle dell'app. Per informazioni sulle azioni di compilazione specifiche per Xamarin.Android, vedere la guida al [processo di compilazione](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

## <a name="see-also"></a>Vedere anche

- [Azioni di compilazione (Visual Studio in Windows)](/visualstudio/ide/build-actions)