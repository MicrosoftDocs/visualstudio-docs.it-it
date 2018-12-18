---
title: SymTagEnum | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9165059991e4b961fc995b96a0c285f28a1587b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="symtagenum"></a>SymTagEnum
Specifica il tipo di simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>Elementi  
 `SymTagNull`  
 Indica che il simbolo non esiste alcun tipo.  
  
 `SymTagExe`  
 Indica che il simbolo è un file .exe. È presente un solo `SymTagExe` simbolo per ogni archivio simboli. Serve come ambito globale e non ha un padre lessicale.  
  
 `SymTagCompiland`  
 Indica il simbolo di modulo per ogni componente compilando dell'archivio di simboli. Per le applicazioni native, `SymTagCompiland` simboli corrispondano per i file oggetto collegati nell'immagine. Per alcuni tipi di immagini di Microsoft Intermediate Language (MSIL), è disponibile un modulo per ogni classe.  
  
 `SymTagCompilandDetails`  
 Indica che il simbolo contiene attributi estesi del modulo. Recupero di queste proprietà può richiedere il caricamento dei simboli di modulo.  
  
 `SymTagCompilandEnv`  
 Indica che il simbolo è una stringa di ambiente definita per il modulo.  
  
 `SymTagFunction`  
 Indica che il simbolo è una funzione.  
  
 `SymTagBlock`  
 Indica che il simbolo è un blocco nidificato.  
  
 `SymTagData`  
 Indica che il simbolo di dati.  
  
 `SymTagAnnotation`  
 Indica che il simbolo è per un'annotazione del codice. Gli elementi figlio di questo simbolo sono stringhe di dati costanti (`SymTagData`, `LocIsConstant`, `DataIsConstant`). La maggior parte dei client ignorare questo simbolo.  
  
 `SymTagLabel`  
 Indica che il simbolo è un'etichetta.  
  
 `SymTagPublicSymbol`  
 Indica che il simbolo è un simbolo pubblico. Per le applicazioni native, questo simbolo è il simbolo esterno COFF rilevato durante il collegamento dell'immagine.  
  
 `SymTagUDT`  
 Indica che il simbolo è un tipo definito dall'utente (struttura, classe o unione).  
  
 `SymTagEnum`  
 Indica che il simbolo è un'enumerazione.  
  
 `SymTagFunctionType`  
 Indica che il simbolo è un tipo di firma della funzione.  
  
 `SymTagPointerType`  
 Indica che il simbolo è un tipo di puntatore.  
  
 `SymTagArrayType`  
 Indica che il simbolo è un tipo di matrice.  
  
 `SymTagBaseType`  
 Indica che il simbolo è un tipo di base.  
  
 `SymTagTypedef`  
 Indica che il simbolo è un `typedef`, vale a dire un alias per un altro tipo.  
  
 `SymTagBaseClass`  
 Indica che il simbolo è una classe base di un tipo definito dall'utente.  
  
 `SymTagFriend`  
 Indica che il simbolo è un elemento friend di un tipo definito dall'utente.  
  
 `SymTagFunctionArgType`  
 Indica che il simbolo è un argomento di funzione.  
  
 `SymTagFuncDebugStart`  
 Indica che il simbolo è la posizione finale del codice di prologo della funzione.  
  
 `SymTagFuncDebugEnd`  
 Indica che il simbolo è la posizione di inizio del codice di epilogo della funzione.  
  
 `SymTagUsingNamespace`  
 Indica che il simbolo è un nome di spazio dei nomi attivo nell'ambito corrente.  
  
 `SymTagVTableShape`  
 Indica che il simbolo è una descrizione della tabella virtuale.  
  
 `SymTagVTable`  
 Indica che il simbolo è un puntatore di tabella virtuale.  
  
 `SymTagCustom`  
 Indica che il simbolo è un simbolo personalizzato e non verrà interpretato da DIA.  
  
 `SymTagThunk`  
 Indica che il simbolo è un thunk usato per condividere dati tra 16 e il codice a 32 bit.  
  
 `SymTagCustomType`  
 Indica che il simbolo è un simbolo di compilazione personalizzata.  
  
 `SymTagManagedType`  
 Indica che il simbolo nei metadati.  
  
 `SymTagDimension`  
 Indica che il simbolo è una matrice multidimensionale di FORTRAN.  
  
 `SymTagCallSite`  
 Indica che il simbolo rappresenta il sito di chiamata.  
  
 `SymTagInlineSite`  
 Indica che il simbolo rappresenta il sito inline.  
  
 `SymTagBaseInterface`  
 Indica che il simbolo è un'interfaccia di base.  
  
 `SymTagVectorType`  
 Indica che il simbolo è un tipo di vettore.  
  
 `SymTagMatrixType`  
 Indica che il simbolo è un tipo di matrice.  
  
 `SymTagHLSLType`  
 Indica che il simbolo è un tipo di lingua di alto livello dello Shader.  
  
## <a name="remarks"></a>Note  
 Tutti i simboli all'interno di un file di debug dispongono di un tag di identificazione che specifica il tipo del simbolo.  
  
 I valori di questa enumerazione vengono restituiti da una chiamata al [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metodo.  
  
 I valori di questa enumerazione vengono passati ai metodi seguenti per limitare l'ambito di ricerca per un tipo di simbolo specifico:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)