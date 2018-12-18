---
title: Annotazione di parametri di funzione e valori restituiti
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a06a987dc94ac4f3eb71d047ba33d410d7391a91
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="annotating-function-parameters-and-return-values"></a>Annotazione di parametri di funzione e valori restituiti
Questo articolo vengono descritti gli utilizzi tipici di annotazioni per i parametri di funzione semplice, ovvero valori scalari e puntatori a strutture e classi e la maggior parte dei tipi di buffer.  Questo articolo illustra anche i modelli di utilizzo comune per le annotazioni. Per ulteriori annotazioni che sono correlate alle funzioni, vedere [annotazione del comportamento della funzione](../code-quality/annotating-function-behavior.md)

## <a name="pointer-parameters"></a>Parametri dei puntatori
 Per le annotazioni nella tabella seguente, quando un parametro del puntatore viene annotato, l'analizzatore segnala un errore se il puntatore è null.  Questo vale per i puntatori e a qualsiasi elemento di dati a cui punta.

 **Le annotazioni e descrizioni**

-   `_In_`

     Annota parametri di input sono valori scalari, strutture, i puntatori alle strutture e così via.  In modo esplicito può essere utilizzata con valori scalari semplici.  Il parametro deve essere valido in pre- stato di e non verrà modificato.

-   `_Out_`

     Annota i parametri di output che sono valori scalari, strutture, i puntatori alle strutture e così via.  Non applicare a un oggetto che non può restituire un valore, ad esempio, un valore scalare che viene passato per valore.  Il parametro non deve essere valido in pre- stato di ma deve essere valido in post stato di.

-   `_Inout_`

     Annota un parametro che verrà modificato dalla funzione.  Deve essere valido sia pre-stato e post-stato, ma si presuppone che hanno valori diversi prima e dopo la chiamata. È necessario applicare a un valore modificabile.

-   `_In_z_`

     Un puntatore a una stringa con terminazione null che viene utilizzato come input.  La stringa deve essere valida nello stato precedente.  Varianti di `PSTR`, che già le annotazioni corretto, vengono preferiti.

-   `_Inout_z_`

     Un puntatore a una matrice di caratteri con terminazione null che verrà modificata.  Deve essere valido prima e dopo la chiamata, ma si presuppone che il valore sono stati modificati.  Il terminatore null può essere spostato, ma sono accessibili solo gli elementi fino al terminatore null originale.

-   `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Puntatore a una matrice, che viene letto dalla funzione.  La matrice è di dimensioni `s` elementi, ognuno dei quali deve essere valido.

     Il `_bytes_` variante fornisce la dimensione in byte anziché gli elementi. Utilizzare questo metodo solo quando le dimensioni non possono essere espresse come elementi.  Ad esempio, `char` utilizzano stringhe di `_bytes_` variant solo se simili di funzione che utilizza `wchar_t` sarebbe.

-   `_In_reads_z_(s)`

     Un puntatore a una matrice con terminazione null e ha una dimensione nota. Gli elementi fino a terminazione null, o `s` se è presente alcun carattere di terminazione null, deve essere valido nello stato precedente.  Se le dimensioni sono note in byte, applicare la scalabilità `s` per la dimensione dell'elemento.

-   `_In_reads_or_z_(s)`

     Un puntatore a una matrice con terminazione null o con una dimensione nota, o entrambi. Gli elementi fino a terminazione null, o `s` se è presente alcun carattere di terminazione null, deve essere valido nello stato precedente.  Se le dimensioni sono note in byte, applicare la scalabilità `s` per la dimensione dell'elemento.  (Utilizzato per il `strn` famiglia.)

-   `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Un puntatore a una matrice di `s` elementi (rispettivamente. byte) che verranno scritte dalla funzione.  Gli elementi della matrice non deve essere valido in pre- stato di e il numero di elementi che sono validi in post-stato di non è specificato.  Se sono presenti le annotazioni del tipo di parametro, vengono applicate in post stato di. Si consideri il codice di esempio seguente.

     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`

     In questo esempio, il chiamante fornisce un buffer di `size` elementi per `p1`.  `MyStringCopy` rende alcuni di tali elementi validi. Ancora più importante, la `_Null_terminated_` annotazione in `PWSTR` significa che `p1` è con terminazione null in post stato di.  In questo modo, il numero di elementi validi è ancora ben definito, ma il numero di un elemento specifico non è obbligatorio.

     Il `_bytes_` variante fornisce la dimensione in byte anziché gli elementi. Utilizzare questo metodo solo quando le dimensioni non possono essere espresse come elementi.  Ad esempio, `char` utilizzano stringhe di `_bytes_` variant solo se simili di funzione che utilizza `wchar_t` sarebbe.

-   `_Out_writes_z_(s)`

     Un puntatore a una matrice di `s` elementi.  Gli elementi non si dispone sia valido nello stato precedente.  Lo stato post-, gli elementi di backup tramite il carattere di terminazione null, che deve essere presente, deve essere valido.  Se le dimensioni sono note in byte, applicare la scalabilità `s` per la dimensione dell'elemento.

-   `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Puntatore a una matrice, che viene letta e scritta nella funzione.  È di dimensioni `s` elementi e lo pre-stato di e post-stato è valido.

     Il `_bytes_` variante fornisce la dimensione in byte anziché gli elementi. Utilizzare questo metodo solo quando le dimensioni non possono essere espresse come elementi.  Ad esempio, `char` utilizzano stringhe di `_bytes_` variant solo se simili di funzione che utilizza `wchar_t` sarebbe.

-   `_Inout_updates_z_(s)`

     Un puntatore a una matrice con terminazione null e ha una dimensione nota. Gli elementi di backup tramite il carattere di terminazione null, che deve essere presente, deve essere valido sia pre-stato e post-stato.  Il valore in post-stato di presuppone che sia diverso dal valore dello stato di pre; Ciò include la posizione del carattere di terminazione null. Se le dimensioni sono note in byte, applicare la scalabilità `s` per la dimensione dell'elemento.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Un puntatore a una matrice di `s` elementi.  Gli elementi non si dispone sia valido nello stato precedente.  Lo stato post-, gli elementi fino al `c`- esimo elemento deve essere valido.  Se le dimensioni sono note in byte, applicare la scalabilità `s` e `c` per la dimensione dell'elemento o l'uso di `_bytes_` variante, che viene definito come:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     In altre parole, ogni elemento che esiste nel buffer, fino a `s` nello stato precedente è valida nello post stato di.  Ad esempio:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Puntatore a una matrice, che viene letta e scritta dalla funzione.  È di dimensioni `s` elementi, ognuno dei quali deve essere valido in pre-stato di, e `c` in post-stato di gli elementi devono essere validi.

     Il `_bytes_` variante fornisce la dimensione in byte anziché gli elementi. Utilizzare questo metodo solo quando le dimensioni non possono essere espresse come elementi.  Ad esempio, `char` utilizzano stringhe di `_bytes_` variant solo se simili di funzione che utilizza `wchar_t` sarebbe.

-   `_Inout_updates_z_(s)`

     Un puntatore a una matrice con terminazione null e ha una dimensione nota. Gli elementi di backup tramite il carattere di terminazione null, che deve essere presente, deve essere valido sia pre-stato e post-stato.  Il valore in post-stato di presuppone che sia diverso dal valore dello stato di pre; Ciò include la posizione del carattere di terminazione null. Se le dimensioni sono note in byte, applicare la scalabilità `s` per la dimensione dell'elemento.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Un puntatore a una matrice di `s` elementi.  Gli elementi non si dispone sia valido nello stato precedente.  Lo stato post-, gli elementi fino al `c`- esimo elemento deve essere valido.  Se le dimensioni sono note in byte, applicare la scalabilità `s` e `c` per la dimensione dell'elemento o l'uso di `_bytes_` variante, che viene definito come:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     In altre parole, ogni elemento che esiste nel buffer, fino a `s` nello stato precedente è valida nello post stato di.  Ad esempio:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Puntatore a una matrice, che viene letta e scritta dalla funzione.  È di dimensioni `s` elementi, ognuno dei quali deve essere valido in pre-stato di, e `c` in post-stato di gli elementi devono essere validi.

     Il `_bytes_` variante fornisce la dimensione in byte anziché gli elementi. Utilizzare questo metodo solo quando le dimensioni non possono essere espresse come elementi.  Ad esempio, `char` utilizzano stringhe di `_bytes_` variant solo se simili di funzione che utilizza `wchar_t` sarebbe.

-   `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Un puntatore a una matrice, che viene letta e scritta dalla funzione delle dimensioni `s` elementi. Definito come equivalente a:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     In altre parole, ogni elemento che esiste nel buffer, fino a `s` nello stato precedente è valida nello pre- stato di e post-stato.

     Il `_bytes_` variante fornisce la dimensione in byte anziché gli elementi. Utilizzare questo metodo solo quando le dimensioni non possono essere espresse come elementi.  Ad esempio, `char` utilizzano stringhe di `_bytes_` variant solo se simili di funzione che utilizza `wchar_t` sarebbe.

-   `_In_reads_to_ptr_(p)`

     Un puntatore a una matrice per cui l'espressione `p`  -  `_Curr_` (vale a dire `p` meno `_Curr_`) è definito per la lingua appropriata standard.  Gli elementi prima di `p` deve essere valido nello stato precedente.

-   `_In_reads_to_ptr_z_(p)`

     Un puntatore a una matrice con terminazione null per i quali l'espressione `p`  -  `_Curr_` (vale a dire `p` meno `_Curr_`) è definito per la lingua appropriata standard.  Gli elementi prima di `p` deve essere valido nello stato precedente.

-   `_Out_writes_to_ptr_(p)`

     Un puntatore a una matrice per cui l'espressione `p`  -  `_Curr_` (vale a dire `p` meno `_Curr_`) è definito per la lingua appropriata standard.  Gli elementi prima di `p` non deve essere valido in pre- stato di e deve essere valido in post stato di.

-   `_Out_writes_to_ptr_z_(p)`

     Un puntatore a una matrice con terminazione null per i quali l'espressione `p`  -  `_Curr_` (vale a dire `p` meno `_Curr_`) è definito per la lingua appropriata standard.  Gli elementi prima di `p` non deve essere valido in pre- stato di e deve essere valido in post stato di.

## <a name="optional-pointer-parameters"></a>Parametri facoltativi puntatore
 Se un'annotazione di parametro puntatore include `_opt_`, indica che il parametro può essere null. In caso contrario, l'annotazione esegue la stessa versione che non include `_opt_`. Ecco un elenco di `_opt_` varianti delle annotazioni di parametro puntatore:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Puntatore a parametri di output
 I parametri di output puntatore richiedono notazione speciale per risolvere l'ambiguità caratteristica null nel parametro e il percorso a cui punta.

 **Le annotazioni e descrizioni**

-   `_Outptr_`

     Parametro non può essere null e lo stato post-il percorso a cui punta può essere null e deve essere valido.

-   `_Outptr_opt_`

     Parametro può essere null, ma lo stato post-il percorso a cui punta può essere null e deve essere valido.

-   `_Outptr_result_maybenull_`

     Parametro non può essere null e lo stato post-il percorso a cui punta può essere null.

-   `_Outptr_opt_result_maybenull_`

     Parametro può essere null e lo stato post-il percorso a cui punta può essere null.

 Nella tabella seguente, sottostringhe aggiuntive vengono inserite nel nome di annotazione per qualificare ulteriormente il significato dell'annotazione.  Sono diverse sottostringhe `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, e `_to_`.

> [!IMPORTANT]
>  Se l'interfaccia che si inseriscono annotazioni COM, utilizzare il modulo COM di queste annotazioni. Non utilizzare le annotazioni di COM con qualsiasi altra interfaccia di tipo.

 **Le annotazioni e descrizioni**

-   `_Outptr_result_z_`

     `_Outptr_opt_result_z_`

     `_Outptr_result_maybenull_z_`

     `_Ouptr_opt_result_maybenull_z_`

     Il puntatore restituito ha il `_Null_terminated_` annotazione.

-   `_COM_Outptr_`

     `_COM_Outptr_opt_`

     `_COM_Outptr_result_maybenull_`

     `_COM_Outptr_opt_result_maybenull_`

     Il puntatore restituito presenta la semantica di COM ed esegue pertanto un `_On_failure_` post-condizione che il puntatore restituito è null.

-   `_Outptr_result_buffer_(s)`

     `_Outptr_result_bytebuffer_(s)`

     `_Outptr_opt_result_buffer_(s)`

     `_Outptr_opt_result_bytebuffer_(s)`

     Il puntatore restituito punta a un buffer di dimensione valido `s` elementi o byte.

-   `_Outptr_result_buffer_to_(s, c)`

     `_Outptr_result_bytebuffer_to_(s, c)`

     `_Outptr_opt_result_buffer_to_(s,c)`

     `_Outptr_opt_result_bytebuffer_to_(s,c)`

     Il puntatore restituito punta a un buffer di dimensione `s` elementi o byte, di cui il primo `c` sono validi.

 Alcune convenzioni interfaccia presumono che i parametri di output sono considerati eliminati in caso di errore.  Ad eccezione di in modo esplicito codice COM, i moduli nella tabella seguente sono preferiti.  Per il codice COM, utilizzare le corrispondenti forme COM sono elencate nella sezione precedente.

 **Le annotazioni e descrizioni**

-   `_Result_nullonfailure_`

     Modifica di altre annotazioni. Il risultato viene impostato su null se la funzione ha esito negativo.

-   `_Result_zeroonfailure_`

     Modifica di altre annotazioni. Il risultato viene impostato su zero se la funzione ha esito negativo.

-   `_Outptr_result_nullonfailure_`

     Il puntatore restituito punta a un buffer valido se la funzione ha esito positivo, o null se la funzione ha esito negativo. Questa annotazione è per un parametro non è facoltativo.

-   `_Outptr_opt_result_nullonfailure_`

     Il puntatore restituito punta a un buffer valido se la funzione ha esito positivo, o null se la funzione ha esito negativo. Questa annotazione è per un parametro facoltativo.

-   `_Outref_result_nullonfailure_`

     Il puntatore restituito punta a un buffer valido se la funzione ha esito positivo, o null se la funzione ha esito negativo. Questa annotazione è per un parametro di riferimento.

## <a name="output-reference-parameters"></a>Parametri di riferimento di output
 Un utilizzo comune del parametro di riferimento è per i parametri di output.  Per i parametri di riferimento di output semplici, ad esempio, `int&`:`_Out_` fornisce la semantica corretta.  Tuttavia, quando il valore di output è un puntatore, ad esempio `int *&`: le annotazioni equivalenti puntatore come `_Outptr_ int **` non forniscono la semantica corretta.  Per esprimere in modo conciso la semantica di riferimento dei parametri di output per i tipi di puntatore, utilizzare queste annotazioni composite:

 **Le annotazioni e descrizioni**

-   `_Outref_`

     Risultato deve essere in post-stato di valido e non può essere null.

-   `_Outref_result_maybenull_`

     Risultato deve essere in post-stato di valido, ma può essere null in post stato di.

-   `_Outref_result_buffer_(s)`

     Risultato deve essere in post-stato di valido e non può essere null. Punta a un buffer di dimensione valido `s` elementi.

-   `_Outref_result_bytebuffer_(s)`

     Risultato deve essere in post-stato di valido e non può essere null. Punta a un buffer di dimensione valido `s` byte.

-   `_Outref_result_buffer_to_(s, c)`

     Risultato deve essere in post-stato di valido e non può essere null. Punta a buffer di `s` elementi, di cui il primo `c` sono validi.

-   `_Outref_result_bytebuffer_to_(s, c)`

     Risultato deve essere in post-stato di valido e non può essere null. Punta a buffer di `s` byte di cui il primo `c` sono validi.

-   `_Outref_result_buffer_all_(s)`

     Risultato deve essere in post-stato di valido e non può essere null. Punta a un buffer di dimensione valido `s` elementi validi.

-   `_Outref_result_bytebuffer_all_(s)`

     Risultato deve essere in post-stato di valido e non può essere null. Punta a un buffer valido di `s` byte di elementi validi.

-   `_Outref_result_buffer_maybenull_(s)`

     Risultato deve essere in post-stato di valido, ma può essere null in post stato di. Punta a un buffer di dimensione valido `s` elementi.

-   `_Outref_result_bytebuffer_maybenull_(s)`

     Risultato deve essere in post-stato di valido, ma può essere null in post stato di. Punta a un buffer di dimensione valido `s` byte.

-   `_Outref_result_buffer_to_maybenull_(s, c)`

     Risultato deve essere in post-stato di valido, ma può essere null in post stato di. Punta a buffer di `s` elementi, di cui il primo `c` sono validi.

-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Risultato deve essere in post-stato di valido, ma può essere null in stato di post. Punta a buffer di `s` byte di cui il primo `c` sono validi.

-   `_Outref_result_buffer_all_maybenull_(s)`

     Risultato deve essere in post-stato di valido, ma può essere null in stato di post. Punta a un buffer di dimensione valido `s` elementi validi.

-   `_Outref_result_bytebuffer_all_maybenull_(s)`

     Risultato deve essere in post-stato di valido, ma può essere null in stato di post. Punta a un buffer valido di `s` byte di elementi validi.

## <a name="return-values"></a>Valori restituiti
 Il valore restituito di una funzione simile a un `_Out_` parametro ma è un livello diverso di de-reference e non è necessario prendere in considerazione il concetto di puntatore al risultato.  Per le seguenti annotazioni, il valore restituito è l'oggetto con annotazioni, ovvero un valore scalare, un puntatore a una struttura o un puntatore a un buffer. Queste annotazioni hanno la stessa semantica corrispondente `_Out_` annotazione.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="other-common-annotations"></a>Altre annotazioni comuni
 **Le annotazioni e descrizioni**

-   `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Il parametro, un campo o un risultato è compreso nell'intervallo (inclusivo) da `low` a `hi`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` applicato all'oggetto annotato con le condizioni di pre- stato di o post-state appropriate.

    > [!IMPORTANT]
    >  Anche se i nomi contengono "in" e "out", la semantica di `_In_` e `_Out_` si **non** si applicano a queste annotazioni.

-   `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Il valore annotato è esattamente `expr`.  Equivalente a `_Satisfies_(_Curr_ == expr)` applicato all'oggetto annotato con le condizioni di pre- stato di o post-state appropriate.

-   `_Struct_size_bytes_(size)`

     Si applica a una dichiarazione di classe o struct.  Indica che un oggetto valido di tale tipo può essere maggiore rispetto al tipo dichiarato, con il numero di byte viene fornito dal `size`.  Ad esempio:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Le dimensioni del buffer in byte di un parametro `pM` di tipo `MyStruct *` viene quindi considerato:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Risorse correlate
 [Blog del Team di analisi del codice](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>Vedere anche
 [Utilizzo delle annotazioni SAL per ridurre gli errori del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [comprensione SAL](../code-quality/understanding-sal.md) [annotazione del comportamento della funzione](../code-quality/annotating-function-behavior.md) [annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md) [ Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md) [specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md) [funzioni intrinseche](../code-quality/intrinsic-functions.md) [suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)