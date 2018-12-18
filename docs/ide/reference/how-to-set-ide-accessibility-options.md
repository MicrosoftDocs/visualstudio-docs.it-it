---
title: 'Procedura: Impostare le opzioni di accessibilità IDE | Microsoft Docs'
ms.custom: ''
ms.date: 08/22/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b44f31b03dae1c553008685553548d886a8943a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-ide-accessibility-options"></a>Procedura: impostare le opzioni di accessibilità IDE
> [!TIP]
> Per altre informazioni sugli aggiornamenti di accessibilità recenti, visitare il post di blog sui [miglioramenti dell'accessibilità di Visual Studio 2017 (versione 15.3)](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/).

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contiene funzionalità che rendono più agevole la lettura e la scrittura per gli utenti con problemi di vista e difficoltà di movimento. Queste funzionalità includono, tra le altre, la modifica delle dimensioni e del colore del testo negli editor, la modifica delle dimensioni di testo e pulsanti sulle barre degli strumenti e il completamento automatico per metodi e parametri.  

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta anche i layout di tastiera Dvorak, che consentono di accedere più facilmente ai caratteri usati con maggiore frequenza. È anche possibile personalizzare le combinazioni di tasti predefinite di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [Identificazione e personalizzazione dei tasti di scelta rapida](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  

> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  

## <a name="editors-dialogs-and-tool-windows"></a>Editor, finestre di dialogo e finestre degli strumenti  
 Per impostazione predefinita, le finestre di dialogo e le finestre degli strumenti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usano le stesse dimensioni di carattere e gli stessi colori del sistema operativo. Le impostazioni relative ai colori per il frame dell'IDE, le finestre di dialogo, le barre degli strumenti e le finestre degli strumenti si basano su una combinazione di colori: chiara o scura. È possibile cambiare il tema colori corrente in [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md).  

 È anche possibile visualizzare finestre popup nella visualizzazione Codice dell'editor. Queste finestre possono indicare i membri disponibili per l'oggetto corrente e i parametri necessari per completare una funzione o un'istruzione e possono essere utili se l'utente ha difficoltà di digitazione, ma interferiscono con lo stato attivo nell'editor del codice, creando problemi per alcuni utenti. Per disattivare queste finestre è possibile aprire la finestra di dialogo Opzioni e deselezionando**Elenco membri automatico** e **Informazioni parametri** nella pagina **Editor di testo**, **Tutti i linguaggi**, **Generale** nella finestra di dialogo **Opzioni**.

 È possibile ridisporre le finestre nell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) in base alle proprie esigenze. È possibile ancorare, rendere mobile, nascondere o nascondere automaticamente ogni finestra degli strumenti.  

 Per altre informazioni su come modificare il layout delle finestre, vedere [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md).  

### <a name="changing-the-size-of-text"></a>Modifica delle dimensioni del testo  
 È possibile modificare le impostazioni per le finestre degli strumenti basate su testo, ad esempio le finestre **Comando**, **Immediato** e **Output**, nel riquadro **Tipi di carattere e colori** delle opzioni **Ambiente** nella finestra di dialogo **Strumenti**. Se l'opzione **[Tutte le finestre degli strumenti di testo]** è selezionata nell'elenco a discesa **Mostra impostazioni per**, l'impostazione predefinita è indicata come **Predefinita** negli elenchi a discesa **Primo piano elemento** e **Sfondo elemento**. È anche possibile modificare le impostazioni di visualizzazione del testo nell'editor.  

##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Per modificare le dimensioni del testo nelle finestre degli strumenti basate su testo e negli editor  

1.  Scegliere **Opzioni** dal menu **Strumenti**.  

2.  Scegliere **Tipi di carattere e colori** nella cartella **Ambiente**.  

3.  Selezionare un'opzione nel menu a discesa **Mostra impostazioni per**.  

     Per modificare le dimensioni dei caratteri del testo in un editor, scegliere **Editor di testo**.  

     Per modificare le dimensioni dei caratteri del testo nelle finestre degli strumenti basate su testo, scegliere **[Tutte le finestre degli strumenti di testo]**.  

     Per modificare le dimensioni dei caratteri del testo delle descrizioni comandi in un editor, scegliere **Descrizione comando editor**.  

     Per modificare le dimensioni dei caratteri del testo degli elementi popup di completamento istruzioni, scegliere **Completamento istruzioni**.  

4.  In **Elementi visualizzati** selezionare **Testo normale**.  

5.  In **Carattere** selezionare un nuovo tipo di carattere.  

6.  In **Dimensioni** selezionare nuove dimensioni del carattere.  

    > [!NOTE]
    >  Per reimpostare le dimensioni del testo per le finestre degli strumenti basate su testo e per gli editor, scegliere **Usa impostazioni predefinite**.  

7.  Scegliere **OK**.  

### <a name="changing-the-colors-used-in-the-ide"></a>Modifica dei colori usati nell'IDE  
 È anche possibile modificare i colori predefiniti per il testo, gli indicatori di margine, lo spazio e gli elementi di codice nell'editor.  

> [!NOTE]
>  Per usare colori a contrasto elevato per tutte le finestre delle applicazioni del sistema operativo, premere **ALT di sinistra +** **MAIUSC di sinistra + STAMP**. Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è aperto, chiuderlo e riaprirlo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per implementare correttamente i colori a contrasto elevato.  

##### <a name="to-change-the-color-of-items-in-the-editor"></a>Per modificare il colore degli elementi nell'editor  

1.  Scegliere **Opzioni** dal menu **Strumenti**.  

2.  Scegliere **Tipi di carattere e colori** nella cartella **Ambiente**.  

3.  In **Mostra impostazioni per** scegliere **Editor di testo**.  

4.  In **Elementi visualizzati** selezionare un elemento di cui si vuole modificare la visualizzazione, ad esempio **Testo normale**, **Margine indicatore**, **Spazio vuoto visibile**, **Nome attributo HTML** o **Attributo XML**.  

5.  Selezionare le impostazioni di visualizzazione delle opzioni seguenti: **Primo piano elemento**, **Sfondo elemento** e **Grassetto**.  

6.  Scegliere **OK**.  

## <a name="toolbars"></a>Barre degli strumenti  
 Per migliorare l'usabilità e l'accessibilità delle barre degli strumenti, è possibile aggiungere testo ai pulsanti di queste ultime.  

#### <a name="to-assign-text-to-toolbar-buttons"></a>Per assegnare testo ai pulsanti delle barre degli strumenti  

1.  Scegliere **Personalizza** dal menu **Strumenti**.  

2.  Nella finestra di dialogo **Personalizza** fare clic sulla scheda **Comandi**.  

3.  Selezionare **Barra degli strumenti** e quindi scegliere il nome della barra degli strumenti che contiene il pulsante per il quale si vuole visualizzare testo.  

4.  Selezionare il comando che si vuole modificare nell'elenco.  

5.  Scegliere **Modifica selezione**.  

6.  Scegliere **Icona e testo**.  

#### <a name="to-modify-the-buttons-displayed-text"></a>Per modificare il testo visualizzato di un pulsante  

1.  Selezionare di nuovo **Modifica selezione**.  

2.  Accanto a In **nome** specificare una nuova didascalia per il pulsante selezionato.  

## <a name="see-also"></a>Vedere anche  
 [Funzionalità di accessibilità di Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Risorse per la progettazione di applicazioni accessibili](../../ide/reference/resources-for-designing-accessible-applications.md)
