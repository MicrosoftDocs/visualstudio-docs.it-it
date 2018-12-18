---
title: Set di regole consigliate gestite per codice gestito
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3f15fc1859e0b7b8f3e3d7dc4bcf7fb315690734
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Set di regole consigliate gestite per codice gestito
È possibile utilizzare le regole consigliate gestite Microsoft set di regole per concentrarsi sui problemi più critici del codice gestito, inclusi potenziali problemi di sicurezza, arresti anomali delle applicazioni e altri errori di logica e di progettazione rilevanti. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti.

|Regola|Descrizione|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|I tipi proprietari di campi disposable devono essere disposable|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Dichiarare correttamente i gestori eventi|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Contrassegnare gli assembly con AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Metodi di interfaccia devono essere richiamabili dai tipi figlio|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Tipi di risorse native devono essere disposable|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Spostare i P/Invoke nella classe NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Non nascondere i metodi della classe base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementare IDisposable correttamente|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Non generare eccezioni in posizioni|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitare tasti di scelta rapida duplicati|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Punti di ingresso P/Invoke devono esistere|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke non devono essere visibili|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|I tipi layout automatici non devono essere visibile a COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Chiamare GetLastError immediatamente dopo P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Tipi di base di tipo visibile a COM devono essere visibili a COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Metodi di registrazione COM devono corrispondere|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Dichiarare correttamente i P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Rimuovere i finalizzatori vuoti|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Campi dei tipi di valore devono essere portabili|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Le dichiarazioni P/Invoke devono essere portabili|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Non bloccare oggetti con identità debole|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Esaminare le query SQL per le vulnerabilità di sicurezza|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Specificare il marshalling per gli argomenti di stringa P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Controllare la sicurezza dichiarativa sui tipi di valore|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|I puntatori non devono essere visibili|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|I tipi protetti non devono esporre campi|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Sicurezza del metodo deve essere un superset del tipo|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|I metodi APTCA devono chiamare solo metodi APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|I tipi APTCA devono estendere solo tipi di base APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Non esporre in modo indiretto metodi con richieste di collegamento|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Le richieste di collegamento di override devono essere identiche a base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incapsulamento vulnerabile delle clausole finally in esterno try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Le richieste di collegamento necessarie richieste di ereditarietà|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|I tipi SecurityCritical possono non partecipare all'equivalenza del tipo|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Costruttori predefiniti devono essere critici almeno come i costruttori predefiniti del tipo di base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegati devono essere associati ai metodi con trasparenza consistente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|I metodi devono conservare trasparenza consistente durante l'override dei metodi base|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|I metodi Transparent devono contenere solo IL verificabile|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Il codice Transparent non deve fare riferimento a elementi SecurityCritical|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|I metodi Transparent non devono soddisfare i LinkDemand|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|I tipi devono essere critici almeno come le interfacce e i relativi tipi di base|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|I metodi Transparent non possono utilizzare sicurezza asserzioni|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|I metodi Transparent non devono chiamare in codice nativo|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Eseguire il rethrow per conservare i dettagli dello stack|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Non eliminare oggetti più volte|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inizializzare i campi statici del tipo di valore inline|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Non contrassegnare componenti serviti con WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|I campi Disposable devono essere eliminati.|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Non chiamare metodi sottoponibili a override nei costruttori|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|I tipi eliminabili devono dichiarare un finalizzatore|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|I finalizzatori devono chiamare il finalizzatore di classe di base|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementare costruttori di serializzazione|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Overload dell'operatore è uguale all'override di ValueType. Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Punti di ingresso contrassegno Windows Form con STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Contrassegnare tutti i campi non serializzabili|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Chiamare metodi della classe di base su tipi ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Contrassegnare i tipi ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementare correttamente i metodi di serializzazione|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementare ISerializable in modo corretto|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Fornire argomenti corretti ai metodi di formattazione|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Testare i valori NaN in modo corretto|