---
title: Gestire strumenti esterni | Microsoft Docs
ms.custom: 
ms.date: 11/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 78a3e1ee549a42681d6f15b432d0c6bb608976fd
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="manage-external-tools"></a>Gestire strumenti esterni

È possibile chiamare strumenti esterni direttamente in Visual Studio usando il menu **Strumenti**. Alcuni strumenti predefiniti sono disponibili nel menu **Strumenti** ed è possibile personalizzare il menu aggiungendo altri file eseguibili personalizzati.

## <a name="tools-available-on-the-tools-menu"></a>Strumenti disponibili nel menu Strumenti

Il menu **Strumenti** include alcuni strumenti predefiniti, ad esempio:

* **Estensioni e aggiornamenti** per la [gestione delle estensioni di Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Gestione frammenti di codice** per l'[organizzazione dei frammenti di codice](code-snippets.md)
* **PreEmptive Protection - Dotfuscator** per l'avvio di [Dotfuscator Community Edition (CE)](dotfuscator/index.md) se [installato](dotfuscator/install.md)
* **Personalizza** per la [personalizzazione di menu e barre degli strumenti](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opzioni** per l'[impostazione di un'ampia gamma di opzioni per l'IDE di Visual Studio e altri strumenti](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Aggiungere nuovi strumenti al menu Strumenti

È possibile aggiungere uno strumento esterno per visualizzarlo nel menu **Strumenti**.

1. Aprire la finestra di dialogo **Strumenti esterni** scegliendo **Strumenti** > **Strumenti esterni**.

1. Fare clic su **Aggiungi** e quindi compilare le informazioni. L'immissione seguente consente ad esempio di aprire la cartella dove si trova il file attualmente aperto in Visual Studio:

   * Titolo: `Open File Location`

   * Comando: `explorer.exe`

   * Argomenti: `/root, "$(ItemDir)"`

   ![Finestra di dialogo Strumenti esterni](media/external-tools-dialog.png)

Di seguito è riportato un elenco completo di argomenti che possono essere usati per la definizione di uno strumento esterno:

|nome|Argomento|Descrizione|  
|----------|--------------|-----------------|  
|Percorso elemento|$(ItemPath)|Nome file completo del file corrente (unità + percorso + nome file).|  
|Directory elemento|$(ItemDir)|Directory del file corrente (unità + percorso).|  
|Nome file elemento|$(ItemFilename)|Nome del file corrente (nome file).|  
|Estensione di elemento|$(ItemExt)|Estensione del nome del file corrente.|  
|Riga corrente|$(CurLine)|Posizione della riga corrente del cursore nella finestra del codice.|  
|Colonna corrente|$(CurCol)|Posizione della colonna corrente del cursore nella finestra del codice.|  
|Testo corrente|$(CurText)|Testo selezionato.|  
|Percorso di destinazione|$(TargetPath)|Nome file completo dell'elemento da compilare (unità + percorso + nome file).|  
|Target Directory|$(TargetDir)|Directory dell'elemento da compilare.|  
|Target Name|$(TargetName)|Nome file dell'elemento da compilare.|  
|Estensione di destinazione|$(TargetExt)|Estensione di file dell'elemento da compilare.|  
|Directory binaria|$(BinDir)|Posizione finale del file binario in fase di compilazione (definita come unità + percorso).|  
|Directory del progetto|$(ProjDir)|Directory del progetto corrente (unità + percorso).|  
|Nome del file di progetto|$(ProjFileName)|Nome file del progetto corrente (unità + percorso + nome file).|  
|Directory soluzione|$(SolutionDir)|Directory della soluzione corrente (unità + percorso).|  
|Nome del file della soluzione|$(SolutionFileName)|Nome file della soluzione corrente (unità + percorso + nome file).|

> [!NOTE]
> La barra di stato dell'IDE visualizza le variabili di Riga corrente e Colonna corrente per indicare dove si trova il punto di inserimento nell'Editor codice attivo. La variabile di Testo corrente restituisce il testo o codice selezionato in quella posizione.

## <a name="see-also"></a>Vedere anche

[Strumenti per la compilazione in C/C++](/cpp/build/reference/c-cpp-build-tools)
