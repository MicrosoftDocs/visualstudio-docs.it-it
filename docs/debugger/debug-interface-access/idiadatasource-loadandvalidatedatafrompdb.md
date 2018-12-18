---
title: 'Idiadatasource:: Loadandvalidatedatafrompdb | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e298edac96b311e8e25e41698aaa3db539ec154
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Apre e verifica che il file del database (con estensione pdb) corrisponda alle informazioni di firma fornite e prepara il file con estensione PDB come un'origine dati di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdbPath`  
 [in] Il percorso del file PDB.  
  
 `pcsig70`  
 [in] Firma GUID per la verifica della firma di file con estensione pdb. File PDB solo [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e versioni successive dispongono di firme GUID.  
  
 `sig`  
 [in] La firma a 32 bit per la verifica della firma di file con estensione pdb.  
  
 `age`  
 [in] Valore di durata per verificare. La durata non corrisponde necessariamente a qualsiasi valore di tempo noto, viene utilizzato per determinare se un file con estensione PDB non è sincronizzato con un file .exe corrispondente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Impossibile aprire il file o il file di formato non è valido.|  
|E_PDB_FORMAT|Tentativo di accedere a un file con formato obsoleto.|  
|E_PDB_INVALID_SIG|Firma non corrisponde.|  
|E_PDB_INVALID_AGE|Non corrisponde all'età.|  
|E_INVALIDARG|Parametro non valido.|  
|E_UNEXPECTED|L'origine dati è già stata preparata.|  
  
## <a name="remarks"></a>Note  
 Un file con estensione PDB contiene valori sia di firma e di età. Questi valori vengono replicati nel file che corrisponde al file con estensione pdb .exe o DLL. Prima di preparare l'origine dati, questo metodo verifica che firma e la validità del file con estensione pdb denominato corrispondano ai valori specificati.  
  
 Per caricare un file con estensione pdb senza convalida, utilizzare il [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodo.  
  
 Per ottenere l'accesso per il processo di caricamento di dati (tramite un meccanismo di callback), utilizzare il [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
 Per caricare un file con estensione pdb direttamente dalla memoria, utilizzare il [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodo.  
  
## <a name="example"></a>Esempio  
  
```C++  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)