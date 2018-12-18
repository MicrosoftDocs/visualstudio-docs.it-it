---
title: Configurazione degli avvisi in Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 265d86365c9084dac9d75a04df1e1ea243b3b585
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="configuring-warnings-in-visual-basic"></a>Configurazione degli avvisi in Visual Basic
Il compilatore di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] include un set di avvisi relativi al codice che può causare errori di runtime. È possibile usare tali informazioni per scrivere codice migliore, più semplice e rapido e con meno errori. Ad esempio il compilatore genera un avviso quando l'utente cerca di chiamare un membro di una variabile di oggetto non assegnata, di completare l'esecuzione di una funzione senza impostare il valore restituito o di eseguire un blocco `Try` con errori nel codice per l'intercettazione delle eccezioni.  
  
 In alcuni casi il compilatore produce codice aggiuntivo per conto dell'utente, che potrà concentrarsi sul task corrente anziché sulla necessità di prevedere possibili errori. Le versioni precedenti di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] usavano **Option Strict** per limitare il codice aggiuntivo prodotto dal compilatore [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. La configurazione degli avvisi consente di limitare tale codice in modo più dettagliato, a livello dei singoli avvisi.  
  
 Può risultare utile personalizzare il progetto, disattivare gli avvisi non pertinenti all'applicazione e trasformare altri avvisi in errori. Questa pagina illustra come attivare e disattivare i singoli avvisi.  
  
## <a name="turning-warnings-off-and-on"></a>Attivare e disattivare gli avvisi  
 Esistono due modi per configurare gli avvisi: è possibile configurarli con **Creazione progetti** o mediante le opzioni del compilatore **/warnaserror** e **/nowarn**.  
  
 La scheda **Compila** della pagina **Creazione progetti** consente di attivare e disattivare gli avvisi. Selezionare la casella di controllo **Disabilita tutti gli avvisi** per disabilitare tutti gli avvisi. Selezionare **Considera tutti gli avvisi come errori** per considerare tutti gli avvisi come errori. Alcuni avvisi singoli possono essere impostati come errori o come avvisi in base alle esigenze nella tabella visualizzata.  
  
 Quando **Option Strict** è impostato su **Off**, gli avvisi associati a **Option Strict** non possono essere elaborati individualmente. Quando **Option Strict** è impostato su **On**, gli avvisi associati vengono considerati come errori, indipendentemente dal loro stato. Quando **Option Strict** è impostato su **Custom** specificando `/optionstrict:custom` nel compilatore della riga di comando, gli avvisi **Option Strict** possono essere attivati o disattivati in modo indipendente.  
  
 L'opzione della riga di comando **/warnaserror** del compilatore consente anche di specificare se gli avvisi vengono considerati come errori. È possibile aggiungere un elenco delimitato da virgole a questa opzione per specificare mediante i segni + o - gli avvisi da considerare come errori o come avvisi. La seguente tabella elenca le opzioni possibili.  
  
|Opzione della riga di comando|Specifica|  
|--------------------------|---------------|  
|`/warnaserror+`|Considera tutti gli avvisi come errori.|  
|`/warnsaserror`-|Non considera gli avvisi come errori. Questa è l'impostazione predefinita.|  
|`/warnaserror+:<warning list` `>`|Considera come errori gli avvisi specifici elencati in base al numero ID dell'errore in un elenco delimitato da virgole.|  
|`/warnaserror-:<warning list>`|Non considera come errori gli avvisi specifici elencati in base al numero ID dell'errore in un elenco delimitato da virgole.|  
|`/nowarn`|Non segnala gli avvisi.|  
|`/nowarn:<warning list>`|Non segnala gli avvisi specifici elencati in base al numero ID dell'errore in un elenco delimitato da virgole.|  
  
 L'elenco degli avvisi contiene i numeri ID errore degli avvisi da considerare come errori, usabili con le opzioni della riga di comando per attivare o disattivare avvisi specifici. Se l'elenco degli avvisi contiene un numero non valido, viene restituito un errore.  
  
## <a name="examples"></a>Esempi  
 Questa tabella di esempi di argomenti della riga di comando descrive la funzione di ogni argomento.  
  
|Argomento|Descrizione|  
|--------------|-----------------|  
|`vbc /warnaserror`|Specifica di considerare tutti gli avvisi come errori.|  
|`vbc /warnaserror:42024`|Specifica che l'avviso 42024 va considerato come errore.|  
|`vbc /warnaserror:42024,42025`|Specifica che gli avvisi 42024 e 42025 vanno considerati come errori.|  
|`vbc /nowarn`|Specifica che non deve essere segnalato alcun avviso.|  
|`vbc /nowarn:42024`|Specifica che l'avviso 42024 non deve essere segnalato.|  
|`vbc /nowarn:42024,42025`|Specifica che gli avvisi 42024 e 42025 non devono essere segnalati.|  
  
## <a name="types-of-warnings"></a>Tipi di avvisi  
 L'elenco che segue include avvisi che possono essere considerati come errori.  
  
### <a name="implicit-conversion-warning"></a>Avviso di conversione implicita  
 Viene generato per istanze di conversione implicita. Tali istanze non includono le conversioni implicite da un tipo numerico intrinseco a una stringa quando si usa l'operatore `&`. L'impostazione predefinita per i nuovi progetti è Off (disattivato).  
  
 ID: 42016  
  
### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Avviso di chiamata metodo di associazione tardiva e risoluzione dell'overload  
 Viene generato per istanze di associazione tardiva. L'impostazione predefinita per i nuovi progetti è Off (disattivato).  
  
 ID: 42017  
  
### <a name="operands-of-type-object-warnings"></a>Avvisi per operandi di tipo Object  
 Vengono generati quando appaiono operandi di tipo `Object` che potrebbero generare un errore con **Option Strict On**. L'impostazione predefinita per i nuovi progetti è On (attivato).  
  
 ID: 42018 e 42019  
  
### <a name="declarations-require-as-clause-warnings"></a>Avvisi per dichiarazioni che richiedono la clausola As  
 Vengono generati quando la dichiarazione di una variabile, una funzione o una proprietà priva di una clausola `As` darebbe origine a un errore con **Option Strict On**. Le variabili senza un tipo assegnato vengono considerate di tipo `Object`. L'impostazione predefinita per i nuovi progetti è On (attivato).  
  
 ID: 42020 (dichiarazione di variabile), 42021 (dichiarazione di funzione) e 42022 (dichiarazione di proprietà).  
  
### <a name="possible-null-reference-exception-warnings"></a>Avvisi di eccezione per possibili riferimenti null  
 Vengono generati quando una variabile viene usata prima di ricevere l'assegnazione di un valore. L'impostazione predefinita per i nuovi progetti è On (attivato).  
  
 ID: 42104, 42030  
  
### <a name="unused-local-variable-warning"></a>Avviso di variabile locale non usata  
 Viene generato quando una variabile locale viene dichiarata ma non dispone di nessun riferimento. L'impostazione predefinita è On (attivato).  
  
 ID: 42024  
  
### <a name="access-of-shared-member-through-instance-variable-warning"></a>Avviso di accesso a un membro condiviso tramite una variabile di istanza  
 Viene generato quando l'accesso a un membro condiviso tramite un'istanza può avere effetti collaterali o quando l'accesso a un membro condiviso tramite una variabile di istanza non è il lato destro di un'espressione o viene passato come parametro. L'impostazione predefinita per i nuovi progetti è On (attivato).  
  
 ID: 42025  
  
### <a name="recursive-operator-or-property-access-warnings"></a>Avvisi di accesso ricorsivo a un operatore o una proprietà  
 Vengono generati quando il corpo di una routine usa lo stesso operatore o la stessa proprietà in cui è definito. L'impostazione predefinita per i nuovi progetti è On (attivato).  
  
 ID: 42004 (operatore), 42026 (proprietà)  
  
### <a name="function-or-operator-without-return-value-warning"></a>Avviso di funzione o operatore senza valore restituito  
 Viene generato quando per una funzione o un operatore non è specificato un valore restituito. Ciò include l'omissione di un'istruzione `Set` alla variabile locale implicita con lo stesso nome della funzione. L'impostazione predefinita per i nuovi progetti è On (attivato).  
  
 ID: 42105 (funzione), 42016 (operatore)  
  
### <a name="overloads-modifier-used-in-a-module-warning"></a>Avviso di modificatore Overloads usato in un modulo  
 Viene generato quando il modificatore `Overloads` viene usata in `Module`. L'impostazione predefinita per i nuovi progetti è On (attivato).  
  
 ID: 42028  
  
### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Avvisi per blocchi catch duplicati o sovrapposti  
 Viene generato quando un blocco `Catch` non viene mai raggiunto perché è correlato ad altri blocchi `Catch` definiti. L'impostazione predefinita per i nuovi progetti è On (attivato).  
  
 ID: 42029, 42031  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di errore](/dotnet/visual-basic/programming-guide/language-features/error-types)   
 [Istruzione Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)   
 [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)   
 [Pagina Compilazione, Creazione progetti (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Avvisi del compilatore disattivati per impostazione predefinita](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)