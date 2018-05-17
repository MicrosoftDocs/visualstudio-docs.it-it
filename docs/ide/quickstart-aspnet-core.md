---
title: Usare Visual Studio per creare un'app Web ASP.NET Core in C#
description: Informazioni dettagliate su come creare un'app web ASP.NET Core in Visual Studio con C#.
ms.custom: mvc
ms.date: 10/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1b74f47201c706cbb4fe4a4f0eca647b350d9a72
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app Web ASP.NET Core

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio, sarà possibile creare una semplice Applicazione Web ASP.NET Core C#.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa, creare un progetto dell'applicazione Web ASP:NET Core. Il tipo di progetto viene specificato con i file di modello che costituiscono un'applicazione web funzionale, prima ancora di aggiungere alcun elemento.

1. Aprire Visual Studio 2017.

1. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual C#**, quindi selezionare **.NET Core**. Nel riquadro centrale, scegliere **Applicazione Web ASP.NET Core**, quindi scegliere **OK**.

     Se non viene visualizzata la categoria dei modelli di progetto **.NET Core** scegliere il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

     ![Carico di lavoro ASP.NET nel programma di installazione di Visual Studio](../ide/media/quickstart-aspnet-workload.png)

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** selezionare **ASP.NET Core 2.0** nel menu a discesa in alto. (Se non viene visualizzato **ASP.NET Core 2.0** nell'elenco, installarlo seguendo il collegamento **Download** visualizzato in una barra gialla nella parte superiore della finestra di dialogo.) Scegliere **OK**.

   ![Finestra di dialogo Nuova applicazione Web ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Nella barra degli strumenti **Esplora soluzioni** espandere la cartella **Pagine**, quindi scegliere **About.cshtml**(Informazioni su.cshtml) per aprirlo nell'editor. Questo file corrisponde a una pagina denominata **Informazioni su** nell'applicazione web.

1. Nell'editor scegliere `AboutModel` e quindi premere **F12** oppure scegliere **Vai a definizione** dal menu di scelta rapida (clic con il pulsante destro del mouse). Questo comando consente di passare alla definizione della classe C# `AboutModel`.

   ![Menu di scelta rapida Vai a definizione](../ide/media/quickstart-aspnet-gotodefinition.png)

1. Verranno eliminate le direttive `using` all'inizio del file usando un semplice collegamento. Scegliere una qualsiasi delle direttive using disattivate e una lampadina [Azioni rapide](../ide/quick-actions.md) verrà visualizzata sotto il punto di inserimento o nel margine sinistro. Scegliere la lampadina e quindi **Rimuovi istruzioni using non necessarie**.

     Le istruzioni using non necessarie vengono eliminate dal file.

1. Nel metodo `OnGet()` modificare il corpo con il codice seguente:

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. Verranno visualizzate due sottolineature ondulate in **Ambiente** e **Stringa**, poiché questi tipi non sono inclusi nell'ambito. Aprire la barra degli strumenti **Elenco errori** per visualizzare gli errori. (Se non viene visualizzata la barra degli strumenti **Elenco errori**, scegliere **Visualizza** > **Elenco errori** dalla barra dei menu in alto.)

   ![Elenco errori](../ide/media/quickstart-aspnet-errorlist.png)

1. Nella finestra dell'editor, posizionare il cursore su una riga che contiene l'errore, quindi scegliere la lampadina relativa alle azioni rapide nel margine sinistro. Nel menu a discesa, scegliere **using System;** per aggiungere questa direttiva all'inizio del file e risolvere gli errori.

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Premere **CTRL**+**F5** per eseguire l'applicazione e aprirla in un Web browser.

1. Nella parte superiore del sito web, scegliere **Informazioni su** per visualizzare il messaggio della directory aggiunto in precedenza nel metodo `OnGet()` per la pagina **Informazioni su**.

1. Chiudere il Web browser.

> [!NOTE]
> Se viene visualizzato il messaggio di errore **Impossibile connettersi al server Web 'IIS Express'**, chiudere Visual Studio e quindi aprirlo usando l'opzione **Esegui come amministratore** dal menu di scelta rapida. Eseguire quindi di nuovo l'applicazione.

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento sull'uso di IDE di Visual Studio. Se si vuole approfondire la conoscenza relativa alle funzionalità, continuare con un'esercitazione nella sezione del sommario relativa alle **esercitazioni**.

## <a name="next-steps"></a>Passaggi successivi
La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C#, ASP.NET Core e dell'IDE di Visual Studio. Per altre informazioni, continuare con l'esercitazione seguente.

> [!div class="nextstepaction"]
> [Introduzione a C# e ad ASP.NET Core in Visual Studio](tutorial-csharp-aspnet-core.md)
