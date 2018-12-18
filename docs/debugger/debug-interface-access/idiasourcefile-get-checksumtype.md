---
title: 'Idiasourcefile:: Get_checksumtype | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f34e840dc6389b721610251c592480afbdda5f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Recupera il tipo di checksum.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il tipo di checksum.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il tipo di checksum è un valore che può essere mappato a un algoritmo di checksum. Ad esempio, il formato di file PDB standard in genere può avere uno dei valori seguenti:  
  
|Tipo di checksum|Etichetta CryptoAPI|Descrizione|  
|-------------------|---------------------|-----------------|  
|0|\<Nessuno >|Checksum non presente.|  
|1|`CALG_MD5`|checksum generato con l'algoritmo hash MD5.|  
|2|`CALG_SHA1`|checksum generato con l'algoritmo hash SHA1.|  
  
 Il `CryptoAPI` etichette sono compresi il `ALG_ID` enumerazione. Per ulteriori informazioni su algoritmi di hash, consultare il `CryptoAPI` sezione di Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Per ottenere i byte di checksum effettivo del file di origine, chiamare il [idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)