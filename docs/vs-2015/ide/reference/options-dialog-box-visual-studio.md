---
title: Finestra di dialogo Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 373c6ad006d915412252f48ac536bb50c7ff44bf
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048515"
---
# <a name="options-dialog-box-visual-studio"></a>Finestra di dialogo Opzioni (Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]


La finestra di dialogo **Opzioni** consente di configurare l'ambiente di sviluppo integrato (IDE) in base alle proprie esigenze. Ad esempio, è possibile stabilire un percorso di salvataggio predefinito per i progetti, modificare l'aspetto e il comportamento predefiniti delle finestre e creare tasti di scelta rapida per i comandi di uso comune. Sono inoltre disponibili opzioni specifiche del linguaggio di sviluppo e della piattaforma. È possibile accedere alla finestra di dialogo **Opzioni** dal menu **Strumenti**.

> [!NOTE]
>  Le opzioni disponibili nelle finestre di dialogo e i nomi e i percorsi dei comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida a seconda dell'edizione o delle impostazioni attive. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="layout-of-the-options-dialog-box"></a>Layout della finestra di dialogo Opzioni
 La finestra di dialogo **Opzioni** è suddivisa in due parti: un riquadro di spostamento a sinistra e un'area di visualizzazione a destra. Il controllo della struttura ad albero nel riquadro di spostamento include nodi di cartella, ad esempio Ambiente, Editor di testo, Progetti e soluzioni e Controllo del codice sorgente. Espandere un nodo di cartella per elencare le pagine di opzioni che contiene. Quando si seleziona il nodo per una pagina particolare, le relative opzioni appaiono nell'area di visualizzazione.

 Le opzioni per una funzionalità IDE non appaiono nel riquadro di spostamento finché la funzionalità non viene caricata in memoria. Di conseguenza, è possibile che le opzioni visualizzate quando si inizia una nuova sessione non siano le stesse che apparivano quando si è chiusa l'ultima. Quando si crea un progetto o si esegue un comando che usa una determinata applicazione, i nodi per le relative opzioni vengono aggiunti alla finestra di dialogo Opzioni. Queste opzioni aggiunte rimarranno disponibili finché la funzionalità IDE rimane in memoria.

> [!NOTE]
>  Alcune raccolte di impostazioni esaminano il numero di pagine visualizzate nel riquadro di spostamento della finestra di dialogo Opzioni. Per scegliere di visualizzare tutte le pagine possibili, selezionare **Mostra tutte le impostazioni**.

## <a name="how-options-are-applied"></a>Modalità di applicazione delle opzioni
 Fare clic su OK nella finestra di dialogo **Opzioni** per salvare tutte le impostazioni in tutte le pagine. Fare clic su Annulla in qualsiasi pagina per annullare tutte le richieste di modifica, incluse quelle eseguite in altre pagine **Opzioni**. Alcune modifiche alle impostazioni delle opzioni, ad esempio quelle apportate in [Tipi di carattere e colori, Ambiente, finestra di dialogo Opzioni](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), avranno effetto solo quando si chiude e si riapre Visual Studio.

### <a name="show-all-settings"></a>Mostra tutte le impostazioni
 Selezionando o deselezionando l'opzione **Mostra tutte le impostazioni** vengono applicate tutte le modifiche apportate nella finestra di dialogo **Opzioni**, anche se non si è ancora scelto **OK**.

## <a name="see-also"></a>Vedere anche
 [Personalizzazione dell'editor](../../ide/customizing-the-editor.md)
