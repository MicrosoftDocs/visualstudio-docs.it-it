---
title: Impostare Visual Studio per Mac Tools per Unity
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: a1d6d523de9a5a57cf6b4c696a68dbdde1428156
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Impostare Visual Studio per Mac Tools per Unity

Questa sezione illustra come iniziare a usare Visual Studio per Mac Tools per Unity.

## <a name="install-visual-studio-for-mac"></a>Installare Visual Studio per Mac

Scaricare e installare Visual Studio per Mac. Tutte le edizioni di Visual Studio per Mac supportano Visual Studio per Mac Tools per Unity, inclusa l'edizione gratuita Community:

* Scaricare Visual Studio per Mac da [https://www.visualstudio.com/](https://www.visualstudio.com/).
* Visual Studio per Mac Tools per Unity viene installato automaticamente durante il processo di installazione.
* Per ulteriore assistenza nell'installazione, seguire la procedura riportata nella [Guida all'installazione](/visualstudio/mac/installation).

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Verificare che l'estensione di Visual Studio per Mac Tools per Unity sia abilitata

L'estensione di Visual Studio per Mac Tools per Unity dovrebbe essere abilitata per impostazione predefinita, tuttavia è possibile verificarlo e controllare il numero della versione installata:

1.  Dal menu di Visual Studio scegliere **Estensioni...**.

  ![Selezionare le estensioni](media/setup-vsmac-tools-unity-image1.png)

2.  Espandere la sezione Sviluppo di giochi e confermare la voce Visual Studio per Mac Tools per Unity.

  ![Visualizzare la voce di Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>Installare Unity

Visual Studio per Mac Tools per Unity richiede Unity 5.6.1 o versione successiva. Tutti i piani Unity funzionano con Visual Studio Tools per Unity, incluso il piano Personal gratuito. Scaricare Unity da [store.unity.com](https://store.unity.com/).

> [!NOTE]
> Per verificare che Visual Studio Tools per Unity sia abilitato nella versione di Unity installata, selezionare **About Unity (Informazioni su Unity)** dal menu di Unity e cercare il testo "Microsoft Visual Studio Tools for Unity enabled (Microsoft Visual Studio Tools for Unity enabled)" nella parte inferiore sinistra della finestra di dialogo.
>
>   ![About Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Configurare Unity per l'uso con Visual Studio per Mac

Visual Studio deve essere impostato come editor di script esterni in Unity:

1.  Selezionare **Preferences...** dal menu di Unity.

  ![Selezionare Preferences](media/setup-vsmac-tools-unity-image4.png)

2.  Nella finestra di dialogo Preferences selezionare la scheda **External Tools**.

3.  Dall'elenco a discesa External Script Editor scegliere **Visual Studio**, se elencato, altrimenti selezionare **Browse... (Sfoglia...)**.

  ![Selezionare Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4.  Se si è selezionato **Browse...**, spostarsi sulla directory Applications e selezionare Visual Studio, quindi fare clic su **Open**.

  ![Selezionare Open](media/setup-vsmac-tools-unity-image6.png)

5.  Dopo aver selezionato Visual Studio nell'elenco **External Script Editor**, chiudere la finestra di dialogo Preferences per completare il processo di configurazione.
