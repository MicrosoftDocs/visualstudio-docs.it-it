---
title: Sincronizzare le impostazioni in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ef4179c5bc0fb80e2fb65d54885c342ca49bce3b
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="synchronize-your-settings-in-visual-studio"></a>Sincronizzare le impostazioni in Visual Studio

Quando si usa lo stesso account di personalizzazione per accedere a Visual Studio Online da più computer, per impostazione predefinita le impostazioni vengono sincronizzate in tutti i computer.

## <a name="synchronized-settings"></a>Impostazioni sincronizzate

Per impostazione predefinita, vengono sincronizzate le impostazioni seguenti.

- Impostazioni di sviluppo. È necessario selezionare un set di impostazioni la prima volta che si esegue Visual Studio, ma è possibile modificare la selezione in qualsiasi momento. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

- Le opzioni seguenti nelle pagine **Strumenti &#124; Opzioni**:

    - Impostazioni del **tema** e di maiuscole e minuscole nella barra dei menu nella pagina delle opzioni **Ambiente**, **Generale**

    - Tutte le impostazioni nella pagina delle opzioni **Ambiente**, **Tipi di carattere e colori**

    - Tutti i tasti di scelta rapida nella pagina delle opzioni **Ambiente**, **Tastiera**

    - Tutte le impostazioni nella pagina delle opzioni **Ambiente, Schede e Finestre**

    - Tutte le impostazioni nella pagina delle opzioni **Ambiente**, **Avvio**

    - Tutte le impostazioni nelle pagine delle opzioni **Editor di testo**

    - Tutte le impostazioni nelle pagine delle opzioni di **XAML Designer**

- Alias di comandi definiti dall'utente. Per altre informazioni su come definire gli alias di comandi, vedere [Alias di comandi di Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- I layout delle finestre definite dall'utente nella pagina **Finestra &#124; Gestisci layout finestra**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Disattivare le impostazioni sincronizzate per un computer specifico

Le impostazioni sincronizzate per Visual Studio sono attivate per impostazione predefinita. È possibile disattivare le impostazioni sincronizzate in un computer visitando la pagina **Strumenti &#124; Opzioni &#124; Ambiente&#124; Account** e deselezionando la casella di controllo.  Ad esempio, se si decide di non sincronizzare le impostazioni di Visual Studio nel computer A, nessuna delle modifiche alle impostazioni del computer A verrà visualizzata nel computer B o nel computer C. I computer B e C continueranno a sincronizzarsi tra loro, ma non si sincronizzeranno con il computer A.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizzare le impostazioni tra prodotti e edizioni della famiglia Visual Studio

Le impostazioni possono essere sincronizzate tra tutte le edizioni di Visual Studio, compresa l'edizione Community. Le impostazioni vengono sincronizzate anche tra prodotti della famiglia Visual Studio. Tuttavia, ogni prodotto di questa famiglia potrebbe disporre di impostazioni personalizzate che non vengono condivise con Visual Studio. Ad esempio, impostazioni specifiche di un prodotto nel computer A verranno condivise con un altro prodotto nel computer B, ma non con Visual Studio nel computer A o B.

## <a name="side-by-side-synchronized-settings"></a>Impostazioni sincronizzate affiancate

In Visual Studio 15.3 e versioni successive, è stata interrotta la condivisione di alcune impostazioni, ad esempio i layout delle finestre degli strumenti, tra diverse installazioni affiancate di Visual Studio 2017 modificando il percorso del file `CurrentSettings.vssettings` in una cartella `%userprofile%\Documents\Visual Studio 2017\Settings`specifica dell'installazione simile a `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings`.

**NOTA:** per usare le nuove impostazioni specifiche dell'installazione è necessario eseguire una nuova installazione. Quando si esegue l'aggiornamento di un'installazione Visual Studio 2017 esistente alla versione più recente, verrà usato il percorso condiviso esistente. Se attualmente sono presenti installazioni affiancate di Visual Studio 2017 e si decide di eseguire l'aggiornamento usando il nuovo percorso del file di impostazioni specifico dell'installazione, eseguire i passaggio passaggi riportati:

1. Dopo l'aggiornamento, usare la procedura guidata Importazione/Esportazione impostazioni per esportare tutte le impostazioni esistenti in un percorso diverso dalla cartella `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx`.
2. Aprire il **prompt dei comandi per gli sviluppatori per VS 2017** dell'installazione di Visual Studio aggiornata ed eseguire `devenv /resetuserdata`.
3. Avviare Visual Studio e importare le impostazioni salvate dal file di impostazioni esportato.

## <a name="see-also"></a>Vedere anche

[Personalizzazione dell'IDE](../ide/personalizing-the-visual-studio-ide.md)
