---
title: 'CA2109: Controllare i gestori di eventi visibili'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf11564e7420231ac6ab65c6dc00762bb4077ef2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Controllare i gestori di eventi visibili
|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 È stato rilevato un metodo di gestione eventi pubblico o protetto.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo visibile esternamente di gestione degli eventi presenta un problema di sicurezza che richiede revisione.

 I metodi di gestione eventi non devono essere esposti se non assolutamente necessario. Un gestore eventi, un tipo delegato, che richiama il metodo esposto può aggiunti a qualsiasi evento purché le firme del gestore ed evento corrispondano. Gli eventi possono potenzialmente essere generati da qualsiasi codice e vengono spesso generati dal codice di sistema altamente attendibile in risposta alle azioni dell'utente, ad esempio un pulsante. Aggiunta di un controllo di sicurezza a un metodo di gestione degli eventi non impedisce al codice di registrazione di un gestore eventi che richiama il metodo.

 Una richiesta non è possibile proteggere in modo affidabile un metodo richiamato da un gestore eventi. Richieste di sicurezza consentono il codice dai chiamanti non attendibili esaminando i chiamanti nello stack di chiamate. Codice che aggiunge un gestore eventi a un evento non è necessariamente presente nello stack di chiamate durante l'esecuzione dei metodi del gestore eventi. Pertanto, lo stack di chiamate potrebbe contenere solo chiamanti altamente attendibili quando viene richiamato il metodo del gestore eventi. In questo modo di richieste eseguite dal metodo del gestore eventi abbia esito positivo. Inoltre, quando viene richiamato il metodo potrebbe asserire l'autorizzazione richiesta. Per questi motivi, il rischio di non correggere una violazione di questa regola può essere valutato solo dopo aver esaminato il metodo di gestione degli eventi. Quando si verifica il codice, tenere presente quanto segue:

-   Il gestore eventi esegue tutte le operazioni pericolose o vulnerabile, ad esempio l'asserzione delle autorizzazioni o l'eliminazione di autorizzazioni di codice non gestito?

-   Quali sono le minacce alla sicurezza da e verso il codice, poiché possono essere eseguiti in qualsiasi momento con solo altamente attendibili i chiamanti nello stack?

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, controllare il metodo e valutare quanto segue:

-   Sarà possibile rendere il metodo di gestione degli eventi non pubblici?

-   È possibile spostare tutte le funzionalità pericolose fuori il gestore dell'evento?

-   Se una richiesta di sicurezza viene imposto, possa essere eseguita in altro modo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola solo dopo un'attenta revisione della sicurezza per assicurarsi che il codice non costituisce una minaccia alla sicurezza.

## <a name="example"></a>Esempio
 Il codice seguente viene illustrato un metodo di gestione degli eventi che può essere usato in modo improprio da codice dannoso.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
