---
title: Aggiunta del supporto di altri linguaggi all'editor di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology:
- vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 885563b456ca27c319e8b1eafb1963e77d9d1cfa
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Aggiunta del supporto di altri linguaggi all'editor di Visual Studio
Informazioni su come l'editor di Visual Studio supporti la lettura e il passaggio da un linguaggio di programmazione a un altro e su come aggiungere il supporto per altri linguaggi all'editor di Visual Studio.  
  
## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Supporto della colorazione della sintassi, del completamento istruzioni e di Navigate To (Passa a)  
 Alcune funzionalità dell'editor di Visual Studio, ad esempio la colorazione della sintassi, il completamento istruzioni e Navigate To (Passa a) consentono una maggiore facilità di lettura, creazione e modifica del codice. Lo screenshot seguente mostra un esempio di modifica di uno script Perl in Visual Studio. La sintassi viene colorata automaticamente. Ad esempio, i commenti nel codice sono di colore verde, il codice è nero, i percorsi sono rossi e le istruzioni sono blu. L'editor di Visual Studio applica automaticamente la colorazione della sintassi per qualsiasi linguaggio supportato. Oltre a questo, quando si inizia a immettere una parola chiave o un oggetto noto del linguaggio, la funzionalità di completamento istruzioni visualizza l'elenco delle istruzioni e degli oggetti possibili. Il completamento istruzioni consente di creare codice in modo più rapido e facile.  
  
 ![Colorazione della sintassi in uno script Perl](../ide/media/vside_perledit.png "VSIDE_PerlEdit")  
  
 Attualmente Visual Studio supporta le funzioni di colorazione della sintassi e di completamento istruzioni per i linguaggi riportati di seguito tramite le [grammatiche TextMate](https://manual.macromates.com/en/language_grammars). Se nella tabella non è presente il linguaggio preferito, tuttavia, non è il caso di preoccuparsi: è possibile aggiungerlo.  
  
|||||||  
|-|-|-|-|-|-|  
|Bat|F#|Java|Markdown|Rust|Visual Basic|  
|Clojure|Vai|JavaDoc|Objective-C|ShaderLab|C#|  
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|  
|CoffeeScript|HTML|LESS|Python|SQL|VBNet|  
|CSS|INI|LUA|R|Swift|XML|  
|Docker|Jade|Marca|Ruby|TypeScript|YAML|  
  
 Oltre alla colorazione della sintassi e al completamento delle istruzioni di base, Visual Studio ha una funzionalità detta [Navigate To](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/) (Passa a). Questa funzionalità consente di cercare rapidamente file di codice, percorsi dei file e simboli di codice. Visual Studio supporta la funzione Navigate To (Passa a) per i linguaggi seguenti.  
  
-   Vai  
  
-   Java  
  
-   JavaScript  
  
-   PHP  
  
-   TypeScript  
  
-   Visual Basic  
  
-   Visual C++  
  
-   C#  
  
Tutti questi tipi di file dispongono delle funzionalità descritte in precedenza anche se il supporto di un linguaggio specifico non è stato ancora installato. L'installazione di supporto specializzato per alcuni linguaggi potrebbe offrire il supporto di linguaggi aggiuntivi, ad esempio IntelliSense, o di altre funzionalità avanzate di un linguaggio, ad esempio le lampadine.  
  
## <a name="adding-support-for-non-supported-languages"></a>Aggiunta del supporto per linguaggi non supportati  
 Visual Studio 2015 Update 1 e versioni successive offrono il supporto dei linguaggi nell'editor tramite le [grammatiche TextMate](https://manual.macromates.com/en/language_grammars). Se il linguaggio di programmazione preferito non è attualmente supportato nell'editor di Visual Studio, prima di tutto eseguire una ricerca sul Web. Un bundle TextMate per questo linguaggio potrebbe già essere disponibile. Se non si riesce a trovare il bundle, tuttavia, è possibile aggiungere il supporto del linguaggio autonomamente in Visual Studio 2015 Update 1 o versione successiva mediante la creazione di un modello di bundle TextMate per la grammatica e i frammenti del linguaggio.  
  
 Aggiungere le nuove grammatiche TextMate per Visual Studio nella cartella seguente:  
  
 *%userprofile%\\.vs\Extensions*  
  
 In questo percorso di base aggiungere le cartelle seguenti, se applicabili alla propria situazione:  
  
|Nome cartella|Descrizione|  
|-----------------|-----------------|  
|\\*\<nome linguaggio>*|Cartella del linguaggio. Sostituire  *\<nome linguaggio>* con il nome del linguaggio, ad esempio, *\Matlab*.|  
|*\Syntaxes*|Cartella della grammatica. Contiene i file della grammatica con estensione *json* per il linguaggio, ad esempio *Matlab.json*.|  
|*\Snippets*|Cartella dei frammenti. Contiene frammenti di codice per il linguaggio.|  
  
 In Windows *%userprofile%* si risolve nel percorso *c:\Users\\*\<nome utente>*.* Se nel sistema non esiste la cartella delle estensioni, è necessario crearla. Se la cartella esiste già, verrà nascosta.  
  
 Per informazioni dettagliate su come creare grammatiche TextMate, vedere [TextMate - Introduction to Language Grammars: How to add source code syntax highlighting embedded in HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) (TextMate: introduzione alle grammatiche dei linguaggi: come aggiungere l'evidenziazione della sintassi del codice sorgente incorporata in HTML) e [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) (Note sulla creazione della grammatica di un linguaggio e di un tema personalizzato per un bundle TextMate).  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio 2013 Navigate To Improvements](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/)  (Miglioramenti della funzione Navigate To (Passa a) di Visual Studio 2013)  
 [Procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md)   
 [Procedura dettagliata: Visualizzazione del completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)