---
title: Installazione di R Tools per Visual Studio | Microsoft Docs
description: Come installare R Tools per Visual Studio in Visual Studio 2017 e Visual Studio 2015, comprese le installazioni offline.
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
dev_langs:
- R
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: c4ca5a7fea1a84c4f4a38396daebd3e01412d9d7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Come installare R Tools per Visual Studio

Contenuto dell'articolo:

- [Versioni supportate di Visual Studio](#supported-versions-of-visual-studio)
- [Installazione di RTVS in Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Installazione di RTVS in Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Installazione offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Dopo aver installato R Tools, si potrebbe voler configurare Visual Studio per un layout Data Scientist ottimizzato, come descritto nell'articolo [Options](options-for-r-tools-in-visual-studio.md) (Opzioni).

## <a name="supported-versions-of-visual-studio"></a>Versioni supportate di Visual Studio

R Tools per Visual Studio (RTVS) è supportato in Windows con le edizioni Community (gratuita), Professional ed Enterprise di [Visual Studio 2017](https://www.visualstudio.com/downloads/) e [Visual Studio 2015 Update 3 (o versioni successive)](http://go.microsoft.com/fwlink/?LinkId=691129) (download diretto).

RTVS non è attualmente supportato in Visual Studio per Mac.

RTVS non viene installato se si ha solo Visual Studio Shell incluso in prodotti come Visual Studio Test Professional e SQL Server Management Studio. Visual Studio Shell non ha i componenti necessari per RTVS.

## <a name="installing-rtvs-in-visual-studio-2017"></a>Installazione di RTVS in Visual Studio 2017

1. Eseguire il programma di installazione di Visual Studio. Se Visual Studio non è ancora installato, vedere la pagina [Download](https://www.visualstudio.com/downloads/). In Windows 7 verificare che il programma di installazione sia aggiornato in modo da visualizzare Visual Studio versione *15.2 build 26430.12* o versione successiva.

1. Selezionare il carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati**:

    ![Carico di lavoro delle applicazioni analitiche e di analisi scientifica dei dati in VS2017](media/installation-data-science-workload.png)

1. Impostare tutte le opzioni aggiuntive sul lato destro con lo stesso nome del carico di lavoro. Per impostazione predefinita, questo carico di lavoro include il supporto per F# e Python. Per R, i requisiti minimi sono il **supporto del linguaggio R**, il **supporto del runtime per lo sviluppo R** e **Microsoft R Client**.

RTVS viene installato in: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` in cui `<version>` è generalmente `2017` e `<edition>` è `Community`, `Professional` o `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Installazione di RTVS in Visual Studio 2015

Con Visual Studio 2015, è necessario installare separatamente un interprete di R e R Tools.

### <a name="install-an-r-interpreter"></a>Installare un interprete di R

RTVS richiede un'installazione a 64 bit di R versione 3.2.1 o successiva da una o da più origini seguenti:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open e CRAN R consentono l'uso di più versioni affiancate. Microsoft R Client supporta solo una versione e usa sempre la versione installata più recentemente.

### <a name="install-the-r-tools"></a>Installare R Tools

Scaricare RTVS corrente per Visual Studio 2015 da [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS verifica la disponibilità di una versione appropriata di Visual Studio e consente anche di installare un interprete di R, se non è già installato.

> [!Note]
> Il programma di installazione autonomo RTVS funziona solo con Visual Studio 2015. Per Visual Studio 2017, installare il supporto R tramite il [carico di lavoro delle applicazioni analitiche e di analisi scientifica dei dati](#installing-rtvs-in-visual-studio-2017) come descritto in precedenza.

RTVS per Visual Studio 2015 è installato:`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Installazione offline di Visual Studio e RTVS

L'installazione offline è utile per i computer che non sono connessi a Internet:

1. Seguire le istruzioni per creare un programma di installazione offline per la propria versione di Visual Studio: 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Per Visual Studio 2015, scaricare i programmi di installazione offline RTVS da [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) e [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip). 

1. Installare Visual Studio e RTVS da un programma di installazione offline.

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva a R](getting-started-with-r.md)
- [R Tools sample projects](getting-started-samples.md) (Progetti di esempio di R Tools)
- [Informazioni di supporto](getting-started-help.md)
- [Option settings](options-for-r-tools-in-visual-studio.md) (Impostazioni delle opzioni)
- [Microsoft Machine Learning Server (in precedenza, R Server)](/machine-learning-server/)