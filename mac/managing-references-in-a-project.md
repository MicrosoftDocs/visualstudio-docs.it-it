---
title: Gestione dei riferimenti in un progetto
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 30f6c99c6ac827b7da94fd228a7034e9ce0b0fac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="managing-references-in-a-project"></a>Gestione dei riferimenti in un progetto

Visual Studio per Mac offre tre modi per aggiungere ulteriori riferimenti al progetto:

![Riferimenti al progetto](media/projects-and-solutions-image10.png)

Questi sono:

* Riferimenti
* Pacchetti NuGet (aggiunti tramite la cartella Pacchetti)
* Componenti

A qualsiasi progetto è anche possibile aggiungere riferimenti Web e riferimenti nativi.

## <a name="assembly-references"></a>Riferimenti ad assembly

Ogni framework in Xamarin include più di una dozzina di assembly. Non a tutti i pacchetti di assembly viene fatto riferimento nel progetto per impostazione predefinita. 

Per modificare i pacchetti a cui viene fatto riferimento nel progetto, usare la finestra di dialogo _Modifica riferimenti_, che è possibile visualizzare facendo doppio clic sulla cartella Riferimenti oppure scegliendo Modifica riferimenti tra le azioni del menu di scelta rapida:

![Finestra di dialogo dei riferimenti ad assembly](media/projects-and-solutions-image11.png)

Per informazioni sugli assembly disponibili per ogni framework Xamarin, vedere la guida agli [assembly disponibili](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet è il più diffuso strumento di gestione pacchetti per lo sviluppo .NET. Il supporto di NuGet di Visual Studio per Mac consente di cercare i pacchetti da aggiungere al progetto.

A tale scopo, fare clic con il pulsante destro del mouse sulla cartella **Pacchetto** nel riquadro della soluzione e scegliere Aggiungi pacchetti.

Per altre informazioni sull'uso di un pacchetto NuGet, vedere la procedura guidata [Inserimento di un pacchetto NuGet nel progetto](~/nuget-walkthrough.md).
