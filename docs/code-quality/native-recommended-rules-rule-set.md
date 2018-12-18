---
title: Set di regole consigliate native
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a2fff799001f9fdffb9dde52785e08239d363d9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="native-recommended-rules-rule-set"></a>Set di regole consigliate native

Le regole consigliate Native orientate ai problemi più critici e comuni nel codice nativo, inclusi potenziali problemi di sicurezza e arresti anomali delle applicazioni. È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.

|Regola|Descrizione|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Utilizzo di memoria non inizializzata|
|[C6011](../code-quality/c6011.md)|Dereferenziazione del puntatore Null|
|[C6029](../code-quality/c6029.md)|Utilizzo del valore non verificato|
|[C6031](../code-quality/c6031.md)|Valore restituito ignorato|
|[C6053](../code-quality/c6053.md)|Terminazione zero da chiamata|
|[C6054](../code-quality/c6054.md)|Zero terminazione mancante|
|[C6059](../code-quality/c6059.md)|Concatenazione non valida|
|[C6063](../code-quality/c6063.md)|Argomento stringa mancante per formattare la funzione|
|[C6064](../code-quality/c6064.md)|Argomento Integer mancante per formattare la funzione|
|[C6066](../code-quality/c6066.md)|Argomento puntatore mancante per formattare la funzione|
|[C6067](../code-quality/c6067.md)|Argomento puntatore stringa mancante per formattare la funzione|
|[C6101](../code-quality/c6101.md)|Restituzione di memoria non inizializzata|
|[C6200](../code-quality/c6200.md)|L'indice supera il limite massimo del buffer|
|[C6201](../code-quality/c6201.md)|L'indice supera il limite massimo del buffer di stack|
|[C6214](../code-quality/c6214.md)|Cast non valido HRESULT a BOOL|
|[C6215](../code-quality/c6215.md)|Cast di BOOL a HRESULT non valido|
|[C6216](../code-quality/c6216.md)|Cast inserito dal compilatore non valido a BOOL a HRESULT|
|[C6217](../code-quality/c6217.md)|Test HRESULT non valido con NOT|
|[C6220](../code-quality/c6220.md)|Confronto HRESULT non valido a -1|
|[C6226](../code-quality/c6226.md)|Assegnazione HRESULT non valido per -1|
|[C6230](../code-quality/c6230.md)|Uso HRESULT non valido come valore booleano|
|[C6235](../code-quality/c6235.md)|Costante non Zero con Logical- o|
|[C6236](../code-quality/c6236.md)|Logica- o con costante Non Zero|
|[C6237](../code-quality/c6237.md)|Zero con Logical- And senza effetti collaterali|
|[C6242](../code-quality/c6242.md)|Rimozione locale forzata|
|[C6248](../code-quality/c6248.md)|Creazione elenco DACL|
|[C6250](../code-quality/c6250.md)|Descrittori di indirizzo non rilasciati|
|[C6255](../code-quality/c6255.md)|Uso non protetto di allocazione|
|[C6258](../code-quality/c6258.md)|Utilizzando terminare Thread|
|[C6259](../code-quality/c6259.md)|Il codice In bit per bit- o limitate commutatore|
|[C6260](../code-quality/c6260.md)|Uso dell'aritmetica Byte|
|[C6262](../code-quality/c6262.md)|Utilizzo eccessivo dello Stack|
|[C6263](../code-quality/c6263.md)|Uso di allocazione In ciclo|
|[C6268](../code-quality/c6268.md)|Parentesi mancanti In Cast|
|[C6269](../code-quality/c6269.md)|Dereferenziazione del puntatore ignorato|
|[C6270](../code-quality/c6270.md)|Argomento Float mancante per formattare la funzione|
|[C6271](../code-quality/c6271.md)|Argomento aggiuntivo per formattare la funzione|
|[C6272](../code-quality/c6272.md)|Argomento non Float per formattare la funzione|
|[C6273](../code-quality/c6273.md)|Argomento non Integer per formattare la funzione|
|[C6274](../code-quality/c6274.md)|Argomento non Character per formattare la funzione|
|[C6276](../code-quality/c6276.md)|Cast stringa non valido|
|[C6277](../code-quality/c6277.md)|Chiamata CreateProcess non valida|
|[C6278](../code-quality/c6278.md)|Mancata corrispondenza array-New Scalar-Delete|
|[C6279](../code-quality/c6279.md)|Mancata corrispondenza di matrice scalare-New-Delete|
|[C6280](../code-quality/c6280.md)|Mancata corrispondenza tra la deallocazione di allocazione di memoria|
|[C6281](../code-quality/c6281.md)|Precedenza di relazione bit per bit|
|[C6282](../code-quality/c6282.md)|Assegnazione sostituisce Test|
|[C6283](../code-quality/c6283.md)|Mancata corrispondenza di primitivo Array-New Scalar-Delete|
|[C6284](../code-quality/c6284.md)|Argomento di oggetto non valido per formattare la funzione|
|[C6285](../code-quality/c6285.md)|Logica- o di costanti|
|[C6286](../code-quality/c6286.md)|Diverso da Zero logico- o perdita di effetti collaterali|
|[C6287](../code-quality/c6287.md)|Ridondante a livello Test|
|[C6288](../code-quality/c6288.md)|L'inclusione reciproca logico- ed è False|
|[C6289](../code-quality/c6289.md)|L'esclusione reciproca logico- o è True|
|[C6290](../code-quality/c6290.md)|Precedenza Logical-Not Bitwise-And|
|[C6291](../code-quality/c6291.md)|Precedenza Logical-Not Bitwise-Or|
|[C6292](../code-quality/c6292.md)|Conteggi cicli dalla massimo|
|[C6293](../code-quality/c6293.md)|Conteggi cicli dal minimo|
|[C6294](../code-quality/c6294.md)|Corpo ciclo mai eseguito|
|[C6295](../code-quality/c6295.md)|Ciclo infinito|
|[C6296](../code-quality/c6296.md)|Ciclo eseguito solo una volta|
|[C6297](../code-quality/c6297.md)|Risultato dello Shift a eseguire il Cast di dimensioni maggiori|
|[C6299](../code-quality/c6299.md)|Campo di bit a confronto booleano|
|[C6302](../code-quality/c6302.md)|Argomento stringa di caratteri non valido per formattare la funzione|
|[C6303](../code-quality/c6303.md)|Argomento stringa di caratteri wide non valido per formattare la funzione|
|[C6305](../code-quality/c6305.md)|Uso dimensione e conteggio non corrispondente|
|[C6306](../code-quality/c6306.md)|Chiamata di funzione dell'argomento variabile non corretto|
|[C6308](../code-quality/c6308.md)|Perdita realloc|
|[C6310](../code-quality/c6310.md)|Costante filtro eccezioni non valido|
|[C6312](../code-quality/c6312.md)|Eccezione continuazione ciclo esecuzione|
|[C6314](../code-quality/c6314.md)|Bit per bit- o sulla precedenza|
|[C6317](../code-quality/c6317.md)|Non non complemento|
|[C6318](../code-quality/c6318.md)|Eccezione continuare la ricerca|
|[C6319](../code-quality/c6319.md)|Ignorato da virgola|
|[C6324](../code-quality/c6324.md)|Copia stringa invece di confronto tra stringhe|
|[C6328](../code-quality/c6328.md)|Tipo argomento potenzialmente non corrispondente|
|[C6331](../code-quality/c6331.md)|Flag non valido di VirtualFree|
|[C6332](../code-quality/c6332.md)|Parametro non valido di VirtualFree|
|[C6333](../code-quality/c6333.md)|Dimensioni VirtualFree valido|
|[C6335](../code-quality/c6335.md)|Verifica una perdita di Handle del processo|
|[C6381](../code-quality/c6381.md)|Informazioni di chiusura mancante|
|[C6383](../code-quality/c6383.md)|Conteggio di elementi Byte-sovraccarico del Buffer di conteggio|
|[C6384](../code-quality/c6384.md)|Puntatore dimensioni divisione|
|[C6385](../code-quality/c6385.md)|Overrun di lettura|
|[C6386](../code-quality/c6386.md)|Overrun di scrittura|
|[C6387](../code-quality/c6387.md)|Valore parametro non valido|
|[C6388](../code-quality/c6388.md)|Valore parametro non valido|
|[C6500](../code-quality/c6500.md)|Proprietà attributo non valido|
|[C6501](../code-quality/c6501.md)|Conflitto valori di proprietà attributo|
|[C6503](../code-quality/c6503.md)|I riferimenti non possono essere Null|
|[C6504](../code-quality/c6504.md)|Null su non puntatore|
|[C6505](../code-quality/c6505.md)|MustCheck su nullo|
|[C6506](../code-quality/c6506.md)|Dimensioni buffer su non puntatore o matrice|
|[C6508](../code-quality/c6508.md)|Accesso in scrittura a costante|
|[C6509](../code-quality/c6509.md)|Restituzione utilizzati in precondizione|
|[C6510](../code-quality/c6510.md)|Null terminato su non puntatore|
|[C6511](../code-quality/c6511.md)|MustCheck deve essere Yes o No|
|[C6513](../code-quality/c6513.md)|Dimensioni elemento senza dimensione buffer|
|[C6514](../code-quality/c6514.md)|Le dimensioni del buffer superano le dimensioni della matrice|
|[C6515](../code-quality/c6515.md)|Dimensioni buffer su non puntatore|
|[C6516](../code-quality/c6516.md)|Nessuna proprietà su attributo|
|[C6517](../code-quality/c6517.md)|Dimensioni valide su buffer non leggibile|
|[C6518](../code-quality/c6518.md)|Dimensioni scrivibili su buffer non scrivibile|
|[C6522](../code-quality/c6522.md)|Tipo stringa dimensioni non valida|
|[C6525](../code-quality/c6525.md)|Percorso irraggiungibile stringa dimensioni non valida|
|[C6527](../code-quality/c6527.md)|Annotazione non valida: la proprietà 'NeedsRelease' non può essere utilizzata con valori di tipo void|
|[C6530](../code-quality/c6530.md)|Stile stringa formato non riconosciuto|
|[C6540](../code-quality/c6540.md)|L'utilizzo delle annotazioni di attributo in questa funzione invalida tutte le relative annotazioni __declspec|
|[C6551](../code-quality/c6551.md)|Specifica di dimensione non valida: espressione non analizzabile|
|[C6552](../code-quality/c6552.md)|Deref= o Notref= non valido: espressione non analizzabile|
|[C6701](../code-quality/c6701.md)|Il valore non è un valore Yes/No/Maybe valido|
|[C6702](../code-quality/c6702.md)|Il valore non è un valore stringa|
|[C6703](../code-quality/c6703.md)|Il valore non è un numero|
|[C6704](../code-quality/c6704.md)|Errore imprevisto dell'espressione dell'annotazione|
|[C6705](../code-quality/c6705.md)|Numero previsto di argomenti per l'annotazione non corrispondente al numero effettivo di argomenti per l'annotazione|
|[C6706](../code-quality/c6706.md)|Errore di annotazione imprevisto per l'annotazione|
|[C6995](../code-quality/c6995.md)|Impossibile salvare il file di Log XML|
|[C26100](../code-quality/c26100.md)|Condizione di competizione|
|[C26101](../code-quality/c26101.md)|Impossibilità di utilizzare correttamente l'operazione con interlock|
|[C26110](../code-quality/c26110.md)|Chiamante non riesce a mantenere il blocco|
|[C26111](../code-quality/c26111.md)|Chiamante non riesce a rilasciare il blocco|
|[C26112](../code-quality/c26112.md)|Chiamante non può contenere qualsiasi tipo di blocco|
|[C26115](../code-quality/c26115.md)|Impossibile rilasciare il blocco|
|[C26116](../code-quality/c26116.md)|Errore di acquisire o mantenere il blocco|
|[C26117](../code-quality/c26117.md)|Il rilascio del blocco si|
|[C26140](../code-quality/c26140.md)|Errore di concorrenza SAL annotazione|
|[C28020](../code-quality/c28020.md)|L'espressione non è true per questa chiamata|
|[C28021](../code-quality/c28021.md)|Il parametro annotato deve essere un puntatore|
|[C28022](../code-quality/c28022.md)|Classi di funzioni in questa funzione non corrispondono alle classi di funzioni nel typedef utilizzato per definirla.|
|[C28023](../code-quality/c28023.md)|La funzione viene assegnata o passata deve avere un _Function_class\_ annotazione per almeno uno delle classi|
|[C28024](../code-quality/c28024.md)|Puntatore a funzione assegnato è annotato con la classe di funzione, che non è contenuta nell'elenco delle classi della funzione.|
|[C28039](../code-quality/c28039.md)|Il tipo di parametro effettivo deve corrispondere esattamente al tipo|
|[C28112](../code-quality/c28112.md)|Una variabile a cui si accede tramite una funzione Interlocked deve sempre essere accessibile tramite una funzione Interlocked.|
|[C28113](../code-quality/c28113.md)|L'accesso a una variabile locale mediante una funzione Interlocked|
|[C28125](../code-quality/c28125.md)|La funzione deve essere chiamata da un blocco try / except blocco|
|[C28137](../code-quality/c28137.md)|L'argomento della variabile deve essere una costante (letterale)|
|[C28138](../code-quality/c28138.md)|L'argomento della costante deve essere variabile|
|[C28159](../code-quality/c28159.md)|Provare a utilizzare un'altra funzione.|
|[C28160](../code-quality/c28160.md)|Error (annotazione)|
|[C28163](../code-quality/c28163.md)|La funzione non dovrebbe mai essere chiamata dall'interno di un blocco try / except blocco|
|[C28164](../code-quality/c28164.md)|L'argomento è passato a una funzione che prevede un puntatore a un oggetto (non un puntatore a puntatore)|
|[C28182](../code-quality/c28182.md)|Deferenziazione del puntatore NULL. Il puntatore contiene lo stesso valore NULL contenuto in un altro puntatore.|
|[C28183](../code-quality/c28183.md)|L'argomento può essere un valore ed è una copia del valore trovato nel puntatore|
|[C28193](../code-quality/c28193.md)|La variabile contiene un valore che deve essere esaminato|
|[C28196](../code-quality/c28196.md)|Non viene soddisfatto il requisito. (L'espressione restituisce true).|
|[C28202](../code-quality/c28202.md)|Riferimento non valido a membro non statico|
|[C28203](../code-quality/c28203.md)|Riferimento ambiguo al membro di classe.|
|[C28205](../code-quality/c28205.md)|_Success\_ o _On_failure\_ usato in un contesto non valido|
|[C28206](../code-quality/c28206.md)|L'operando sinistro punta a uno struct. Utilizzare '->'|
|[C28207](../code-quality/c28207.md)|L'operando sinistro è uno struct. Utilizzare '.'|
|[C28209](../code-quality/c28209.md)|La dichiarazione del simbolo dispone di una dichiarazione in conflitto|
|[C28210](../code-quality/c28210.md)|Impossibile definire le annotazioni per il contesto __On_failure in un precontesto esplicito|
|[C28211](../code-quality/c28211.md)|Previsto nome contesto statico per SAL_context|
|[C28212](../code-quality/c28212.md)|Prevista espressione del puntatore per l'annotazione|
|[C28213](../code-quality/c28213.md)|L'annotazione _Use_decl_annotations\_ deve essere usata per fare riferimento, senza alcuna modifica, a una dichiarazione precedente.|
|[C28214](../code-quality/c28214.md)|I nomi di parametro di attributo devono essere p1...p9|
|[C28215](../code-quality/c28215.md)|Impossibile applicare typefix a un parametro che già dispone di un typefix|
|[C28216](../code-quality/c28216.md)|L'annotazione checkReturn si applica soltanto a postcondizioni per il parametro di funzione specifico.|
|[C28217](../code-quality/c28217.md)|Per la funzione, il numero di parametri per l'annotazione non corrisponde a quello trovato nel file|
|[C28218](../code-quality/c28218.md)|Per il parametro di funzione, il parametro dell'annotazione non corrisponde a quello trovato nel file|
|[C28219](../code-quality/c28219.md)|Membro di enumerazione previsto per l'annotazione del parametro nell'annotazione|
|[C28220](../code-quality/c28220.md)|Espressione integer prevista per l'annotazione del parametro nell'annotazione|
|[C28221](../code-quality/c28221.md)|Prevista espressione di tipo String per il parametro nell'annotazione|
|[C28222](../code-quality/c28222.md)|Previsto __yes, \__no o \__maybe per l'annotazione|
|[C28223](../code-quality/c28223.md)|Token o identificatore previsto mancante per l'annotazione, parametro|
|[C28224](../code-quality/c28224.md)|L'annotazione richiede parametri|
|[C28225](../code-quality/c28225.md)|Numero non corretto di parametri necessari nell'annotazione|
|[C28226](../code-quality/c28226.md)|L'annotazione non può essere anche PrimOp nella dichiarazione corrente|
|[C28227](../code-quality/c28227.md)|L'annotazione non può essere anche PrimOp nella dichiarazione precedente|
|[C28228](../code-quality/c28228.md)|Parametro di annotazione: Impossibile utilizzare il tipo nelle annotazioni|
|[C28229](../code-quality/c28229.md)|L'annotazione non supporta parametri|
|[C28230](../code-quality/c28230.md)|Il tipo di parametro non ha membro.|
|[C28231](../code-quality/c28231.md)|L'annotazione è valida solo in una matrice|
|[C28232](../code-quality/c28232.md)|Pre, post o deref non applicato ad alcuna annotazione|
|[C28233](../code-quality/c28233.md)|Pre, post o deref applicato a un blocco|
|[C28234](../code-quality/c28234.md)|L'espressione __At non si applica alla funzione corrente|
|[C28235](../code-quality/c28235.md)|La funzione non può fungere autonomamente da annotazione|
|[C28236](../code-quality/c28236.md)|Impossibile utilizzare l'annotazione in un'espressione|
|[C28237](../code-quality/c28237.md)|L'annotazione nel parametro non è più supportata|
|[C28238](../code-quality/c28238.md)|L'annotazione nel parametro presenta più di un valore, stringValue e longValue. Utilizzare paramn=xxx|
|[C28239](../code-quality/c28239.md)|L'annotazione nel parametro presenta sia stringValue, o longValue, che paramn=xxx. Utilizzare solo paramn=xxx|
|[C28240](../code-quality/c28240.md)|L'annotazione nel parametro presenta param2 ma nessun param1|
|[C28241](../code-quality/c28241.md)|Annotazione per la funzione nel parametro non riconosciuta|
|[C28243](../code-quality/c28243.md)|L'annotazione per la funzione nel parametro richiede più dereferenziazioni di quante ne siano consentite dal tipo annotato effettivo|
|[C28244](../code-quality/c28244.md)|L'annotazione per la funzione dispone di un'annotazione esterna/parametro non analizzabile|
|[C28245](../code-quality/c28245.md)|L'annotazione per la funzione annota 'this' in una funzione non membro|
|[C28246](../code-quality/c28246.md)|Nell'annotazione per la funzione, il parametro non corrisponde al tipo del parametro|
|[C28250](../code-quality/c28250.md)|Annotazione incoerente per la funzione: errore dell'istanza precedente.|
|[C28251](../code-quality/c28251.md)|Annotazione incoerente per la funzione: errore dell'istanza.|
|[C28252](../code-quality/c28252.md)|Annotazione incoerente per la funzione: il parametro presenta altre annotazioni su questa istanza.|
|[C28253](../code-quality/c28253.md)|Annotazione incoerente per la funzione: il parametro presenta altre annotazioni su questa istanza.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>() non è supportato nelle annotazioni|
|[C28262](../code-quality/c28262.md)|Errore di sintassi dell'annotazione rilevato nella funzione per l'annotazione|
|[C28263](../code-quality/c28263.md)|Errore di sintassi nell'annotazione condizionale rilevato nell'oggetto annotazione intrinseco|
|[C28267](../code-quality/c28267.md)|Errore di sintassi dell'annotazione rilevato nella funzione per l'annotazione.|
|[C28272](../code-quality/c28272.md)|L'annotazione per la funzione, parametro, durante l'analisi non è coerente con la dichiarazione della funzione|
|[C28273](../code-quality/c28273.md)|Per la funzione, le informazioni non sono coerenti con la dichiarazione della funzione|
|[C28275](../code-quality/c28275.md)|Il parametro to _Macro_value\_ è null|
|[C28279](../code-quality/c28279.md)|Per il simbolo è stato trovato un 'begin' senza il corrispondente 'end'|
|[C28280](../code-quality/c28280.md)|Per il simbolo, è stato trovato un 'end' senza un 'begin' corrispondente|
|[C28282](../code-quality/c28282.md)|Le stringhe di formato devono essere nelle precondizioni|
|[C28285](../code-quality/c28285.md)|Per la funzione, errore di sintassi nel parametro|
|[C28286](../code-quality/c28286.md)|Per la funzione, errore di sintassi vicino alla fine|
|[C28287](../code-quality/c28287.md)|Per la funzione, errore di sintassi nell'annotazione _At\_() (nome parametro non riconosciuto)|
|[C28288](../code-quality/c28288.md)|Per la funzione, errore di sintassi nell'annotazione _At\_() (nome parametro non valido)|
|[C28289](../code-quality/c28289.md)|Per la funzione: ReadableTo o WritableTo non disponeva di limit-spec come parametro|
|[C28290](../code-quality/c28290.md)|L'annotazione per la funzione contiene un numero di riferimenti esterni maggiore del numero di parametri effettivi|
|[C28291](../code-quality/c28291.md)|Il post null/notnull al livello deref 0 è privo di significato per la funzione.|
|[C28300](../code-quality/c28300.md)|Operandi dell'espressione di tipi incompatibili per l'operatore|
|[C28301](../code-quality/c28301.md)|Nessuna annotazione per la prima dichiarazione di funzione.|
|[C28302](../code-quality/c28302.md)|Operatore _Deref\_ aggiuntivo rilevato nell'annotazione.|
|[C28303](../code-quality/c28303.md)|Operatore _Deref\_ ambiguo trovato nell'annotazione.|
|[C28304](../code-quality/c28304.md)|Operatore _Notref\_ non correttamente posizionato applicato al token.|
|[C28305](../code-quality/c28305.md)|È stato individuato un errore durante l'analisi di un token.|
|[C28306](../code-quality/c28306.md)|L'annotazione nel parametro è obsoleta|
|[C28307](../code-quality/c28307.md)|L'annotazione nel parametro è obsoleta|
|[C28350](../code-quality/c28350.md)|L'annotazione descrive una situazione non applicabile in modo condizionale.|
|[C28351](../code-quality/c28351.md)|L'annotazione descrive la posizione nella condizione in cui non è possibile utilizzare un valore dinamico (variabile).|