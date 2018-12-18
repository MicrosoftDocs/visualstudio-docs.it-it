---
title: Avvisi di analisi per codice gestito ordinati per CheckId codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1806
- CA1809
- CA1810
- CA1811
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA5122
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 4f08a53f5af8342387ce5b523e29e007de3a0524
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Avvisi di analisi del codice per il codice gestito ordinati per CheckId
Nella tabella seguente sono elencati gli avvisi di analisi del codice per il codice gestito ordinati per identificatore CheckId.  
  
## <a name="warnings"></a>Avvisi  
  
|CheckId|Avviso|Descrizione|  
|-------------|-------------|-----------------|  
|CA1000|[CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Quando viene chiamato un membro statico di un tipo generico, è necessario specificare l'argomento tipo. Quando viene chiamato un membro di istanza generica che non supporta l'inferenza, è necessario specificare l'argomento tipo relativo al membro. In questi due casi, la sintassi necessaria per specificare l'argomento tipo è diversa e può generare confusione.|  
|CA1001|[CA1001: I tipi proprietari di campi Disposable devono essere Disposable](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Una classe dichiara e implementa un campo di istanza di tipo System.IDisposable e la classe non implementa IDisposable. Una classe che dichiara un campo IDisposable è indirettamente proprietaria di una risorsa non gestita e deve implementare l'interfaccia IDisposable.|  
|CA1002|[CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)|Collections < (di \<(T >) >) è una raccolta generica progettata per prestazioni ottimali, non per l'ereditarietà. List, pertanto, non contiene membri virtuali. Devono invece essere esposte le raccolte generiche che sono state progettate per l'ereditarietà.|  
|CA1003|[CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)|Un tipo contiene un delegato che restituisce void, la cui firma contiene due parametri (il primo è un oggetto e il secondo è un tipo assegnabile a EventArgs) e l'assembly che contiene è destinato a Microsoft .NET Framework 2.0.|  
|CA1004|[CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Per inferenza si intende la procedura con cui viene determinato l'argomento tipo di un metodo generico in base al tipo di argomento passato al metodo, piuttosto che in base alla specifica esplicita dell'argomento tipo. Per consentire l'inferenza, la firma di parametro di un metodo generico deve includere un parametro dello stesso tipo del parametro di tipo relativo al metodo. In tal caso non è necessario specificare l'argomento tipo. Quando si utilizza l'inferenza per tutti i parametri di tipo, la sintassi necessaria per chiamare metodi di istanza generici e non generici è identica. In questo modo si semplifica l'usabilità dei metodi generici.|  
|CA1005|[CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Quanto più è alto il numero di parametri di tipo contenuti, maggiore è la difficoltà di sapere e ricordare cosa rappresenta ciascun parametro. È in genere ovvio con un parametro di tipo, come in List\<T > e in alcuni casi che presentano due parametri di tipo, come in Dictionary\<TKey, TValue >. Tuttavia, se il numero dei parametri di tipo è superiore a due, il livello di difficoltà sarà troppo elevato per la maggior parte degli utenti.|  
|CA1006|[CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Un argomento tipo annidato è un argomento tipo che è anche un tipo generico. Per chiamare un membro la cui firma contiene un argomento tipo annidato, l'utente deve creare un'istanza su un tipo generico e passare il tipo al costruttore di un secondo tipo generico. La sintassi e la procedura necessarie sono complesse ed è opportuno evitarle.|  
|CA1007|[CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)|Un metodo visibile esternamente contiene un parametro per riferimento di tipo System.Object. L'utilizzo di un metodo generico consente di passare al metodo tutti i tipi, soggetti a vincoli, senza prima eseguire il cast del tipo al tipo di parametro per riferimento.|  
|CA1008|[CA1008: Gli enum devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)|Il valore predefinito di un'enumerazione non inizializzata, come altri tipi di valore, è zero. Un'enumerazione senza attributi flag definisce un membro utilizzando il valore zero in modo che il valore predefinito sia un valore valido dell'enumerazione. Se un'enumerazione a cui è applicato l'attributo FlagsAttribute definisce un membro con valore zero, il relativo nome deve essere "None" per indicare che nell'enumerazione non è stato impostato alcun valore.|  
|CA1009|[CA1009: Dichiarare correttamente i gestori eventi](../code-quality/ca1009-declare-event-handlers-correctly.md)|I metodi di gestione eventi accettano due parametri. Il primo è di tipo System.Object ed è denominato "sender". Corrisponde all'oggetto che ha generato l'evento. Il secondo parametro è di tipo System.EventArgs ed è denominato "e". Questi sono i dati associati all'evento. I metodi del gestore eventi non restituiscono un valore. Nel linguaggio di programmazione C# il tipo restituito è void.|  
|CA1010|[CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Per ampliare la possibilità di utilizzo di una raccolta, implementare una delle interfacce di raccolta generiche. La raccolta può quindi essere utilizzata per popolare tipi di raccolte generiche.|  
|CA1011|[CA1011: Considerare il passaggio di tipi di base come parametri](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Quando un tipo di base viene specificato come parametro in una dichiarazione di metodo, qualsiasi tipo derivato dal tipo di base può essere passato al metodo come argomento corrispondente. Se la funzionalità aggiuntiva fornita dal tipo di parametro derivato non è necessaria, l'utilizzo del tipo di base consente un utilizzo più ampio del metodo.|  
|CA1012|[CA1012: I tipi astratti non devono avere costruttori](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|I costruttori sui tipi astratti possono essere chiamati solo da tipi derivati. Poiché i costruttori pubblici creano istanze di un tipo e non è possibile creare istanze di un tipo astratto, per una buona progettazione non bisognerebbe creare un tipo astratto con costruttore pubblico.|  
|CA1013|[CA1013: Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Un membro pubblico o protetto implementa gli operatori di addizione o sottrazione senza implementare l'operatore di uguaglianza.|  
|CA1014|[CA1014: Contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|In Common Language Specification (CLS) vengono definite limitazioni di denominazione, tipi di dati e regole che gli assembly devono rispettare per poter essere utilizzati tra diversi linguaggi di programmazione. In una progettazione corretta tutti gli assembly devono indicare in modo esplicito la conformità CLS utilizzando <xref:System.CLSCompliantAttribute>. Se questo attributo non è presente in un assembly, tale assembly non è conforme.|  
|CA1016|[CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|In [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] viene utilizzato il numero di versione per identificare in modo univoco un assembly e per stabilire associazioni a tipi in assembly con nome sicuro. Il numero di versione viene utilizzato insieme ai criteri di versione ed editore. Per impostazione predefinita, le applicazioni vengono eseguite solo con la versione di assembly con cui sono state compilate.|  
|CA1017|[CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|ComVisibleAttribute determina il modo in cui i client COM accedono al codice gestito. In una buona progettazione gli assembly devono indicare in modo esplicito la visibilità COM. È possibile impostare la visibilità COM per l'intero assembly e quindi eseguirne l'override per singoli tipi e membri dei tipi. Se questo attributo non è presente, il contenuto dell'assembly è visibile ai client COM.|  
|CA1018|[CA1018: Contrassegnare gli attributi con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Quando si definisce un attributo personalizzato, contrassegnarlo tramite AttributeUsageAttribute per indicare la posizione nel codice sorgente in cui applicare l'attributo personalizzato. Il significato e l'utilizzo previsto di un attributo ne determinano le posizioni valide nel codice.|  
|CA1019|[CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Gli attributi possono definire argomenti obbligatori che devono essere specificati quando si applica l'attributo a una destinazione. Sono inoltre noti come argomenti posizionali poiché vengono forniti ai costruttori di attributo come parametri posizionali. Per ogni argomento obbligatorio, l'attributo deve fornire anche una proprietà in sola lettura corrispondente in modo che il valore dell'argomento possa essere recuperato in fase di esecuzione. Gli attributi possono inoltre definire argomenti facoltativi, noti anche come argomenti denominati. Questi argomenti sono forniti ai costruttori degli attributi in base al nome e devono disporre di una proprietà in lettura e scrittura corrispondente.|  
|CA1020|[CA1020: Evitare l'uso di spazi dei nomi con un numero ridotto di tipi](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Accertarsi che ognuno degli spazi dei nomi disponga di un'organizzazione logica e che sia presente un motivo valido per inserire tipi in uno spazio dei nomi scarsamente popolato.|  
|CA1021|[CA1021: Evitare parametri out](../code-quality/ca1021-avoid-out-parameters.md)|Il passaggio di tipi per riferimento (mediante out o ref) richiede esperienza nell'utilizzo dei puntatori, nonché la conoscenza delle differenze tra tipi di valore e tipi di riferimento e dei metodi di gestione con più valori restituiti. Inoltre, la differenza tra parametri out e ref non è sempre nota.|  
|CA1023|[CA1023: Gli indicizzatori non devono essere multidimensionali](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Gli indicizzatori, ovvero le proprietà indicizzate, devono utilizzare un indice singolo. Gli indicizzatori multidimensionali possono ridurre sensibilmente l'usabilità della libreria.|  
|CA1024|[CA1024: Usare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)|Un metodo pubblico o protetto presenta un nome che inizia con "Get", non accetta parametri e restituisce un valore diverso da una matrice. Il metodo presenta tutte le caratteristiche per diventare una proprietà.|  
|CA1025|[CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Utilizzare una matrice di parametri anziché argomenti ripetuti quando non si conosce il numero esatto di argomenti e quando gli argomenti variabili sono dello stesso tipo oppure possono essere passati come lo stesso tipo.|  
|CA1026|[CA1026: Evitare l'uso di parametri predefiniti](../code-quality/ca1026-default-parameters-should-not-be-used.md)|I metodi che utilizzano parametri predefiniti sono consentiti dalla specifica CLS; questa specifica, tuttavia, consente ai compilatori di ignorare i valori assegnati a questi parametri. Per mantenere il comportamento desiderato tra diversi linguaggi di programmazione, è necessario sostituire i metodi che utilizzano parametri predefiniti con overload di metodi che forniscono i parametri predefiniti.|  
|CA1027|[CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Applicare FlagsAttribute a un'enumerazione quando le relative costanti denominate possono essere combinate in modo significativo.|  
|CA1028|[CA1028: L'archivio di enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)|Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Per impostazione predefinita, il tipo di dati System.Int32 viene utilizzato per archiviare il valore costante. Benché sia possibile modificare il tipo sottostante, questa operazione non è necessaria né consigliata nella maggior parte degli scenari.|  
|CA1030|[CA1030: Usare eventi dove appropriato](../code-quality/ca1030-use-events-where-appropriate.md)|Questa regola rileva i metodi che presentano nomi comunemente utilizzati per gli eventi. Se un metodo viene chiamato in risposta a una modifica dello stato chiaramente definita, il metodo deve essere richiamato da un gestore eventi. Gli oggetti che chiamano il metodo devono generare eventi anziché chiamare direttamente il metodo.|  
|CA1031|[CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Le eccezioni generali non devono essere rilevate. Rilevare un'eccezione più specifica oppure generare nuovamente l'eccezione generale come ultima istruzione nel blocco catch.|  
|CA1032|[CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md)|Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni.|  
|CA1033|[CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Un tipo visibile esternamente non sealed fornisce un'implementazione di metodo esplicita di un'interfaccia pubblica e non fornisce un metodo visibile esternamente alternativo con lo stesso nome.|  
|CA1034|[CA1034: I tipi annidati non devono essere visibili](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Un tipo annidato è un tipo dichiarato nell'ambito di un altro tipo. I tipi annidati sono utili per incapsulare dettagli di implementazione privati del tipo contenitore. I tipi annidati utilizzati per questo scopo non devono essere visibili esternamente.|  
|CA1035|[CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|La regola richiede che le implementazioni di ICollection forniscano membri fortemente tipizzati in modo che agli utenti non venga richiesto di eseguire il cast di argomenti al tipo Object quando utilizzano la funzionalità fornita dall'interfaccia. La regola presuppone che il tipo che implementa ICollection esegua questa operazione per gestire una raccolta di istanze di un tipo più sicuro di Object.|  
|CA1036|[CA1036: Eseguire l'override di metodi su tipi confrontabili](../code-quality/ca1036-override-methods-on-comparable-types.md)|Un tipo pubblico o protetto implementa l'interfaccia System.IComparable. Non esegue l'override di Object.Equals né l'overload dell'operatore specifico del linguaggio per uguaglianza, ineguaglianza, minore di o maggiore di.|  
|CA1038|[CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Questa regola richiede che le implementazioni di IEnumerator forniscano anche una versione fortemente tipizzata della proprietà Current in modo che agli utenti non venga richiesto di eseguire il cast del valore restituito al tipo sicuro quando utilizzano la funzionalità fornita dall'interfaccia.|  
|CA1039|[CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)|La regola richiede che le implementazioni di IList forniscano membri fortemente tipizzati in modo che agli utenti non venga richiesto di eseguire il cast di argomenti al tipo System.Object quando utilizzano la funzionalità fornita dall'interfaccia.|  
|CA1040|[CA1040: Evitare l'uso di interfacce vuote](../code-quality/ca1040-avoid-empty-interfaces.md)|Le interfacce definiscono membri che forniscono un comportamento o un contratto di utilizzo. La funzionalità descritta dall'interfaccia può essere adottata da qualsiasi tipo, indipendentemente dal punto in cui il tipo è visualizzato nella gerarchia di ereditarietà. Un tipo implementa un'interfaccia fornendo implementazioni per i membri dell'interfaccia. Un'interfaccia vuota non definisce alcun membro. Di conseguenza, non definisce un contratto implementabile.|  
|CA1041|[CA1041: Specificare una proprietà ObsoleteAttribute.Message](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Un tipo o un membro viene contrassegnato utilizzando un attributo System.ObsoleteAttribute per cui non è stata specificata la proprietà ObsoleteAttribute.Message. Quando viene compilato un membro o un tipo contrassegnato utilizzando ObsoleteAttribute, viene visualizzata la proprietà Message dell'attributo. In questo modo vengono fornite le informazioni utente sul tipo o sul membro obsoleto.|  
|CA1043|[CA1043: Usare argomento di tipo stringa o integrale per gli indicizzatori](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Gli indicizzatori, ovvero le proprietà indicizzate, devono utilizzare tipi integrali o stringa per l'indice. Questi tipi vengono in genere utilizzati per l'indicizzazione di strutture di dati e aumentano l'utilizzabilità della libreria. L'utilizzo del tipo Object deve essere limitato ai casi in cui non sia possibile specificare in fase di progettazione il tipo integrale o stringa.|  
|CA1044|[CA1044: Le proprietà non devono essere in sola scrittura](../code-quality/ca1044-properties-should-not-be-write-only.md)|Sebbene la presenza di proprietà di sola lettura sia accettabile e spesso necessaria, le linee guida di progettazione proibiscono l'utilizzo di proprietà di sola scrittura. Ciò è dovuto al fatto che consentire a un utente di impostare un valore e quindi impedirgli di visualizzarlo, non offre alcuna sicurezza. Inoltre, senza accesso in lettura, lo stato degli oggetti condivisi non può essere visualizzato, il che ne limita l'utilità.|  
|CA1045|[CA1045: Non passare i tipi per riferimento](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Il passaggio di tipi per riferimento (mediante out o ref) richiede esperienza nell'utilizzo dei puntatori, nonché la conoscenza delle differenze tra tipi di valore e tipi di riferimento e dei metodi di gestione con più valori restituiti. Gli architetti di librerie destinate a un pubblico generico non devono aspettarsi che gli utenti siano in grado di utilizzare i parametri out o ref.|  
|CA1046|[CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Per i tipi di riferimento, l'implementazione predefinita dell'operatore di uguaglianza è quasi sempre corretta. Per impostazione predefinita, i due riferimenti sono uguali solo se puntano allo stesso oggetto.|  
|CA1047|[CA1047: Non dichiarare membri protetti nei tipi sealed](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|I tipi dichiarano membri protetti in modo che i tipi che ereditano possano accedere al membro o eseguirne l'override. Per definizione, non è possibile ereditare tipi sealed, pertanto non è possibile chiamare metodi protetti su tipi sealed.|  
|CA1048|[CA1048: Non dichiarare membri virtuali nei tipi sealed](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|I tipi dichiarano metodi come virtuali in modo che l'ereditarietà di tipi possa eseguire l'override dell'implementazione del metodo virtuale. Per definizione, non è possibile ereditare un tipo sealed. Di conseguenza, un metodo virtuale su un tipo sealed risulterà non significativo.|  
|CA1049|[CA1049: I tipi delle risorse native devono essere Disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|I tipi che allocano risorse non gestite devono implementare IDisposable per consentire ai chiamanti di rilasciare quelle risorse su richiesta e ridurre la durata degli oggetti che le contengono.|  
|CA1050|[CA1050: Dichiarare i tipi negli spazi dei nomi](../code-quality/ca1050-declare-types-in-namespaces.md)|I tipi vengono dichiarati in spazi dei nomi per impedire conflitti di denominazione e per organizzare i tipi correlati in una gerarchia di oggetti.|  
|CA1051|[CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|L'utilizzo principale di un campo deve essere come dettaglio di implementazione. I campi devono essere privati o interni e devono essere esposti tramite proprietà.|  
|CA1052|[CA1052: I tipi che contengono membri statici devono essere sealed](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Un tipo pubblico o protetto contiene solo membri statici e non è dichiarato utilizzando il modificatore (NotInheritable) (Riferimenti per C#) sealed. Un tipo non adatto a essere ereditato deve essere contrassegnato utilizzando il modificatore sealed per impedire che venga utilizzato come tipo di base.|  
|CA1053|[CA1053: I tipi che contengono membri statici non devono avere costruttori](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Un tipo pubblico o annidato dichiara solo membri statici e presenta un costruttore predefinito pubblico o protetto. Il costruttore non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo. A scopo di sicurezza e protezione, l'overload dei valori di stringa deve chiamare l'overload URI tramite l'argomento stringa.|  
|CA1054|[CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Se un metodo accetta una rappresentazione in forma di stringa di un URI, è necessario fornire un overload corrispondente che accetti un'istanza della classe URI che fornisce questi servizi in modo sicuro e protetto.|  
|CA1055|[CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Questa regola presuppone che il metodo restituisca un URI. Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La classe System.Uri fornisce questi servizi in modo sicuro e protetto.|  
|CA1056|[CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Questa regola presuppone che la proprietà rappresenti un URI (Uniform Resource Identifier). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La classe System.Uri fornisce questi servizi in modo sicuro e protetto.|  
|CA1057|[CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Un tipo dichiara overload del metodo che risultano diversi solo per la sostituzione di un parametro di stringa con un parametro System.Uri. L'overload che accetta il parametro di stringa non chiama l'overload che accetta il parametro URI.|  
|CA1058|[CA1058: I tipi non devono estendere tipi di base specifici](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Un tipo visibile esternamente estende tipi di base specifici. Utilizzare una delle alternative seguenti:|  
|CA1059|[CA1059: I membri non devono esporre tipi concreti specifici](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Un tipo concreto è un tipo con implementazione completa, pertanto è possibile crearne un'istanza. Per consentire un utilizzo esteso del membro, sostituire il tipo concreto utilizzando l'interfaccia suggerita.|  
|CA1060|[CA1060: Spostare P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|I metodi di chiamata al sistema operativo, ad esempio quelli contrassegnati utilizzando l'attributo System.Runtime.InteropServices.DllImportAttribute, o i metodi definiti mediante la parola chiave Declare in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] accedono a codice non gestito. Questi metodi devono appartenere alla classe NativeMethods, SafeNativeMethods o UnsafeNativeMethods.|  
|CA1061|[CA1061: Non nascondere i metodi di una classe base](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Un metodo di un tipo di base è nascosto da un metodo denominato in modo identico in un tipo derivato, quando la firma del parametro del metodo derivato differisce solo per i tipi che presentano una derivazione più debole rispetto ai tipi corrispondenti nella firma del parametro del metodo di base.|  
|CA1062|[CA1062: Convalidare gli argomenti di metodi pubblici](../code-quality/ca1062-validate-arguments-of-public-methods.md)|È necessario che tutti gli argomenti di riferimento passati a metodi visibili esternamente vengano sottoposti a verifica per accertarsi che non corrispondano a valori Null.|  
|CA1063|[CA1063: Implementare IDisposable correttamente](../code-quality/ca1063-implement-idisposable-correctly.md)|È necessario che tutti i tipi IDisposable implementino correttamente il modello Dispose.|  
|CA1064|[CA1064: Le eccezioni devono essere pubbliche](../code-quality/ca1064-exceptions-should-be-public.md)|Un'eccezione interna è visibile solo nel relativo ambito interno. Se l'eccezione si verifica al di fuori dell'ambito interno, può essere rilevata solo tramite l'eccezione di base. Se l'eccezione interna è ereditata da T:System.Exception, T:System.SystemException o T:System.ApplicationException, il codice esterno non disporrà di informazioni sufficienti per la corretta gestione dell'eccezione.|  
|CA1065|[CA1065: Non generare eccezioni in posizioni impreviste](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Un metodo che normalmente non genera eccezioni genera un'eccezione.|  
|CA1300|[CA1300: Specificare MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Per visualizzare correttamente una finestra di messaggio per le impostazioni cultura che utilizzano un ordine di lettura da destra a sinistra, è necessario passare i membri RightAlign e RtlReading dell'enumerazione MessageBoxOptions al metodo Show.|  
|CA1301|[CA1301: Evitare tasti di scelta rapida duplicati](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Un tasto di scelta o tasto di scelta rapida consente l'accesso da tastiera a un controllo mediante ALT. Quando più controlli presentano tasti di scelta duplicati, il comportamento del tasto di scelta non è ben definito.|  
|CA1302|[CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|L'enumerazione System.Environment.SpecialFolder contiene membri che fanno riferimento a cartelle di sistema speciali. I percorsi di queste cartelle possono presentare valori diversi in sistemi operativi diversi. I percorso possono essere modificati e sono localizzati. Il metodo Environment.GetFolderPath restituisce i percorsi associati all'enumerazione Environment.SpecialFolder, localizzati e appropriati per il computer attualmente in esecuzione.|  
|CA1303|[CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Un metodo visibile esternamente passa una stringa letterale come parametro a un costruttore o a un metodo nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e questa stringa deve essere localizzabile.|  
|CA1304|[CA1304: Specificare CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|Un metodo o un costruttore chiama un membro che presenta un overload che accetta un parametro System.Globalization.CultureInfo e tale metodo o costruttore non chiama l'overload che accetta il parametro CultureInfo. Quando non viene fornito un oggetto CultureInfo o System.IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali.|  
|CA1305|[CA1305: Specificare IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Un metodo o un costruttore chiama uno o più membri con overload che accettano un parametro System.IFormatProvider e tale metodo o costruttore non chiama l'overload che accetta il parametro IFormatProvider. Quando non viene fornito un oggetto System.Globalization.CultureInfo o IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali.|  
|CA1306|[CA1306: Specificare le impostazioni locali per i tipi di dati](../code-quality/ca1306-set-locale-for-data-types.md)|Le impostazioni locali determinano elementi di presentazione specifici delle impostazioni cultura per i dati, ad esempio la formattazione utilizzata per valori numerici, simboli di valuta e criterio di ordinamento. Quando si crea un oggetto DataTable o DataSet, è opportuno definire in modo esplicito le impostazioni locali.|  
|CA1307|[CA1307: Specificare StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Un'operazione di confronto tra stringhe utilizza un overload del metodo che non imposta un parametro StringComparison.|  
|CA1308|[CA1308: Normalizzare le stringhe in lettere maiuscole](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri non è in grado di completare un round trip in caso di conversione in lettere minuscole.|  
|CA1309|[CA1309: Usare StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)|In un'operazione di confronto tra stringhe di tipo non linguistico il parametro StringComparison non viene impostato su Ordinal o OrdinalIgnoreCase. L'impostazione esplicita del parametro su StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase consente spesso di rendere il codice più veloce, corretto e affidabile.|  
|CA1400|[CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Un metodo pubblico o protetto è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.DllImportAttribute. Non è possibile individuare la libreria non gestita né associare il metodo a una funzione nella libreria.|  
|CA1401|[CA1401: I P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Un metodo pubblico o protetto in un tipo pubblico presenta l'attributo System.Runtime.InteropServices.DllImportAttribute (implementato anche dalla parola chiave Declare in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Questi metodi non devono essere esposti.|  
|CA1402|[CA1402: Evitare gli overload nelle interfacce visibili a COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Quando i metodi sottoposti a overload vengono esposti ai client COM, solo il primo overload di metodo conserva il proprio nome. Gli overload successivi vengono rinominati in modo univoco aggiungendo al nome un carattere di sottolineatura (_) e un numero intero che corrisponde all'ordine di dichiarazione dell'overload.|  
|CA1403|[CA1403: I tipi layout automatici non devono essere visibili a COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Un tipo di valore visibile a COM è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.StructLayoutAttribute impostato su LayoutKind.Auto. Il layout di tali tipi può variare a seconda delle versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], con conseguente compromissione delle funzionalità dei client COM che prevedono un layout specifico.|  
|CA1404|[CA1404: Chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Viene eseguita una chiamata al metodo Marshal. GetLastWin32Error o l'equivalente [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funzione GetLastError e la chiamata immediatamente precedente non è un sistema operativo invoke (metodo).|  
|CA1405|[CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Un tipo visibile a COM deriva da un tipo non visibile a COM.|  
|CA1406|[CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|I client COM Visual Basic 6 non è possibile accedere interi a 64 bit.|  
|CA1407|[CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM non supporta i metodi statici.|  
|CA1408|[CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|I tipi che utilizzano un'interfaccia duale consentono l'associazione dei client a uno specifico layout di interfaccia. Eventuali modifiche apportate in una versione futura al layout del tipo o ai tipi base interromperanno l'associazione dei client COM all'interfaccia. Per impostazione predefinita, se l'attributo ClassInterfaceAttribute non è specificato, viene utilizzata un'interfaccia di solo invio.|  
|CA1409|[CA1409: I tipi visibili a COM devono essere creabili](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Un tipo di riferimento contrassegnato specificatamente come visibile a COM contiene un costruttore con parametri pubblico, ma non contiene un costruttore predefinito pubblico senza parametri. Un tipo senza un costruttore predefinito pubblico non può essere creato da client COM.|  
|CA1410|[CA1410: I metodi di registrazione COM devono corrispondere](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|In un tipo viene dichiarato un metodo contrassegnato utilizzando l'attributo System.Runtime.InteropServices.ComRegisterFunctionAttribute, ma non un metodo contrassegnato utilizzando l'attributo System.Runtime.InteropServices.ComUnregisterFunctionAttribute o viceversa.|  
|CA1411|[CA1411: I metodi di registrazione COM non devono essere visibili](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Un metodo contrassegnato utilizzando l'attributo System.Runtime.InteropServices.ComRegisterFunctionAttribute o System.Runtime.InteropServices.ComUnregisterFunctionAttribute è visibile esternamente.|  
|CA1412|[CA1412: Contrassegnare le interfacce ComSource come IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Un tipo è contrassegnato utilizzando l'attributo System.Runtime.InteropServices.ComSourceInterfacesAttribute e almeno una delle interfacce specificate non è contrassegnata utilizzando l'attributo System.Runtime.InteropServices.InterfaceTypeAttribute impostato su ComInterfaceType.InterfaceIsIDispatch.|  
|CA1413|[CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|I campi di istanza non pubblici di tipi di valori visibili a COM sono visibili ai client COM. Esaminare il contenuto dei campi alla ricerca di informazioni che non devono essere esposte o che avranno un impatto non previsto sulla progettazione o la sicurezza.|  
|CA1414|[CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Per il tipo di dati booleano sono disponibili più rappresentazioni nel codice non gestito.|  
|CA1415|[CA1415: Dichiarare correttamente i P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md)|Tramite questa regola vengono cercate le dichiarazioni di metodo di chiamata al sistema operativo per le funzioni [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] con un puntatore a un parametro di struttura OVERLAPPED e il cui parametro gestito corrispondente non è un puntatore a una struttura System.Threading.NativeOverlapped.|  
|CA1500|[CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante, pertanto vengono generati errori.|  
|CA1501|[CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà. Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione.|  
|CA1502|[CA1502: Evitare complessità eccessiva](../code-quality/ca1502-avoid-excessive-complexity.md)|Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali.|  
|CA1504|[CA1504: Controllare i nomi dei campi fuorvianti](../code-quality/ca1504-review-misleading-field-names.md)|Il nome di un campo di istanza inizia con "s _", o il nome del campo statico (Shared in Visual Basic) inizia con "m _".|  
|CA1505|[CA1505: evitare codice non gestibile](../code-quality/ca1505-avoid-unmaintainable-code.md)|Un tipo o metodo presenta un valore di indice di gestibilità basso. Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione.|  
|CA1506|[CA1506: Evitare un numero eccessivo di accoppiamenti di classi](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.|  
|CA1600|[CA1600: Non impostare la priorità del processo su Inattivo](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Non impostare la priorità del processo su Inattivo. I processi con System.Diagnostics.ProcessPriorityClass.Idle occupano la CPU, che diversamente sarebbe inattiva, e bloccano quindi la modalità standby.|  
|CA1601|[CA1601: Non usare i timer che impediscono le modifiche allo stato di potenza](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.|  
|CA1700|[CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Questa regola presuppone che un membro di enumerazione con un nome che contiene la parola "reserved" non sia attualmente utilizzato, ma sia un segnaposto che dovrà essere rinominato o rimosso in una versione futura. La ridenominazione o rimozione di un membro è ritenuta una modifica sostanziale.|  
|CA1701|[CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Ogni parola nella stringa di risorsa è suddivisa in token basati sulla distinzione tra maiuscole e minuscole. Ogni combinazione di due token contigui viene controllata in base alla libreria del correttore ortografico Microsoft. Se riconosciuta, la parola produce una violazione della regola.|  
|CA1702|[CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Il nome di un identificatore contiene più parole, fra cui almeno una che sembra essere composta e digitata in modo non corretto con distinzione tra maiuscole e minuscole.|  
|CA1703|[CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Una stringa di risorsa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.|  
|CA1704|[CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Il nome di un identificatore visibile esternamente contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.|  
|CA1707|[CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Per convenzione i nomi degli identificatori non contengono il carattere di sottolineatura (_). In base a questa regola vengono controllati spazi dei nomi, tipi, membri e parametri.|  
|CA1708|[CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Gli identificatori per spazi dei nomi, tipi, membri e parametri non possono differire solo in base a maiuscole e minuscole poiché ai linguaggi destinati a Common Language Runtime non è richiesta la distinzione tra maiuscole e minuscole.|  
|CA1709|[CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Per convenzione i nomi di parametro sono basati sulla convenzione Camel, mentre i nomi di spazio dei nomi, tipo e membro utilizzano la convenzione Pascal.|  
|CA1710|[CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Per convenzione, i nomi dei tipi che estendono determinati tipi di base o implementano determinate interfacce o dei tipi derivati da questi tipi contengono un suffisso associato al tipo di base o all'interfaccia.|  
|CA1711|[CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Per convenzione, solo i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce o dei tipi derivati da questi tipi devono terminare con suffissi specifici riservati. Gli altri nomi di tipi non devono utilizzare questi suffissi riservati.|  
|CA1712|[CA1712: Non usare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|I nomi dei membri di enumerazione non hanno come prefisso il nome del tipo poiché si prevede che le informazioni sul tipo vengano fornite dagli strumenti di sviluppo.|  
|CA1713|[CA1713: Non usare il prefisso Before o After negli eventi](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Il nome di un evento inizia con "Before" o "After". Per denominare eventi correlati generati in una sequenza specifica, utilizzare i tempi verbali presente o passato per indicare la posizione relativa nella sequenza di azioni.|  
|CA1714|[CA1714: Le enumerazioni con Flags devono avere nomi plurali](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Un'enumerazione pubblica dispone dell'attributo System.FlagsAttribute e il nome non termina per "s". Ai tipi contrassegnati utilizzando FlagsAttribute sono assegnati nomi plurali perché tale attributo indica che è possibile specificare più valori.|  
|CA1715|[CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Il nome di un'interfaccia visibile esternamente non inizia con una "I" maiuscola. Il nome di un parametro di tipo generico su un tipo o metodo visibile esternamente non inizia con una "T" maiuscola.|  
|CA1716|[CA1716: Gli identificatori non devono corrispondere a parole chiave](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Un nome di spazio dei nomi o di tipo corrisponde a una parola chiave riservata in un linguaggio di programmazione. Gli identificatori di spazi dei nomi e tipi non devono corrispondere a parole chiave definite dai linguaggi con destinazione Common Language Runtime.|  
|CA1717|[CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|In base alle convenzioni di denominazione, un nome plurale in un'enumerazione indica che è possibile specificare più valori di enumerazione contemporaneamente.|  
|CA1719|[CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Un nome di parametro deve comunicare il significato di un parametro e un nome di membro deve comunicare il significato di un membro. Le progettazioni in cui questi nomi coincidono sono rare. Assegnare a un parametro lo stesso nome del relativo membro non è intuitiva e rende più complesso l'utilizzo della libreria.|  
|CA1720|[CA1720: Gli identificatori non devono contenere nomi di tipo](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Il nome di un parametro in un membro visibile esternamente contiene un nome di tipo di dati oppure il nome di un membro visibile esternamente contiene un nome di tipo di dati specifico del linguaggio.|  
|CA1721|[CA1721: I nomi delle proprietà non devono corrispondere ai metodi get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Il nome di un membro pubblico o protetto inizia con "Get" e corrisponde in altro modo al nome di una proprietà pubblica o protetta. I metodi "Get" e le proprietà devono avere nomi indicano chiaramente la distinzione tra le funzioni.|  
|CA1722|[CA1722: Gli identificatori non devono contenere il prefisso non corretto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Per convenzione, solo determinati elementi di programmazione presentano nomi che iniziano con un prefisso specifico.|  
|CA1724|[CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi definiti nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. La violazione di questa regola può ridurre l'utilizzabilità della libreria.|  
|CA1725|[CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Una denominazione coerente dei parametri in una gerarchia di override aumenta la funzionalità degli override di metodo. Un nome di parametro in un metodo derivato diverso dal nome nella dichiarazione di base può provocare confusione sulla natura del metodo, ovvero se si tratta di un override del metodo di base o di un nuovo overload del metodo.|  
|CA1726|[CA1726: Usare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)|Il nome di un identificatore visibile esternamente include un termine per il quale esiste un termine alternativo preferito. In alternativa, il nome include il termine "Flag" o "Flags".|  
|CA1800|[CA1800: Non eseguire il cast inutilmente](../code-quality/ca1800-do-not-cast-unnecessarily.md)|I cast duplicati comportano una riduzione delle prestazioni, in particolare quando i cast vengono eseguiti in istruzioni di iterazione compatte.|  
|CA1801|[CA1801: Rivedere i parametri non usati](../code-quality/ca1801-review-unused-parameters.md)|Una firma di metodo include un parametro non utilizzato nel corpo del metodo.|  
|CA1802|[CA1802: Usa valori letterali dove appropriato](../code-quality/ca1802-use-literals-where-appropriate.md)|Un campo viene dichiarato static e read-only (Shared e ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e viene inizializzato utilizzando un valore calcolabile in fase di compilazione. Poiché il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione di una variabile const (Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) in modo che il valore viene calcolato in fase di compilazione anziché in fase di esecuzione.|  
|CA1804|[CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)|Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni.|  
|CA1806|[CA1806: Non ignorare i risultati del metodo](../code-quality/ca1806-do-not-ignore-method-results.md)|Un nuovo oggetto viene creato, ma non viene mai utilizzato oppure viene chiamato un metodo che crea e restituisce una nuova stringa e la nuova stringa non viene mai utilizzata oppure un metodo COM o P/Invoke restituisce un HRESULT o un codice di errore che non viene mai utilizzato.|  
|CA1809|[CA1809: Evitare un numero eccessivo di variabili locali](../code-quality/ca1809-avoid-excessive-locals.md)|Un'ottimizzazione comune delle prestazioni consiste nell'archiviare un valore in un registro del processore anziché in memoria. Tale procedura è definita "registrazione del valore". Per aumentare la probabilità che tutte le variabili locali vengono registrate, limitare il numero di variabili a 64.|  
|CA1810|[CA1810: Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Quando un tipo dichiara un costruttore statico esplicito, tramite il compilatore JIT (Just-In-Time) viene aggiunto un controllo a ogni metodo statico del tipo e a ogni costruttore di istanza del tipo per assicurare che il costruttore statico sia stato precedentemente chiamato. I controlli dei costruttori statici possono ridurre le prestazioni.|  
|CA1811|[CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)|Un membro privato o interno (a livello di assembly) non presenta chiamanti nell'assembly, non viene richiamato da Common Language Runtime né da un delegato.|  
|CA1812|[CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Un'istanza di un tipo a livello di assembly non viene creata dal codice nell'assembly.|  
|CA1813|[CA1813: Evitare attributi non sealed](../code-quality/ca1813-avoid-unsealed-attributes.md)|La libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fornisce metodi per recuperare attributi personalizzati. Per impostazione predefinita, questi metodi eseguono ricerche nella gerarchia di ereditarietà dell'attributo. L'utilizzo di attributi sealed elimina la ricerca nella gerarchia di ereditarietà e può migliorare le prestazioni.|  
|CA1814|[CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Una matrice di matrici è una matrice i cui elementi sono costituiti da matrici. Poiché le matrici che costituiscono gli elementi possono presentare dimensioni diverse, la quantità di spazio inutilizzato sarà inferiore per alcuni insiemi di dati.|  
|CA1815|[CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Per i tipi di valore, l'implementazione ereditata di Equals utilizza la libreria Reflection e confronta il contenuto di tutti i campi. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti confrontino o ordinino le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare Equals.|  
|CA1816|[CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Un metodo che è un'implementazione di Dispose non chiama GC. SuppressFinalize; o un metodo che non è un'implementazione di Dispose chiama GC. SuppressFinalize; o un metodo chiama GC. SuppressFinalize e passa un valore diverso da this (Me in Visual Basic).|  
|CA1819|[CA1819: Le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md)|Le matrici restituite dalle proprietà non sono protette in scrittura, anche se la proprietà è in sola lettura. Affinché la matrice sia protetta da eventuali alterazioni, la proprietà deve restituire una copia della matrice. In genere, gli utenti non comprendono le implicazioni negative sulle prestazioni derivanti dalla chiamata di tale proprietà.|  
|CA1820|[CA1820: Testare le stringhe vuote usando la lunghezza di stringa](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Il confronto tra stringhe mediante la proprietà String.Length o il metodo String.IsNullOrEmpty è notevolmente più veloce rispetto all'utilizzo di Equals.|  
|CA1821|[CA1821: Rimuovere i finalizzatori vuoti](../code-quality/ca1821-remove-empty-finalizers.md)|Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto. Un finalizzatore vuoto provoca un sovraccarico aggiuntivo e non fornisce alcun vantaggio.|  
|CA1822|[CA1822: Contrassegna i membri come statici](../code-quality/ca1822-mark-members-as-static.md)|I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. Si potrà così ottenere un sensibile miglioramento delle prestazioni per codici sensibili alle prestazioni.|  
|CA1823|[CA1823: Evitare campi privati non usati](../code-quality/ca1823-avoid-unused-private-fields.md)|Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly.|  
|CA1824|[CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|L'attributo NeutralResourcesLanguage indica a ResourceManager la lingua utilizzata per visualizzare le risorse delle impostazioni cultura non associate ad alcun paese per un assembly. Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set.|  
|CA1900|[CA1900: I campi dei tipi di valore devono essere portabili](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Questa regola consente di verificare che le strutture dichiarate utilizzando layout esplicito vengano allineate correttamente quando viene effettuato il marshalling a codice non gestito nei sistemi operativi a 64 bit.|  
|CA1901|[CA1901: le Dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|La regola valuta la dimensione di ciascun parametro e il valore restituito di P/Invoke e verifica che la dimensione del parametro sia corretta quando viene effettuato il marshalling a codice non gestito in sistemi operativi a 32 e a 64 bit.|  
|CA1903|[CA1903: Usare solo API della versione di .NET Framework di destinazione](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso con la versione di .NET Framework di destinazione del progetto.|  
|CA2000|[CA2000: Eliminare gli oggetti prima di perdere l'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Poiché è possibile che si verifichi un evento eccezionale che impedisca l'esecuzione del finalizzatore di un oggetto, è opportuno eliminare in modo esplicito l'oggetto prima che tutti i riferimenti a tale oggetto siano esterni all'ambito.|  
|CA2001|[CA2001: Evitare le chiamate a metodi problematici](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un membro chiama un metodo potenzialmente pericoloso o problematico.|  
|CA2002|[CA2002: Non bloccare oggetti con identità debole](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.|  
|CA2003|[CA2003: Non considerare i fiber come i thread](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un thread gestito viene considerato come thread [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)].|  
|CA2004|[CA2004: Rimuovere le chiamate a GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Se si effettua la conversione all'utilizzo di SafeHandle, rimuovere tutte le chiamate a GC.KeepAlive (oggetto). In questo caso, non è necessario che le classi chiamino GC.KeepAlive. Questo comportamento presuppone che non dispongano di un finalizzatore, ma utilizzino SafeHandle per finalizzare l'handle OS al loro posto.|  
|CA2006|[CA2006: Usare SafeHandle per incapsulare le risorse native](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|L'utilizzo di IntPtr nel codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutte le occorrenze di IntPtr devono essere esaminate per stabilire se al loro posto è necessario utilizzare SafeHandle o una tecnologia simile.|  
|CA2100|[CA2100: Controllare la vulnerabilità della sicurezza nelle query SQL](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Un metodo imposta la proprietà System.Data.IDbCommand.CommandText usando una stringa compilata da un argomento stringa nel metodo. La regola presuppone che l'argomento stringa contenga l'input dell'utente. Una stringa di comando SQL compilata da un input dell'utente è vulnerabile agli attacchi intrusivi nel codice SQL,|  
|CA2101|[CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Un membro di platform invoke consente i chiamanti parzialmente attendibili, presenta un parametro di stringa e non effettua il marshalling della stringa. Questo può comportare una potenziale vulnerabilità di sicurezza.|  
|CA2102|[CA2102: Individuare le eccezioni non conformi a CLS nei gestori generali](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|In un membro di un assembly che non è contrassegnato utilizzando l'attributo RuntimeCompatibilityAttribute o che è contrassegnato con RuntimeCompatibility(WrapNonExceptionThrows = false) è incluso un blocco catch che gestisce System.Exception e che non contiene un blocco catch generale immediatamente successivo.|  
|CA2103|[CA2103: Controllare la sicurezza imperativa](../code-quality/ca2103-review-imperative-security.md)|Un metodo utilizza la sicurezza imperativa e potrebbe costruire l'autorizzazione tramite le informazioni sullo stato o i valori restituiti che possono essere modificati mentre la richiesta è attiva. Usare la sicurezza dichiarativa quando possibile.|  
|CA2104|[CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Un tipo visibile esternamente contiene un campo in sola lettura visibile esternamente che costituisce un tipo di riferimento modificabile. Un tipo modificabile è un tipo i cui dati di istanza possono essere modificati.|  
|CA2105|[CA2105: I campi di matrici non devono essere di sola lettura](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Quando si applica il modificatore (ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) in sola lettura a un campo contenente una matrice, il campo non può essere modificato in modo da fare riferimento a una matrice diversa. È tuttavia possibile modificare gli elementi della matrice archiviati in un campo in sola lettura.|  
|CA2106|[CA2106: Asserzioni protette](../code-quality/ca2106-secure-asserts.md)|Un metodo asserisce un'autorizzazione e non vengono eseguiti controlli di sicurezza sul chiamante. Quando si asserisce un'autorizzazione di sicurezza senza eseguire alcun controllo di sicurezza, nel codice potrebbero restare punti deboli nella sicurezza.|  
|CA2107|[CA2107: Controllare l'utilizzo di Deny e PermitOnly](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Il metodo PermitOnly e le azioni di sicurezza CodeAccessPermission.Deny devono essere utilizzati esclusivamente da utenti con una conoscenza approfondita della sicurezza [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Il codice che usa queste azioni di sicurezza deve essere sottoposto a una revisione della sicurezza.|  
|CA2108|[CA2108: Controllare la sicurezza dichiarativa sui tipi di valori](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Un tipo di valore pubblico o protetto è protetto da richieste di collegamento o accesso ai dati.|  
|CA2109|[CA2109: Controllare i gestori di eventi visibili](../code-quality/ca2109-review-visible-event-handlers.md)|È stato rilevato un metodo di gestione eventi pubblico o protetto. I metodi di gestione eventi non devono essere esposti se non assolutamente necessario.|  
|CA2111|[CA2111: I puntatori non devono essere visibili](../code-quality/ca2111-pointers-should-not-be-visible.md)|Un puntatore non è privato, interno o in sola lettura. Il valore del puntatore può essere modificato dal codice dannoso e ciò può consentire potenzialmente l'accesso a percorsi arbitrari nella memoria o causare errori dell'applicazione o del sistema.|  
|CA2112|[CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|In un tipo pubblico o protetto sono inclusi campi pubblici; tale tipo viene protetto da richieste di collegamento. Se il codice ha accesso a un'istanza di un tipo protetta da una richiesta di collegamento, non è necessario che il codice soddisfi la richiesta di collegamento per accedere ai campi del tipo.|  
|CA2114|[CA2114: La sicurezza del metodo deve essere un superset del tipo](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Un metodo non può presentare sicurezza dichiarativa sia a livello di metodo sia a livello di tipo per la stessa azione.|  
|CA2115|[CA2115: Chiamare GC.KeepAlive durante l'uso di risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Questa regola rileva gli errori che possono verificarsi qualora una risorsa non gestita venga completata mentre è ancora usata da codice non gestito.|  
|CA2116|[CA2116: I metodi APTCA devono chiamare solo metodi APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Quando APTCA (AllowPartiallyTrustedCallersAttribute) è presente in un assembly completamente attendibile e l'assembly esegue codice in un altro assembly che non consente chiamanti parzialmente attendibili, è possibile che si verifichi una violazione della sicurezza.|  
|CA2117|[CA2117: I tipi APTCA devono estendere solo tipi di base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Quando APTCA è presente in un assembly totalmente attendibile e un tipo nell'assembly eredita da un tipo che non consente chiamanti parzialmente attendibili, è possibile che si verifichi una violazione della sicurezza.|  
|CA2118|[CA2118: Verificare la sintassi di SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|SuppressUnmanagedCodeSecurityAttribute consente di modificare il comportamento del sistema di sicurezza predefinito per i membri che eseguono codice non gestito mediante interoperabilità COM o chiamata al sistema operativo. Questo attributo viene principalmente utilizzato per aumentare le prestazioni. L'aumento delle prestazioni, tuttavia, comporta notevoli rischi in termini di sicurezza.|  
|CA2119|[CA2119: Impostare come sealed i metodi che soddisfano interfacce private](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Un tipo pubblico ereditabile fornisce un'implementazione di metodo sottoponibile a override di un'interfaccia interna (Friend in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Per correggere una violazione di questa regola, impedire che venga eseguito l'override del metodo esternamente all'assembly.|  
|CA2120|[CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)|Questo tipo dispone di un costruttore che accetta un oggetto System.Runtime.Serialization.SerializationInfo e un oggetto System.Runtime.Serialization.StreamingContext (la firma del costruttore di serializzazione). Questo costruttore non è protetto da un controllo di sicurezza, ma uno o più costruttori regolari nel tipo sono protetti.|  
|CA2121|[CA2121: I costruttori statici devono essere privati](../code-quality/ca2121-static-constructors-should-be-private.md)|Il costruttore statico viene chiamato prima che venga creata la prima istanza del tipo o venga fatto riferimento a qualsiasi membro statico. Se un costruttore statico non è privato, può essere chiamato da codice esterno al sistema. A seconda delle operazioni eseguite nel costruttore, questa situazione può causare comportamenti imprevisti.|  
|CA2122|[CA2122: Non esporre in modo indiretto metodi con richieste di collegamento](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Un membro pubblico o protetto presenta richieste di collegamento e viene chiamato da un membro che non esegue alcun controllo della sicurezza. Una richiesta di collegamento controlla esclusivamente le autorizzazioni del chiamante immediato.|  
|CA2123|[CA2123: Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Questa regola associa un metodo al relativo metodo di base che può essere un'interfaccia o un metodo virtuale in un altro tipo, quindi confronta le richieste di collegamento in ognuno. Se questa regola viene violata, un chiamante malintenzionato può ignorare la richiesta di collegamento chiamando semplicemente il metodo non sicuro.|  
|CA2124|[CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Un metodo pubblico o protetto contiene un blocco try/finally. Il blocco finally dovrebbe reimpostare lo stato di sicurezza e non è incluso in un altro blocco finally.|  
|CA2126|[CA2126: Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Un tipo non sealed pubblico è protetto utilizzando una richiesta di collegamento e dispone di un metodo sottoponibile a override. Né il tipo né il metodo sono protetti mediante una richiesta di ereditarietà.|  
|CA2127|[CA2136: I membri non devono avere annotazioni di trasparenza in conflitto](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|In un assembly trasparente al 100% non è possibile riscontrare codice critico. Questa regola analizza le annotazioni SecurityCritical a livello di tipo, campo e metodo di assembly trasparenti al 100%.|  
|CA2128|[CA2147: Il codice Transparent non può usare asserzioni di sicurezza](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Questa regola analizza tutti i metodi e tipi in un assembly trasparente al 100% o mista trasparente/critico e contrassegna l'utilizzo dichiarativo o imperativo di Assert.|  
|CA2129|[CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|I metodi contrassegnati con SecurityTransparentAttribute chiamano membri non pubblici, a loro volta contrassegnati con SecurityCritical. Questa regola analizza tutti i metodi e i tipi in un assembly trasparente/critico e contrassegna qualsiasi chiamata da codice trasparente a codice critico non pubblico non contrassegnato con SecurityTreatAsSafe.|  
|CA2130|[CA2130: Le costanti SecurityCritical devono essere Transparent](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|L'imposizione della trasparenza non viene applicata ai valori costanti perché i compilatori rendono inline valori costanti in modo che non sia richiesta alcuna ricerca in fase di esecuzione. I campi costanti devono essere trasparenti per la sicurezza in modo che i revisori del codice non suppongano che il codice trasparente non possa accedere alla costante.|  
|CA2131|[CA2131: I tipi SecurityCritical possono non partecipare all'equivalenza del tipo](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Un tipo partecipa all'equivalenza del tipo e il tipo stesso o un membro o un campo del tipo è contrassegnato utilizzando l'attributo SecurityCriticalAttribute. Questa regola viene applicata a qualsiasi tipo critico o a tipi che contengono metodi o campi critici che partecipano all'equivalenza del tipo. Quando CLR rileva tale tipo, non lo carica con TypeLoadException in fase di esecuzione. In genere, questa regola viene generata solo quando gli utenti implementano l'equivalenza del tipo manualmente, anziché utilizzare tlbimp e i compilatori per eseguire l'equivalenza del tipo.|  
|CA2132|[CA2132: I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|I tipi e i membri che presentano SecurityCriticalAttribute non possono essere usati dal codice dell'applicazione Silverlight. I tipi e i membri critici per la sicurezza possono essere utilizzati solo da codice attendibile nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] per Silverlight. Poiché una costruzione pubblica o protetta in una classe derivata deve disporre della trasparenza uguale o superiore alla classe di base, una classe in un'applicazione non può essere derivata da una classe contrassegnata come SecurityCritical.|  
|CA2133|[CA2133: Delegati devono essere associati ai metodi con trasparenza consistente](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Questo avviso è generato su un metodo che associa un delegato contrassegnato tramite SecurityCriticalAttribute a un metodo trasparente o contrassegnato tramite SecuritySafeCriticalAttribute. L'avviso viene generato anche su un metodo che associa un delegato trasparente o critico per la sicurezza a un metodo critico.|  
|CA2134|[CA2134: I metodi devono mantenere trasparenza consistente durante l'override dei metodi base](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Questa regola è generata quando un metodo contrassegnato tramite SecurityCriticalAttribute esegue l'override di un metodo trasparente o contrassegnato tramite SecuritySafeCriticalAttribute. Viene inoltre generata quando un metodo trasparente o contrassegnato tramite SecuritySafeCriticalAttribute esegue l'override di un metodo contrassegnato tramite SecurityCriticalAttribute. La regola è applicata in caso di esecuzione dell'override di un metodo virtuale o di implementazione di un'interfaccia.|  
|CA2135|[CA2135: Gli assembly di livello 2 non devono contenere LinkDemands](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|I LinkDemand sono deprecati nel set di regole per la sicurezza di livello 2. Anziché utilizzare i LinkDemand per applicare la sicurezza nella compilazione JIT, contrassegnare i metodi, i tipi e campi utilizzando l'attributo SecurityCriticalAttribute.|  
|CA2136|[CA2136: I membri non devono avere annotazioni di trasparenza in conflitto](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Gli attributi di trasparenza vengono applicati da elementi di codice con un ambito più ampio a elementi con ambito più ridotto. Gli attributi di trasparenza di elementi di codice che presentano un ambito più ampio hanno la precedenza su quelli contenuti nel primo elemento. Ad esempio, una classe contrassegnata tramite l'attributo SecurityCriticalAttribute non può contenere un metodo contrassegnato tramite l'attributo SecuritySafeCriticalAttribute.|  
|CA2137|[CA2137: I metodi Transparent devono contenere solo IL verificabile](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Un metodo contiene codice non verificabile o restituisce un tipo tramite riferimento. Questa regola viene generata nei tentativi tramite codice trasparente per la sicurezza per eseguire MISL (Microsoft Intermediate Language) non verificabile. Tuttavia, la regola non contiene un verificatore di IL completo, ma usa invece regole euristiche per intercettare la maggior parte delle violazioni di verifica MSIL.|  
|CA2138|[CA2138: I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Un metodo trasparente per la sicurezza chiama un metodo contrassegnato tramite l'attributo SuppressUnmanagedCodeSecurityAttribute.|  
|CA2139|[CA2139: I metodi Transparent non possono usare l'attributo HandleProcessCorruptingExceptions](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Questa regola è generata da qualsiasi metodo trasparente che tenti di gestire un'eccezione che danneggia il processo tramite l'attributo HandleProcessCorruptedStateExceptionsAttribute. Un'eccezione che danneggia il processo è una classificazione di eccezione CLR versione 4.0, ad esempio AccessViolationException. L'attributo HandleProcessCorruptedStateExceptionsAttribute può essere utilizzato solo dai metodi SecurityCritical e sarà ignorato se applicato a un metodo trasparente.|  
|CA2140|[CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Un elemento di codice contrassegnato tramite l'attributo SecurityCriticalAttribute è SecurityCritical. Un metodo trasparente non può utilizzare un elemento critico per la sicurezza. Se un tipo trasparente tenta di utilizzare un tipo SecurityCritical viene generata un eccezione TypeAccessException, MethodAccessException o FieldAccessException.|  
|CA2141|[CA2141:I metodi Transparent non devono soddisfare i LinkDemand](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Un metodo trasparente per la sicurezza chiama un metodo in un assembly che non è contrassegnato tramite APTCA oppure un metodo trasparente per la sicurezza soddisfa un LinkDemand per un tipo o un metodo.|  
|CA2142|[CA2142: Il codice Transparent non deve essere protetto con LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Questa regola funziona in metodi trasparenti che richiedono l'accesso da parte dei LinkDemand. Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni.|  
|CA2143|[CA2143: I metodi Transparent non devono usare SecurityDemand](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Il codice trasparente per la sicurezza deve usare richieste complete per prendere decisioni relative alla sicurezza e il codice critico per la sicurezza non deve basarsi sul codice trasparente per l'esecuzione della richiesta completa.|  
|CA2144|[CA2144: Il codice Transparent non deve caricare assembly da matrici di byte](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|La revisione di sicurezza per il codice trasparente non è completa come la revisione di sicurezza per il codice critico, perché il primo non può eseguire azioni sensibili per la sicurezza. Assembly caricati da una matrice di byte potrebbero non essere notati nel codice trasparente e tale matrice di byte potrebbe contenere codice critico o, ancora più importante, codice critico per la sicurezza che è necessario controllare.|  
|CA2145|[CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|I metodi decorati mediante l'attributo SuppressUnmanagedCodeSecurityAttribute presentano un LinkDemand implicito su ogni metodo che lo chiama. Questo LinkDemand richiede che il codice che effettua la chiamata sia critico per la sicurezza. Contrassegnare il metodo che utilizza SuppressUnmanagedCodeSecurity mediante l'attributo SecurityCriticalAttribute rende più ovvio questo requisito per i chiamanti del metodo.|  
|CA2146|[CA2146: I tipi devono essere Critical almeno come le interfacce e i tipi base relativi](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Questa regola viene generata quando un tipo derivato dispone di un attributo di trasparenza di sicurezza che non è critico come il relativo tipo di base o la relativa interfaccia implementata. Solo i tipi critici possono derivare da tipi di base critici o implementare interfacce critiche e solo tipi critici o critici per la sicurezza possono derivare da tipi di base critici per la sicurezza o implementare interfacce critiche per la sicurezza.|  
|CA2147|[CA2147: Il codice Transparent non può usare asserzioni di sicurezza](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Al codice contrassegnato come SecurityTransparentAttribute non sono concesse autorizzazioni sufficienti per l'asserzione.|  
|CA2149|[CA2149: I metodi Transparent non devono effettuare chiamate nel codice nativo](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Questa regola viene generata in qualsiasi metodo trasparente che chiama direttamente nel codice nativo (ad esempio, tramite P/Invoke). Le violazioni di questa regola conducono a MethodAccessException nel modello di trasparenza di livello 2 e a una richiesta completa per UnmanagedCode nel modello di trasparenza di livello 1.|  
|CA2151|[CA2151: I campi con tipi critici devono essere SecurityCritical](../code-quality/ca2151-fields-with-critical-types-should-be-security-critical.md)|Per usare i tipi critici per la sicurezza, il codice che fa riferimento al tipo deve essere critico per la sicurezza critico per la sicurezza e richiamabile da codice trasparente. Questo vale anche se il riferimento è indiretto. Pertanto, un campo trasparente per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente è fuorviante perché il codice trasparente non potrà comunque accedere al campo.|  
|CA2200|[CA2200: Eseguire il rethrow per mantenere i dettagli dello stack](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Viene generata di nuovo un'eccezione, specificata in modo esplicito nell'istruzione throw. Se un'eccezione viene generata di nuovo tramite la specifica nell'istruzione throw, l'elenco di chiamate ai metodi tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso.|  
|CA2201|[CA2201: Non generare tipi di eccezione riservati](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Tale circostanza complica il rilevamento e il debug dell'errore originale.|  
|CA2202|[CA2202: Non eliminare oggetti più volte](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Un'implementazione di metodo contiene percorsi del codice che potrebbero comportare più chiamate a System.IDisposable.Dispose o a un equivalente di Dispose (ad esempio un metodo Close() per alcuni tipi) sullo stesso oggetto.|  
|CA2204|[CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Una stringa letterale in un corpo del metodo contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.|  
|CA2205|[CA2205: Usare equivalenti gestiti dell'API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Viene definito un metodo di chiamata del sistema operativo e un metodo che dispone della funzionalità equivalente si trova nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].|  
|CA2207|[CA2207: Inizializzare i campi statici dei tipi di valore inline](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Un tipo di valore dichiara un costruttore statico esplicito. Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico.|  
|CA2208|[CA2208: Creare istanze di eccezioni di argomento correttamente](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Viene effettuata una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione che corrisponde a o deriva da ArgumentException oppure viene passato un argomento stringa non corretto a un costruttore con parametri di un tipo di eccezione che corrisponde a o deriva da ArgumentException.|  
|CA2210|[CA2210: Gli assembly devono avere nomi sicuri validi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Il nome sicuro protegge i client dal caricamento involontario di un assembly alterato. Gli assembly con nomi sicuri non devono essere distribuiti al di fuori di scenari molto limitati. Se si condividono o distribuiscono assembly non firmati correttamente, l'assembly può essere alterato, non essere caricato in Common Language Runtime oppure l'utente potrebbe avere la necessità di disabilitare la verifica nel proprio computer.|  
|CA2211|[CA2211: I campi non costanti non devono essere visibili](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|I campi statici che non sono costanti né in sola lettura non sono thread-safe. L'accesso a tali campi deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe.|  
|CA2212|[CA2212: Non contrassegnare componenti serviti con WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Un metodo in un tipo che eredita da System.EnterpriseServices.ServicedComponent è contrassegnato utilizzando System.Web.Services.WebMethodAttribute. Poiché WebMethodAttribute e un metodo ServicedComponent presentano comportamenti e requisiti di contesto e flusso di transazioni in conflitto tra loro, il comportamento del metodo non sarà corretto in determinati scenari.|  
|CA2213|[CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Un tipo che implementa System.IDisposable dichiara i campi di tipi che implementano anch'essi IDisposable. Il metodo Dispose del campo non viene chiamato dal metodo Dispose del tipo dichiarante.|  
|CA2214|[CA2214: Non chiamare metodi sottoponibili a override nei costruttori](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non sia stato eseguito.|  
|CA2215|[CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Se un tipo eredita da un tipo eliminabile, deve chiamare il metodo Dispose del tipo di base dal proprio metodo Dispose.|  
|CA2216|[CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Un tipo che implementa System.IDisposable e include campi che suggeriscono l'utilizzo di risorse non gestite non implementa un finalizzatore, come descritto da Object.Finalize.|  
|CA2217|[CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Un'enumerazione visibile esternamente è contrassegnata utilizzando FlagsAttribute e presenta uno o più valori che non sono potenze di due o una combinazione degli altri valori definiti nell'enumerazione.|  
|CA2218|[CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode restituisce un valore, basato sull'istanza corrente, appropriato per algoritmi di hash e strutture dei dati come una tabella hash. Due oggetti dello stesso tipo e uguali devono restituire lo stesso codice hash.|  
|CA2219|[CA2219: Non generare eccezioni in clausole di eccezione](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Quando un'eccezione viene generata in una clausola finally o in una clausola fault, la nuova eccezione nasconde l'eccezione attiva. Quando un'eccezione viene generata in una clausola filter, il runtime rileva l'eccezione automaticamente. Tale circostanza complica il rilevamento e il debug dell'errore originale.|  
|CA2220|[CA2220: I finalizzatori devono chiamare il finalizzatore della classe base](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. A tale scopo, i tipi devono chiamare il metodo Finalize della classe di base nel proprio metodo Finalize.|  
|CA2221|[CA2221: I finalizzatori devono essere protetti](../code-quality/ca2221-finalizers-should-be-protected.md)|I finalizzatori devono utilizzare il modificatore di accesso a livello di famiglia.|  
|CA2222|[CA2222: Non diminuire la visibilità di membri ereditati](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Non modificare il modificatore di accesso per i membri ereditati. La modifica in privato di un membro ereditato non impedisce ai chiamanti di accedere all'implementazione della classe base del metodo.|  
|CA2223|[CA2223: La differenza tra membri non deve limitarsi al tipo restituito](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Nonostante Common Language Runtime consenta l'utilizzo di tipi restituiti per differenziare membri altrimenti identici, questa funzionalità non è inclusa nella specifica CLS (Common Language Specification) e non è una funzionalità comune dei linguaggi di programmazione .NET.|  
|CA2224|[CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Un tipo pubblico implementa l'operatore di uguaglianza, ma non esegue l'override di Object.Equals.|  
|CA2225|[CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato. Il membro alternativo denominato fornisce accesso alla stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano operatori di overload.|  
|CA2226|[CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Un tipo implementa l'operatore di uguaglianza o di disuguaglianza e non implementa l'operatore opposto.|  
|CA2227|[CA2227: Le proprietà di raccolte devono essere in sola lettura](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri.|  
|CA2228|[CA2228: Non specificare formati di risorse non rilasciati](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|I file di risorse compilati utilizzando versioni preliminari di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] potrebbero non essere utilizzabili dalle versioni supportate di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].|  
|CA2229|[CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)|Per correggere una violazione di questa regola, implementare il costruttore di serializzazione. Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto.|  
|CA2230|[CA2230: Usare params per argomenti variabili](../code-quality/ca2230-use-params-for-variable-arguments.md)|Un tipo pubblico o protetto contiene un metodo pubblico o protetto che utilizza la convenzione di chiamata VarArgs anziché la parola chiave params.|  
|CA2231|[CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Un tipo di valore esegue l'override di Object.Equals, ma non implementa l'operatore di uguaglianza.|  
|CA2232|[CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute indica che il modello di threading COM per l'applicazione è un apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente.|  
|CA2233|[CA2233: Evitare l'overflow delle operazioni](../code-quality/ca2233-operations-should-not-overflow.md)|Non eseguire operazioni aritmetiche senza prima convalidare gli operandi. In questo modo si verifica che il risultato dell'operazione non sia esterno all'intervallo di valori possibili per i tipi di dati coinvolti.|  
|CA2234|[CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Viene effettuata una chiamata a un metodo che dispone di un parametro di stringa il cui nome contiene "uri", "URI", "urn", "URN", "url" o "URL". Il tipo dichiarante del metodo contiene un overload del metodo corrispondente con un parametro System.Uri.|  
|CA2235|[CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.|  
|CA2236|[CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Per correggere una violazione di questa regola, chiamare il costruttore di serializzazione o il metodo GetObjectData del tipo di base dal costruttore o dal metodo del tipo derivato corrispondente.|  
|CA2237|[CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Affinché i tipi vengano riconosciuti come serializzabili in Common Language Runtime, è necessario che siano contrassegnati utilizzando l'attributo SerializableAttribute anche quando utilizzano una routine di serializzazione personalizzata tramite l'implementazione dell'interfaccia ISerializable.|  
|CA2238|[CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Un metodo che gestisce un evento di serializzazione non dispone della visibilità, del tipo restituito o della firma corretta.|  
|CA2239|[CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Un tipo include un campo contrassegnato utilizzando l'attributo System.Runtime.Serialization.OptionalFieldAttribute e non fornisce metodi di gestione degli eventi di deserializzazione.|  
|CA2240|[CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)|Per correggere una violazione di questa regola, impostare il metodo GetObjectData come visibile e sottoponibile a override e accertarsi che tutti i campi di istanza siano inclusi nel processo di serializzazione o contrassegnati in modo esplicito utilizzando l'attributo NonSerializedAttribute.|  
|CA2241|[CA2241: Specificare argomenti corretti ai metodi di formattazione](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|L'argomento format passato a System.String.Format non contiene un elemento di formato corrispondente a ogni argomento dell'oggetto o viceversa.|  
|CA2242|[CA2242: Testare i valori NaN in modo corretto](../code-quality/ca2242-test-for-nan-correctly.md)|Questa espressione consente di testare un valore rispetto a Single.Nan o Double.Nan. Utilizzare Single.IsNan(Single) o Double.IsNan(Double) per testare il valore.|  
|CA2243|[CA2243: Valori letterali stringa di attributo devono essere analizzate correttamente](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Il parametro del valore letterale stringa di un attributo non esegue l'analisi corretta di un URL, un GUID o una versione.|  
|CA5122|[Dichiarazioni ca5122 le P/Invoke non devono essere critici](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md)|I metodi sono contrassegnati come SecuritySafeCritical quando viene eseguita un'operazione sensibile di sicurezza, ma possono anche essere usati in sicurezza dal codice trasparente. Il codice trasparente non può mai chiamare direttamente il codice nativo tramite P/Invoke. Di conseguenza, contrassegnare P/Invoke come critico per la sicurezza e richiamabile da codice trasparente non consentirà al codice trasparente di chiamarlo ed è fuorviante per l'analisi di sicurezza.|