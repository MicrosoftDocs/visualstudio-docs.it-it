---
title: IntelliSense per JavaScript |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb4d95dcc53926f7ae8b0b295b7552185a4a934c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="javascript-intellisense"></a>IntelliSense per JavaScript

[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] offre funzionalità di modifica complete di JavaScript, implementabili all'istante. Visual Studio, gestito da un servizio di linguaggio basato su TypeScript, offre una modalità IntelliSense più completa, il supporto di funzionalità JavaScript aggiornate e funzioni di produttività migliorate quali Vai a definizione, il refactoring e altro ancora.

> [!NOTE]
> Il servizio di linguaggio JavaScript in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] usa un nuovo motore (denominato "Salsa"). Per i dettagli proseguire la lettura di questo argomento. È anche possibile leggere [questo post di blog](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/more-productive-javascript-in-visual-studio-2017-rc). Le nuove funzioni di modifica si applicano principalmente anche a Visual Studio Code. Per altre informazioni vedere la [documentazione di Visual Studio Code](https://code.visualstudio.com/docs/languages/javascript).

Per altre informazioni sulla funzionalità IntelliSense generale di Visual Studio, vedere [Uso di IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Novità del servizio di linguaggio JavaScript in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

A partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] JavaScript IntelliSense visualizza più informazioni relative agli elenchi di parametri e membri.
Le nuove informazioni sono specificate dal servizio di linguaggio TypeScript, che usa l'analisi statica in background per un'interpretazione più approfondita del codice.
Per ottenere le informazioni necessarie, TypeScript usa diverse fonti:

- [IntelliSense basato sull'inferenza del tipo](#TypeInference)
- [IntelliSense basato su JSDoc](#JsDoc)
- [IntelliSense basato su file dichiarazione TypeScript](#TsDeclFiles)
- [Acquisizione automatica delle definizioni dei tipi](#Auto)

### <a name="TypeInference"></a>IntelliSense basato sull'inferenza del tipo

In JavaScript nella maggior parte dei casi non sono disponibili informazioni esplicite relative ai tipi. In genere è abbastanza semplice intuire un tipo in base al contesto del codice circostante.
Questo processo è detto inferenza del tipo.

Per una variabile o una proprietà, il tipo è in genere il tipo del valore usato per l'inizializzazione oppure l'assegnazione di un valore più recente.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Per una funzione, il tipo restituito può essere dedotto dalle istruzioni return.

Per i parametri di funzione l'inferenza non è attualmente disponibile, ma è possibile risolvere il problema mediante i file `.d.ts` JSDoc o TypeScript (vedere le sezioni successive).

È anche disponibile una funzionalità di inferenza speciale per i seguenti elementi:

- Classi "in stile ES3", specificate mediante una funzione costruttore e assegnazioni alla proprietà prototype.
- Modelli di modulo in stile CommonJS, specificati come assegnazioni di proprietà nell'oggetto `exports` oppure assegnazioni alla proprietà `module.exports`.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

### <a name="JsDoc"></a> IntelliSense basato su JSDoc

Quando l'inferenza del tipo non specifica le informazioni sul tipo desiderate (o si vuole aggiungere supporto alla documentazione), è possibile includere informazioni sul tipo in modo esplicito tramite le annotazioni JSDoc.  Ad esempio, per assegnare un tipo specifico a un oggetto parzialmente dichiarato si può usare il tag `@type` come illustrato di seguito:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Come detto, l'inferenza non è mai valida per i parametri funzione. Tuttavia con il tag JSDoc `@param` è possibile aggiungere tipi anche ai parametri funzione.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Vedere in [questo documento](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) le annotazioni JsDoc attualmente supportate.

### <a name="TsDeclFiles"></a> IntelliSense basato su file dichiarazione TypeScript

Dato che ora JavaScript e TypeScript si basano sullo stesso servizio di linguaggio, sono in grado di interagire in modo più completo. Ad esempio è possibile aggiungere codice IntelliSense JavaScript per i valori dichiarati in un file `.d.ts` ([altre informazioni](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), mentre i tipi quali interfacce e classi dichiarate in TypeScript sono disponibili per l'uso come tipi nei commenti JsDoc. 

Di seguito viene visualizzato un esempio semplice di file di definizione TypeScript che specifica questo tipo di informazioni (attraverso un'interfaccia) a un file JavaScript nello stesso progetto (mediante un tag JsDoc).

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

### <a name="Auto"></a> Acquisizione automatica delle definizioni dei tipi

Nell'ambito TypeScript, le API delle librerie JavaScript più diffuse sono descritte da file `.d.ts` e il repository più comune per tali definizioni si trova in [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Per impostazione predefinita il servizio di linguaggio Salsa prova a rilevare le librerie JavaScript in uso, quindi scarica e crea automaticamente un riferimento al file `.d.ts` corrispondente che descrive la libreria, al fine di fornire un'esecuzione IntelliSense più completa. I file vengono scaricati in una cache posta all'interno della cartella dell'utente in `%LOCALAPPDATA%\Microsoft\TypeScript`.

> [!NOTE]
> Questa funzionalità è **disabilitata** per impostazione predefinita se si usa un file di configurazione `tsconfig.json`, ma può essere impostata come abilitata con le modalità descritte di seguito.

Attualmente il rilevamento automatico funziona per le dipendenze scaricate da npm (mediante la lettura del file `package.json`), Bower (mediante la lettura del file `bower.json`) e per singoli file del progetto corrispondenti a un elenco contenente circa 400 tra le librerie JavaScript più diffuse. Se ad esempio nel progetto è presente `jquery-1.10.min.js`, verrà recuperato e caricato il file `jquery.d.ts` per garantire una funzionalità di modifica più completa. Tale file `.d.ts` non avrà alcun impatto sul progetto.

Se non si vuole usare l'acquisizione automatica, disattivarla mediante l'aggiunta di un file di configurazione, come descritto di seguito. È comunque possibile inserire manualmente file di definizione da usare direttamente nel progetto.

## <a name="see-also"></a>Vedere anche

[Utilizzo di IntelliSense](../ide/using-intellisense.md)