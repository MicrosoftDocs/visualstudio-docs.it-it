---
title: IntelliSense per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 88ee47502d0aa15e391155cae918c8e579e72194
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="using-intellisense-in-visual-studio"></a>Uso di IntelliSense in Visual Studio

IntelliSense è il termine generale per numerose funzionalità: Elenca membri, Informazioni sul parametro, Informazioni rapide e Completa parola. Queste funzionalità consentono di acquisire altre informazioni sul codice in uso, tengono traccia dei parametri che si digitano e aggiungono le chiamate a proprietà e metodi con poche sequenze di tasti.

Molti aspetti di IntelliSense sono specifici del linguaggio. Per altre informazioni su IntelliSense per linguaggi diversi, vedere gli argomenti elencati nella sezione [Vedere anche](#see-also).

## <a name="list-members"></a>Elenca membri

Un elenco di membri validi di un tipo (o dello spazio dei nomi) viene visualizzato dopo avere digitato un carattere del trigger, ad esempio un punto (`.`) nel codice gestito o `::` in C++. Se si continua a digitare caratteri, l'elenco viene filtrato per includere solo i membri o una *qualsiasi* parola all'interno del nome che iniziano con tali caratteri. IntelliSense esegue anche la corrispondenza con notazione Camel, pertanto è possibile digitare solo la prima lettera di ogni parola con notazione Camel nel nome del membro per visualizzare le corrispondenze.

Dopo avere selezionato un elemento, è possibile inserirlo nel codice premendo **Tab** o digitando uno spazio. Se si seleziona un elemento e si digita un punto, l'elemento viene visualizzato seguito dal punto; questa condizione comporta la visualizzazione di un altro elenco di membri. Quando si seleziona un elemento ma prima di inserirlo, vengono visualizzate informazioni rapide per l'elemento.

Nell'elenco dei membri, l'icona a sinistra rappresenta il tipo del membro, ad esempio spazio dei nomi, classe, funzione o variabile. Per un elenco di icone, vedere [Icone di Visualizzazione classi e Visualizzatore oggetti](../ide/class-view-and-object-browser-icons.md). L'elenco può essere piuttosto lungo, pertanto è possibile premere **PGSU** e **PGGIÙ** per spostarsi rispettivamente verso l'alto o verso il basso nell'elenco.

![Elenco dei membri di Visual Studio](../ide/media/vs2015_intellisense.png "vs2015_Intellisense")

È possibile chiamare la funzionalità **Elenca membri** manualmente digitando **CTRL** + **J**, scegliendo **Modifica** > **IntelliSense** > **Elenca membri** o il pulsante **Elenca membri** sulla barra degli strumenti dell'editor. Se richiamato in una riga vuota o al di fuori di un ambito riconoscibile, l'elenco conterrà simboli dello spazio dei nomi globale.

Per disattivare la funzionalità Elenca membri per impostazione predefinita, in modo che sia presente solo se specificamente chiamata, passare a **Strumenti** > **Opzioni** > **Tutti i linguaggi** e deselezionare **Elenco membri automatico**. Se si vuole disattivare la funzionalità Elenca membri solo per un linguaggio specifico, andare sulle impostazioni **Generali** per quel linguaggio.

È inoltre possibile modificare la modalità di suggerimento, in cui solo il testo digitato viene inserito nel codice. Ad esempio, se si immette un identificatore non presente nell'elenco e si preme **Tab**, in modalità di completamento la voce sostituisce l'identificatore digitato. Per passare dalla modalità di completamento alla modalità di suggerimento e viceversa, premere **CTRL** + **ALT** + **BARRA SPAZIATRICE** o scegliere **Modifica** > **IntelliSense** > **Attiva/Disattiva modalità di terminazione**.

## <a name="parameter-info"></a>Informazioni sul parametro

Informazioni sul parametro fornisce informazioni relative al numero, ai nomi e ai tipi di parametri richiesti da un metodo, un parametro di tipo generico di attributo (in C#) o da un modello (in C++).

Il parametro in grassetto indica il parametro successivo richiesto durante la digitazione della funzione. Per le funzioni in overload, è possibile usare i tasti FRECCIA SU e FRECCIA GIÙ per visualizzare informazioni sui parametri alternativi per gli overload della funzione.

![Informazioni sul parametro](../ide/media/vs2015_param_info.png "VS2015_param_Info")

Se si annotano funzioni e parametri con commenti relativi alla documentazione XML, i commenti verranno visualizzati come informazioni sui parametri. Per altre informazioni, vedere [Inserimento di commenti al codice XML](../ide/supplying-xml-code-comments.md).

È possibile chiamare manualmente le informazioni sul parametro scegliendo **Modifica** > **IntelliSense** > **Informazioni sul parametro**, premendo **CTRL** + **MAIUSC** + **BARRA SPAZIATRICE** oppure scegliendo il pulsante **Informazioni sul parametro** sulla barra degli strumenti dell'editor.

## <a name="quick-info"></a>Informazioni rapide

Informazioni rapide visualizza la dichiarazione completa per ogni identificatore incluso nel codice.

![Informazioni rapide di Visual Studio](../ide/media/vs2015_quick_info.png "VS2015_Quick_info")

Quando si seleziona un membro nella casella **Elenca membri**, vengono visualizzate anche le informazioni rapide.

![Informazioni sul parametro in C&#35; file di codice](../ide/media/vs2015_paraminfo.png "VS2015_ParamInfo")

È possibile chiamare manualmente le informazioni rapide scegliendo **Modifica** > **IntelliSense** > **Informazioni rapide**, premendo **CTRL** + **I** o scegliendo il pulsante **Informazioni rapide** sulla barra degli strumenti dell'editor.

Se una funzione è sottoposta a overload, è possibile che IntelliSense non visualizzi le informazioni per tutte le forme di overload.

È possibile disattivare le informazioni rapide per il codice C++ tramite **Strumenti** > **Opzioni** > **Editor di testo** > **C/C++** > **Avanzate**, impostando **Informazioni rapide automatiche** su `false`.

## <a name="complete-word"></a>Completa parola

Completa parola completa la digitazione del nome di una variabile, di un comando o di una funzione dopo che sono stati immessi caratteri sufficienti a identificare il termine in modo univoco. È possibile richiamare Completa parola scegliendo **Modifica** > **IntelliSense** > **Completa parola**, premendo **CTRL**+**BARRA SPAZIATRICE** oppure scegliendo il pulsante **Completa parola** sulla barra degli strumenti dell'editor.

## <a name="intellisense-options"></a>Opzioni IntelliSense

Le opzioni IntelliSense sono attive per impostazione predefinita. Per disattivarle, scegliere **Strumenti** > **Opzioni** > **Editor di testo** e deselezionare **Informazioni parametri** o **Elenco membri automatico** se non si vuole usare la funzionalità Elenca membri.

## <a name="troubleshooting-intellisense"></a>Risoluzione dei problemi relativi a IntelliSense

Le opzioni IntelliSense potrebbero non funzionare come previsto, in alcuni casi.

**Il cursore si trova sotto un errore del codice.** Non è possibile usare IntelliSense se una funzione incompleta o un altro errore esiste nel codice sopra il cursore perché IntelliSense potrebbe non essere in grado di analizzare gli elementi di codice. È possibile risolvere questo problema commentando il codice applicabile.

**Il cursore si trova in un commento del codice.** Non è possibile usare IntelliSense se il cursore si trova in un commento nel file di origine.

**Il cursore si trova in un valore letterale stringa.** Non è possibile usare IntelliSense se il cursore si trova tra virgolette intorno a un valore letterale stringa, come nel seguente esempio:

```cpp
MessageBox( hWnd, "String literal|")
```

**Le opzioni automatiche sono disattivate.** Per impostazione predefinita, il funzionamento di IntelliSense è automatico, ma è possibile disabilitarlo. Anche se il completamento automatico delle istruzioni è disabilitato, è possibile richiamare una funzionalità IntelliSense.

## <a name="see-also"></a>Vedere anche

[IntelliSense per Visual Basic](../ide/visual-basic-specific-intellisense.md)  
[IntelliSense per C#](../ide/visual-csharp-intellisense.md)  
[IntelliSense per JavaScript](../ide/javascript-intellisense.md)  
[Scrittura e refactoring del codice (C++)](/cpp/ide/writing-and-refactoring-code-cpp)  
[Inserimento di commenti al codice XML](../ide/supplying-xml-code-comments.md)
