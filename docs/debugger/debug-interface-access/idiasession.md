---
title: IDiaSession | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b2791f318a921a25535d5e9a8f17e2c595f1f56
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasession"></a>IDiaSession
Fornisce un contesto di query per i simboli di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDiaSession`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Recupera l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli in questo archivio dei simboli. Questo è lo stesso valore passato per il `put_loadAddress` metodo.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Imposta l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli in questo archivio dei simboli. **Nota:** è importante chiamare questo metodo quando si ottengono un `IDiaSession` dell'oggetto e prima di iniziare a utilizzare l'oggetto.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Recupera un riferimento all'ambito globale.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera un enumeratore per tutte le tabelle incluse nell'archivio simboli.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera un enumeratore per tutti i simboli denominati posizioni statico.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera tutti gli elementi figlio di un identificatore padre specificato che corrispondano al tipo di nome e il simbolo.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera un tipo di simbolo specificato che contiene o vicino a, un indirizzo specificato.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Recupera un tipo di simbolo specificato che contiene o vicino a, un indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Recupera un tipo di simbolo specificato che contiene o vicino a, un indirizzo virtuale specificato (VA).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera il simbolo che contiene un token di metadati specificato.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Controlla se due simboli sono equivalenti.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera un simbolo dal relativo identificatore univoco.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera un tipo di simbolo specificato che contiene o vicino a un indirizzo virtuale relativo specificato e l'offset.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera un tipo di simbolo specificato che contiene o vicino a un indirizzo virtuale specificato e l'offset.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera un file di origine dal modulo e il nome.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera un file di origine dall'identificatore di file di origine.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Recupera i numeri di riga all'interno di un identificatore di file di modulo e di origine specificato.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera le righe che contengono un indirizzo specificato in un modulo specificato.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Recupera le righe che contengono un indirizzo virtuale relativo specificato in un modulo specificato.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Consente di trovare le informazioni sul numeri di riga per le righe contenute in un intervallo di indirizzi specificato.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera le righe in un modulo specificato dal numero di riga e file di origine.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera un'origine che è stata inserita nell'archivio simboli dai provider di attributo o di altri componenti del processo di compilazione.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Recupera una sequenza di debug di flussi di dati enumerata.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un determinato indirizzo.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un indirizzo virtuale specificato (VA).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni di numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo padre specificato.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni di numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo padre specificato e è contenuta all'interno dell'intervallo di indirizzi specificato.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni di numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo padre specificato e è contenuta all'interno di indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni di numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, dal simbolo padre specificato e è contenuta all'interno dell'indirizzo virtuale specificato (VA).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni sul numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, il numero di riga e file di origine specificata.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni sul numeri di riga di tutte le funzioni inline che corrisponde al nome specificato.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Restituisce un'enumerazione dei simboli per la variabile che il valore del tag specificato corrisponde alla funzione stub di tasti di scelta rapida del padre.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione di stub di tasti di scelta rapida padre specificato da un indirizzo virtuale relativo specificato.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Restituisce un'enumerazione dei simboli per i frame inline corrispondente al nome di funzione inline specificati.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Restituisce un'enumerazione dei simboli per il frame inline che corrispondono al percorso di origine specificato.|  
  
## <a name="remarks"></a>Note  
 È importante chiamare il [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metodo dopo aver creato il `IDiaSession` oggetto e il valore passato al `put_loadAddress` metodo deve essere diverso da zero, per qualsiasi proprietà dell'indirizzo virtuale (VA) di simboli da accessibile. L'indirizzo di caricamento proviene da qualsiasi programma caricato il file eseguibile in fase di debug. Ad esempio, è possibile chiamare la funzione Win32 `GetModuleInformation` per recuperare l'indirizzo di carico per il file eseguibile, dato un handle al file eseguibile.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere il `IDiaSession` interfaccia come parte di un'inizializzazione generale di DIA SDK.  
  
```C++  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [File exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)