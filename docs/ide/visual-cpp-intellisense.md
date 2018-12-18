---
title: Intellisense per Visual C++ |Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0a00fb9fa52bcba39f4648fc3ffb9800890ac30
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="visual-c-intellisense"></a>IntelliSense per Visual C++

IntelliSense per C++ è disponibile per i file autonomi e per i file che fanno parte di un progetto C++. Nei progetti multipiattaforma alcune funzionalità di IntelliSense sono disponibili nei file con estensione cpp e c del progetto di codice condiviso, anche quando si opera in un contesto Android o iOS.

## <a name="intellisense-features-in-c"></a>Funzionalità IntelliSense in C++

IntelliSense è un nome assegnato a un set di funzionalità che semplificano la scrittura di codice. Per una maggiore flessibilità, tutte le funzionalità di IntelliSense possono essere abilitate o disabilitate nella finestra di dialogo **Opzioni** in **Editor di testo** > **C/C++** > **Avanzate**. La finestra di dialogo **Opzioni** è accessibile dal menu **Strumenti** sulla barra dei menu.

![Finestra di dialogo Strumenti/Opzioni](../ide/media/sintellisensecpptoolsoptions.PNG)

Per accedere a IntelliSense, è possibile utilizzare le voci di menu e i tasti di scelta rapida illustrati nella figura seguente.

![Menu IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

### <a name="statement-completion-and-member-list"></a>Elenco di completamento istruzioni e dei membri

Quando si inizia a digitare una parola chiave, un tipo, una funzione, un nome di variabile o un altro elemento del programma che viene riconosciuto dal compilatore, l'editor visualizza un elenco di suggerimenti per completare la parola.

Per un elenco delle icone e dei relativi significati, vedere [Icone di Visualizzazione classi e Visualizzatore oggetti](../ide/class-view-and-object-browser-icons.md).

![Finestra Completa parola di Visual C&#43;&#43;](../ide/media/vs2015_cpp_complete_word.png "vs2015_cpp_complete_word")

La prima volta che viene richiamato, l'elenco dei membri mostra solo i membri accessibili per il contesto corrente. Se successivamente si preme **CTRL**+**J**, vengono visualizzati tutti i membri indipendentemente dall'accessibilità. Se viene richiamato per la terza volta, viene visualizzato un elenco di elementi del programma ancora più ampio. È possibile disattivare l'elenco dei membri nella finestra di dialogo **Opzioni** in **Editor di testo** > **C/C++** > **Generale** > **Elenco membri automatico**.

![Elenco di membri di Visual C&#43;&#43;](../ide/media/vs2015_cpp_list_members.png "vs2015_cpp_list_members")

### <a name="parameter-help"></a>Guida ai parametri

Quando si digita una parentesi graffa di apertura di una chiamata di funzione o una parentesi angolare in una dichiarazione di variabile del modello di classe, l'editor visualizza una piccola finestra con i tipi di parametro per ogni overload del costruttore o della funzione. Il parametro corrente, in base della posizione del cursore, è visualizzato in grassetto. È possibile disattivare le informazioni sui parametri nella finestra di dialogo **Opzioni** in **Editor di testo** > **C/C++** > **Generale**  >  **Informazioni parametri**.

![Guida ai parametri di Visual C&#43;&#43;](../ide/media/vs_2015_cpp_param_help.png "vs_2015_cpp_param_help")

### <a name="quick-info"></a>Informazioni rapide

Quando si passa con il cursore del mouse su una variabile, viene visualizzata una piccola finestra inline che mostra le informazioni sul tipo e l'intestazione in cui è definito il tipo. Passare con il puntatore del mouse su una chiamata di funzione per visualizzare la firma della funzione. È possibile disattivare le informazioni rapide nella finestra di dialogo **Opzioni** in **Editor di testo** > **C/C++** > **Avanzate** > **Informazioni rapide automatiche**.

![QuickInfo di Visual C&#43;&#43;](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

### <a name="error-squiggles"></a>Sottolineatura a zigzag per gli errori

La presenza di una sottolineatura a zigzag sotto un elemento di programma (variabile, parola chiave, parentesi, nome di tipo e così via) serve a richiamare l'attenzione su un errore effettivo o potenziale nel codice. La sottolineatura a zigzag di colore verde appare quando si scrive una dichiarazione con prototipo per ricordare che non è ancora stata scritta l'implementazione. La sottolineatura a zigzag di colore viola appare in un progetto condiviso quando è presente un errore in codice attualmente non attivo, ad esempio quando si lavora nel contesto Windows ma si scrive codice errato in un contesto Android. La sottolineatura a zigzag di colore rosso indica che nel codice attivo è presente un errore o un avviso che è necessario risolvere.

![Controllo ortografia durante la digitazione di Visual C&#43;&#43;](../ide/media/vs2015_cpp_error_quiggles.png "vs2015_cpp_error_quiggles")

### <a name="code-colorization-and-fonts"></a>Tipi di carattere e colori del codice

I colori predefiniti e i caratteri possono essere modificati nella finestra di dialogo **Opzioni** in **Ambiente** > **Tipi di carattere e colori**. In questa pagina è possibile modificare i tipi di carattere per molte finestre dell'interfaccia utente, non solo per l'editor. Le impostazioni specifiche di C++ iniziano con "C++", mentre le altre impostazioni sono valide per tutti i linguaggi.

### <a name="cross-platform-intellisense"></a>IntelliSense multipiattaforma

In un progetto di codice condiviso, alcune funzionalità di IntelliSense come la sottolineatura a zigzag sono disponibili anche quando si lavora in un contesto Android. Se si scrive codice che causa un errore in un progetto inattivo, IntelliSense mostra comunque la sottolineatura a zigzag, ma in un colore diverso rispetto a quello della sottolineatura a zigzag per gli errori nel contesto corrente.

Di seguito un'applicazione OpenGLES configurata per la compilazione per Android e iOS. Nell’illustrazione viene mostrato il codice condiviso modificato. Nella prima immagine, Android è il progetto attivo:

![Il progetto Android è il progetto attivo.](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")

Tenere presente quanto segue:

- Il ramo #else sulla riga 8 è visualizzato in grigio per indicare l'area inattiva, perché __ANDROID\_\_ è definito per il progetto Android.

- La variabile di saluto sulla riga 11 viene inizializzata con l’identificatore HELLO, che ha una sottolineatura a zig-zag di colore viola. Ciò è dovuto al fatto che nessun identificatore HELLO è definito nel progetto iOS attualmente inattivo. Mentre nel progetto Android la riga 11 verrebbe compilata, non funzionerebbe in iOS. Poiché si tratta di codice condiviso, elemento che è necessario modificare anche se viene compilato nella configurazione attualmente attiva.

- La riga 12 ha una sottolineatura rossa a zig-zag sull'identificatore BYE; tale identificatore non è definito nel progetto attivo correntemente selezionato.

A questo punto, impostare il progetto attivo su iOS.StaticLibrary e osservare come cambiano le sottolineature a zig-zag.

![iOS è selezionato come progetto attivo.](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")

Tenere presente quanto segue:

- Il ramo #ifdef sulla riga 6 è visualizzato in grigio per indicare l'area inattiva, perché __ANDROID\_\_ non è definito per il progetto iOS.

- La variabile di saluto sulla riga 11 viene inizializzata con l’identificatore HELLO, che ora ha una sottolineatura a zig-zag di colore rosso. Ciò è dovuto al fatto che nessun identificatore HELLO è definito nel progetto iOS attualmente attivo.

- La riga 12 ha una sottolineatura a zig-zag di colore viola sull’identificatore BYE; tale identificatore non è definito nel progetto Android.NativeActivity attualmente inattivo.

### <a name="intellisense-for-stand-alone-files"></a>IntelliSense per file autonomi

IntelliSense è disponibile anche quando si apre un singolo file all'esterno di qualsiasi progetto. È possibile abilitare o disabilitare particolari funzionalità IntelliSense nella finestra di dialogo **Opzioni** in **Editor di testo** > **C/C++** > **Avanzate**. Per configurare IntelliSense per singoli file che non fanno parte di un progetto, vedere la sezione **IntelliSense ed esplorazione per file non di progetto**.

![Intellisense per singolo file Visual C&#43;&#43;](../ide/media/vs2015_cpp_single_file_intellisense.png "vs2015_cpp_single_file_intellisense")

Per impostazione predefinita, IntelliSense con singolo file utilizza solo directory di inclusione per trovare i file di intestazione. Per aggiungere ulteriori directory, aprire il menu di scelta rapida del nodo della soluzione e aggiungere la directory all’elenco relativo al **codice sorgente di debug**, come illustrato nella figura seguente:

![Aggiunta di un percorso a un file di intestazione.](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")

## <a name="see-also"></a>Vedere anche

[Utilizzo di IntelliSense](../ide/using-intellisense.md)