---
title: Uso delle impostazioni di EditorConfig in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 12/13/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-general
ms.openlocfilehash: fe1653df6fc1d71dc4497c6e7e0a9adae9fa0b44
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Creare impostazioni personalizzate e portabili per l'editor con EditorConfig

In Visual Studio 2017 è possibile aggiungere un file [EditorConfig](http://editorconfig.org/) al progetto o alla codebase per imporre stili di codifica coerenti per tutti gli utenti che usano la codebase. Le impostazioni di EditorConfig hanno la precedenza sulle impostazioni dell'editor di testo di Visual Studio globali. Ciò significa che è possibile personalizzare ogni codebase in modo che vengano usate le impostazioni dell'editor di testo specifiche del progetto. È comunque possibile impostare preferenze personali per l'editor nella finestra di dialogo **Opzioni** di Visual Studio. Queste impostazioni si applicano ogni volta che si usa una codebase priva di file con estensione *editorconfig* o quando il file con estensione *editorconfig* non esegue l'override di un'impostazione specifica. Un esempio di tale preferenza è lo stile del rientro&mdash;caratteri di tabulazione o spazi.

Le impostazioni di EditorConfig sono supportate da numerosi editor di codice e molti ambienti IDE, tra cui Visual Studio. Si tratta di un componente portatile che viene trasferito con il codice ed è in grado di imporre stili di codice anche all'esterno di Visual Studio.

> [!NOTE]
> Quando si aggiunge un file EditorConfig al progetto in Visual Studio, la formattazione del codice esistente non viene modificata a meno che non si formatti il documento (**Modifica** > **Avanzate**  >  **Formato documento** o **CTRL**+**K**, **CTRL**+**D**). Le nuove righe di codice vengono tuttavia formattate in base alle impostazioni del file EditorConfig.

## <a name="coding-consistency"></a>Coerenza del codice

Le impostazioni nei file EditorConfig consentono di mantenere stili e impostazioni di codifica coerenti in una codebase, ad esempio stile di rientro, rientro di tabulazione, caratteri di fine riga, codifica e altro, indipendentemente dall'editor o dall'IDE in uso. Ad esempio, quando si scrive codice in C#, se la codebase ha una convenzione preferita in base alla quale i rientri sono sempre costituiti da cinque spazi, i documenti devono usare la codifica UTF-8 e ogni riga termina sempre con un CR/LF, è possibile configurare un file con estensione *editorconfig* a tale scopo.

Le convenzioni di codifica usate per i progetti personali possono essere diverse da quelle per i progetti del team. Si potrebbe ad esempio preferire che durante la scrittura di codice il rientro aggiunga un carattere di tabulazione. Il team, tuttavia, potrebbe preferire per il rientro quattro spazi anziché un carattere di tabulazione. I file di EditorConfig risolvono questo problema consentendo di predisporre una configurazione per ogni scenario.

Dato che le impostazioni si trovano all'interno di un file nella codebase, seguono quest'ultima nei suoi spostamenti. Quando il file di codice viene aperto, le impostazioni dell'editor di testo vengono implementate, a condizione che l'editor sia compatibile con EditorConfig. Per altre informazioni sui file di EditorConfig, vedere il sito Web [EditorConfig.org](http://editorconfig.org/).

## <a name="supported-settings"></a>Impostazioni supportate

L'editor in Visual Studio supporta il set di base delle [proprietà di EditorConfig](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- trim\_trailing_whitespace
- insert\_final_newline
- radice

Le impostazioni dell'editor EditorConfig sono supportate in tutti i linguaggi supportati da Visual Studio, ad eccezione di XML. EditorConfig supporta inoltre le convenzioni di [stile del codice](../ide/editorconfig-code-style-settings-reference.md) e [denominazione](../ide/editorconfig-naming-conventions.md) per C# e Visual Basic.

## <a name="adding-and-removing-editorconfig-files"></a>Aggiunta e rimozione dei file EditorConfig

L'aggiunta di un file EditorConfig al progetto o alla codebase non sostituisce gli stili esistenti con quelli nuovi. Se, ad esempio, il file contiene rientri formattati con tabulazioni e si aggiunge un file EditorConfig che imposta rientri con spazi, i caratteri di rientro non vengono convertiti automaticamente in spazi. Le nuove righe di codice vengono tuttavia formattate in base al file EditorConfig. Inoltre, se si formatta il documento (**Modifica** > **Avanzate** > **Formatta documento** o **CTRL**+**K**, **CTRL**+**D**), le impostazioni nel file EditorConfig vengono applicate alle righe di codice esistenti.

Se il file EditorConfig viene rimosso dal progetto o dalla codebase sarà necessario chiudere e riaprire i file di codice aperti per ripristinare le impostazioni globali dell'editor per le nuove righe di codice.

### <a name="to-add-an-editorconfig-file-to-a-project-or-solution"></a>Per aggiungere un file EditorConfig a un progetto o a una soluzione

1. Aprire un progetto o una soluzione in Visual Studio. Selezionare il progetto o il nodo della soluzione, a seconda che le impostazioni del file con estensione *editorconfig* siano da applicare a tutti i progetti nella soluzione o soltanto a uno. È anche possibile selezionare una cartella del progetto o della soluzione alla quale aggiungere il file con estensione *editorconfig*.

1. Dalla barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento...** , oppure premere **CTRL**+**MAIUSC**+**A**.

   Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

1. Nelle categorie a sinistra scegliere **Generale** e selezionare il modello **File di testo**. Nella casella di testo **Nome** immettere `.editorconfig` e scegliere **Aggiungi**.

   Un file con estensione *editorconfig* viene visualizzato in Esplora soluzioni e viene aperto nell'editor.

   ![File con estensione editorconfig in Esplora soluzioni](media/editorconfig-in-solution-explorer.png)

1. Modificare il file come necessario, ad esempio:

   ```EditorConfig
   root = true

   [*.{cs,vb}]
   indent_size = 4
   trim_trailing_whitespace = true

   [*.cs]
   csharp_new_line_before_open_brace = methods
   ```

In alternativa, è possibile installare l'[estensione del servizio di linguaggio di EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig). Dopo aver installato l'estensione, scegliere **Aggiungi** > **File .editorconfig** dal menu di scelta rapida del nodo della soluzione, del nodo del progetto o di una qualsiasi cartella in Esplora soluzioni.

![Aggiungere il file .editorconfig usando l'estensione](media/editorconfig-extension-add.png)

## <a name="override-editorconfig-settings"></a>Eseguire l'override delle impostazioni di EditorConfig

Quando si aggiunge un file con estensione *editorconfig* in una cartella della gerarchia di file, le impostazioni vengono applicate a tutti i file applicabili in tale livello e sotto di questo. È anche possibile eseguire l'override delle impostazioni di EditorConfig per un particolare progetto, codebase o parte di una codebase, in modo da usare convenzioni diverse rispetto ad altre parti della codebase. Questo approccio può essere utile quando si incorpora codice proveniente da altre origini e non si vuole modificarne la convenzioni.

Per eseguire l'override di alcune o di tutte le impostazioni di EditorConfig, aggiungere un file con estensione *editorconfig* a livello della gerarchia di file in cui si vuole applicare l'override delle impostazioni. Le impostazioni del nuovo file EditorConfig vengono applicate ai file presenti allo stesso livello e in tutte le sottodirectory.

![Gerarchia di EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Se si vuole eseguire l'override di alcune impostazioni, ma non di tutte, è sufficiente specificare tali impostazioni nel file con estensione *editorconfig*. Viene eseguito l'override solo delle proprietà elencate in modo esplicito nel file di livello inferiore. Le altre impostazioni dei file con estensione *editorconfig* di livello superiore continuano a essere applicate. Per assicurarsi che _nessuna_ impostazione di _nessun_ file con estensione *editorconfig* di livello superiore sia applicata a questa parte della codebase, aggiungere la proprietà ```root=true``` al file con estensione *editorconfig* di livello inferiore:

```EditorConfig
# top-most EditorConfig file
root = true
```

I file con estensione editorconfig vengono letti dall'alto in basso e i file più vicini vengono letti per ultimi. Le convenzioni delle sezioni EditorConfig corrispondenti vengono applicate in ordine di lettura, pertanto le convenzioni nei file più vicini hanno la precedenza.

## <a name="editing-editorconfig-files"></a>Modifica dei file EditorConfig

Visual Studio consente di modificare i file con estensione *editorconfig* fornendo elenchi di completamento IntelliSense.

![IntelliSense in un file con estensione editorconfig](media/editorconfig-intellisense-no-extension.png)

Dopo aver modificato il file EditorConfig è necessario ricaricare i file di codice per rendere effettive le nuove impostazioni.

Se si modificano vari file con estensione *editorconfig*, può essere utile usare l'[estensione del servizio di linguaggio EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig). Alcune delle funzionalità di questa estensione sono evidenziazione della sintassi, IntelliSense migliorato, convalida e formattazione di codice.

![IntelliSense con estensione del servizio di linguaggio EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Esempio

L'esempio seguente illustra lo stato dei rientri di un frammento di codice C# prima e dopo l'aggiunta di un file con estensione *editorconfig* al progetto. L'impostazione **Tabulazioni** nella finestra di dialogo **Opzioni** per l'editor di testo di Visual Studio è definita in modo che quando si preme **TAB** vengono generati spazi.

![Impostazione della tabulazione dell'editor di testo](../ide/media/vside_editorconfig_tabsetting.png)

Come previsto, premendo **TAB** sulla linea successiva la linea rientra con l'aggiunta di quattro caratteri spazio.

![Il codice prima dell'uso di EditorConfig](../ide/media/vside_editorconfig_before.png)

Aggiungere al progetto un nuovo file con estensione *editorconfig* e il contenuto seguente. L'impostazione `[*.cs]` indica che questa modifica viene applicata solo ai file di codice C# all'interno del progetto.

```EditorConfig
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

A questo punto, quando si preme **TAB** si ottengono caratteri di tabulazione anziché spazi.

![TAB aggiunge caratteri di tabulazione](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Risoluzione dei problemi relativi alle impostazioni EditorConfig

Se è presente un file con estensione editorconfig nella struttura di directory in corrispondenza o al di sopra della posizione del progetto, Visual Studio applica all'editor le impostazioni dell'editor presenti nel file. In questo caso la barra di stato potrebbe visualizzare il seguente messaggio:

   **"Le convenzioni di scrittura codice di questo progetto sostituiscono le preferenze utente per questo tipo di file."**

Ciò significa che se le impostazioni dell'editor in **Strumenti** > **Opzioni** > **Editor di testo**, ad esempio la dimensione e lo stile dei rientri, la dimensione delle tabulazioni o le convenzioni di scrittura del codice, sono specificate in un file EditorConfig che si trova al di sopra o in corrispondenza del livello del progetto nella struttura di directory, le convenzioni presenti nel file EditorConfig hanno la precedenza sulle impostazioni specificate in **Opzioni**. È possibile controllare questo comportamento attivando o disattivando l'opzione **Segui convenzioni di scrittura codice del progetto** in **Strumenti** > **Opzioni** > **Editor di testo**. Se si deseleziona l'opzione, si disattiva il supporto di EditorConfig per Visual Studio.

![Strumenti - Opzioni - Segui convenzioni di scrittura codice del progetto](media/coding_conventions_option.png)

È possibile trovare i file con estensione *editorconfig* nelle directory padre aprendo un prompt dei comandi ed eseguendo il comando seguente nella directory radice del disco che contiene il progetto:

```Shell
dir .editorconfig /s
```

È possibile controllare l'ambito delle convenzioni EditorConfig impostando la proprietà ```root=true``` nel file con estensione *editorconfig* presente nella directory radice del repository o nella directory in cui si trova il progetto. Visual Studio cerca un file con estensione *editorconfig* nella directory del file aperto e in tutte le directory padre. La ricerca termina quando si raggiunge il filepath radice o se viene trovato un file con estensione *editorconfig* con ```root=true```.

## <a name="see-also"></a>Vedere anche

[.NET code style conventions](../ide/editorconfig-code-style-settings-reference.md) (Convenzioni di stile del codice .NET)  
[Convenzioni di denominazione .NET](../ide/editorconfig-naming-conventions.md)  
[Supporting EditorConfig for a language service](../extensibility/supporting-editorconfig.md) (Supporto di EditorConfig per un servizio di linguaggio)  
[EditorConfig.org](http://editorconfig.org/)  
[Writing code in the editor](writing-code-in-the-code-and-text-editor.md) (Scrittura di codice nell'editor)
