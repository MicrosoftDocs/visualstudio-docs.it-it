---
title: Ripristinare Visual Studio
titleSuffix: ''
description: Informazioni su come riparare un'installazione di Visual Studio 2017
ms.date: 10/12/2020
ms.custom: vs-acquisition
ms.topic: how-to
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 55ebb7c44b44a14154cc54f54885455821f9ee68
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386787"
---
# <a name="repair-visual-studio"></a>Ripristinare Visual Studio

In alcuni casi l'installazione di Visual Studio può risultare danneggiata Un ripristino è utile per risolvere i problemi in fase di installazione in tutte le operazioni di installazione, inclusi gli aggiornamenti.

## <a name="when-to-use-repair"></a>Quando usare il ripristino
* Se si verificano problemi di payload dell'installazione. Questo problema può verificarsi quando la scrittura del file su disco non riesce e non può essere corretta eliminando il file danneggiato. Il ripristino può acquisire nuovamente i file necessari. 
* Se si verificano problemi di download sul lato client. Supponendo di aver risolto eventuali problemi di connessione o proxy, il ripristino può essere utile. 
* Se si verificano problemi durante l'aggiornamento Visual Studio. La correzione corregge molti problemi comuni relativi all'aggiornamento. 

> [!TIP] 
> Se il problema di installazione è causato da un problema in un servizio Di Windows sottostante, ad esempio Windows Installer, il ripristino può verificarsi nello stesso problema. I problemi di sistema possono includere una connessione Internet Windows Installer o instabile. Per verificare la presenza di un problema di sistema, usare la segnalazione errori generata dall'operazione di installazione.

> [!NOTE] 
> Il ripristino Visual Studio reimposta le impostazioni utente e installa nuovamente gli assembly già disponibili. Se si verifica un problema del prodotto, creare un ticket Visual Studio [feedback,](https://aka.ms/feedback/suggest?space=8)perché il ripristino potrebbe non risolvere il problema.

## <a name="how-to-repair"></a>Come eseguire il ripristino
::: moniker range="vs-2017"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Ad esempio, in un computer che esegue l'Aggiornamento dell'anniversario di Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

   > [!NOTE]
   > In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.
   >
   > In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Aprire il programma di installazione, scegliere **Altro** e quindi scegliere **Ripristina**.

    ![Ripristinare Visual Studio dalla Programma di installazione di Visual Studio](media/repair-visual-studio.png "Ripristinare Visual Studio dalla Programma di installazione di Visual Studio")

   > [!NOTE]
   > Con il ripristino di Visual Studio verrà reimpostato l'ambiente. Le personalizzazioni locali verranno rimosse, ad esempio le estensioni per utente installate senza l'elevazione dei privilegi, le impostazioni utente e i profili. Verranno ripristinate le impostazioni sincronizzate, ad esempio temi, colori e tasti di scelta rapida.
   >

   > [!TIP]
   > L'opzione **Ripristina** viene visualizzata solo per le istanze installate di Visual Studio. Se non viene visualizzata l'opzione **Ripristina**, è probabile che sia stata selezionata l'opzione **Altro** in una versione inclusa nel programma di installazione di Visual Studio come "Disponibile" anziché "Installata".

::: moniker-end

::: moniker range=">=vs-2019"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Nel menu Start di Windows è possibile cercare "programma di installazione".

     ![Programma di installazione di Visual Studio](media/vs-2019/visual-studio-installer.png "Cercare il Programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata. Scegliere quindi **Altro** e **Ripristina**.

     ![Ripristino Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Ripristino Visual Studio 2019")

   > [!NOTE]
   > Con il ripristino di Visual Studio verrà reimpostato l'ambiente. Le personalizzazioni locali verranno rimosse, ad esempio le estensioni per utente installate senza l'elevazione dei privilegi, le impostazioni utente e i profili. Verranno ripristinate le impostazioni sincronizzate, ad esempio temi, colori e tasti di scelta rapida.
   >

   > [!TIP]
   > L'opzione **Ripristina** viene visualizzata solo per le istanze installate di Visual Studio. Se non viene visualizzata l'opzione **Ripristina**, è probabile che sia stata selezionata l'opzione **Altro** in una versione inclusa nel programma di installazione di Visual Studio come "Disponibile" anziché "Installata".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
* [Risoluzione dei problemi di installazione e aggiornamento di Visual Studio](troubleshooting-installation-issues.md)
