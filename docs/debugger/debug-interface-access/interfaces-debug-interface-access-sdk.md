---
title: Interfacce (Debug Interface Access SDK) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 584c7337ae50f85f95f063a47787b8a4be37c9fb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfacce (Debug Interface Access SDK)
I metodi sono elencati in ordine alfabetico in ogni interfaccia nella tabella del contenuto e nella pagina dell'interfaccia nell'ordine Vtable.  
  
## <a name="in-this-section"></a>In questa sezione  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Consente di controllare come il DIA SDK calcola virtuali e relativi indirizzi virtuali per gli oggetti di debug.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Avvia l'accesso a un'origine dei simboli di debug.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Fornisce l'accesso ai record in un flusso di dati di debug.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Enumera i vari flussi debug contenuti nell'origine dati.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Enumera i vari elementi di dati di frame contenuti nell'origine dati.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Consente di enumerare le varie origini inserite contenute nell'origine dati.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Enumera i numeri di riga diversi contenuti nell'origine dati.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Enumera i vari contributi sezione contenuti nell'origine dati.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Enumera i vari segmenti contenuti nell'origine dati.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Enumera i vari file di origine contenuti nell'origine dati.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Enumera i vari stack frame disponibili.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Enumera i vari simboli contenuti nell'origine dati.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Enumera i indirizzo i simboli diversi contenuti nell'origine dati.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Enumera le varie tabelle contenute nell'origine dati.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Espone i dettagli di uno stack frame.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Espone i dettagli degli offset di posizione e la memoria base del modulo o immagine.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Accede a codice sorgente del programma archiviate nell'origine dati DIA.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Si accede alle informazioni che descrive il processo di mapping da un blocco di byte di testo da un'immagine a un numero di riga di file di origine.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Riceve i callback dal simbolo DIA procedura di individuazione, consentendo un'interfaccia utente per creare report sullo stato del tentativo di percorso.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Riceve i callback dal simbolo DIA procedura di individuazione, che consente le restrizioni da imporre il processo di individuazione.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Consente di leggere le proprietà di un set di proprietà DIA permanente.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Consente a un'applicazione client fornire i byte di un file eseguibile come specificato dalla posizione del file.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Consente a un'applicazione client fornire i byte di un file eseguibile come specificato da un indirizzo virtuale relativo.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Recupera i dati che descrivono un contributo di sezione, vale a dire un blocco di memoria contiguo ha contribuito all'immagine da un modulo.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Mappa i dati del numero di sezione ai segmenti dello spazio degli indirizzi.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Fornisce un contesto di query per i simboli di debug.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Rappresenta un file di origine.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Espone le proprietà di uno stack frame.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Fornisce metodi per eseguire uno stack procedono utilizzando il file PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Gestisce il contesto di stack tra le chiamate del [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metodo.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Facilita la verifica dello stack utilizzando il file di programma debug (PDB) di database.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Vengono descritte le proprietà di un'istanza del simbolo.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Enumera una tabella di origine dati DIA.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Descrive le enumerazioni e strutture utilizzate da varie interfacce di DIA SDK.  
  
 [Costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Vengono descritte le costanti disponibili in DIA SDK.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)