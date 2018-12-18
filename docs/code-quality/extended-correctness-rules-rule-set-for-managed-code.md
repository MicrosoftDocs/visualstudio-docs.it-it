---
title: Set di regole estese di correttezza per codice gestito
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: ccee4f6e139ef502a90a13a231c65f7e87141c78
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Set di regole estese di correttezza per codice gestito
Il set di regole regole estese di correttezza Microsoft ottimizza la logica e i framework utilizzo gli errori restituiti dall'analisi del codice. Attenzione è rivolta a scenari specifici, ad esempio l'interoperabilità COM e applicazioni per dispositivi mobili. È consigliabile inclusi in questo set di regole se uno di questi scenari si applica al progetto o per individuare ulteriori problemi nel progetto.

 Il set di regole regole estese di correttezza Microsoft include le regole impostate nella regola regole base di correttezza Microsoft. Regole base di correttezza includono le regole impostate nella regola di regole minime consigliate Microsoft. Per altre informazioni, vedere [del set di regole regole base di correttezza per codice gestito](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) e [del set di regole regole consigliate gestite per codice gestito](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 Nella tabella seguente vengono descritte tutte le regole nel set di regole regole estese di correttezza Microsoft.

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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Gli enum devono avere valore zero|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Overload di operatore equals all'overload di addizione e sottrazione|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Non passare valori letterali come parametri localizzati|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizzare le stringhe in lettere maiuscole|
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Non ignorare i risultati (metodo)|
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Chiamare GC. SuppressFinalize correttamente|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Proprietà non devono restituire matrici|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testare le stringhe vuote utilizzando la lunghezza della stringa|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Utilizzare solo API .NET framework di destinazione|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Rimuovere le chiamate a GC. KeepAlive|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Utilizzare SafeHandle per incapsulare le risorse native|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Intercettare le eccezioni non CLSCompliant nei gestori generali|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Non dichiarare tipi di riferimento modificabili in sola lettura|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|I campi di matrici non devono essere sola lettura|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Asserzioni protette|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Chiamare GC. KeepAlive durante l'utilizzo di risorse native|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Sealed i metodi che soddisfano interfacce private|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Proteggere i costruttori di serializzazione|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Costruttori statici devono essere privati|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Le costanti SecurityCritical devono essere transparent|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilizzare equivalenti gestiti dell'API Win32|
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Metodi Dispose devono chiamare dispose della classe base|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|I finalizzatori devono essere protetti.|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Non diminuire la visibilità di membri ereditati|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Membri devono limitarsi al tipo restituito più di|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Override di equals all'overload dell'operatore uguale a|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Gli operatori devono avere overload simmetrici|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Le proprietà della raccolta devono essere di sola lettura|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Fornire metodi di deserializzazione per i campi facoltativi|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementare costruttori di eccezioni standard|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|I parametri URI non devono essere stringhe|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI restituiscono valori non devono essere stringhe|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Proprietà URI non devono essere stringhe|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Stringa chiamano gli overload System. Uri|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Evitare gli overload nelle interfacce visibili a COM|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Evitare gli argomenti Int64 per i client Visual Basic 6|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Evitare i membri statici nei tipi visibili a COM|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Non utilizzare AutoDual ClassInterfaceType|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Tipi visibili a COM devono essere creabili|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Metodi di registrazione COM non devono essere visibili|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Contrassegnare le interfacce ComSource come IDispatch|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Evitare i campi non pubblici nei tipi valore visibili a COM|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Contrassegnare gli argomenti P/Invoke booleani con MarshalAs|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Non utilizzare priorità del processo su inattivo|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Non utilizzare i timer che impediscono le modifiche dello stato di alimentazione|
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Contrassegnare gli assembly con NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Evitare chiamate a metodi problematici|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Non considerare i fiber come i thread|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Gli assembly di livello 2 non devono contenere LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|I membri non devono avere annotazioni di trasparenza in conflitto|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|I metodi Transparent non possono utilizzare l'attributo HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Il codice Transparent non deve essere protetto con LinkDemand|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|I metodi Transparent non devono utilizzare SecurityDemand|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Il codice Transparent non deve caricare assembly da matrici di byte|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|I metodi Transparent non devono essere decorati con SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Valori letterali devono essere digitati correttamente|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|I campi non costanti non devono essere visibili|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Non contrassegnare le enumerazioni con FlagsAttribute|
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Eseguire l'override di GetHashCode all'override di Equals|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Non generare eccezioni in clausole di eccezione|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Overload degli operatori hanno alternative con nome|
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Non fornire formati di risorse non rilasciati|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Utilizzare params per argomenti variabili|
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|Evitare l'overflow delle operazioni|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Passare oggetti System. Uri invece di stringhe|
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Valori letterali di stringa di attributo devono essere analizzate correttamente|