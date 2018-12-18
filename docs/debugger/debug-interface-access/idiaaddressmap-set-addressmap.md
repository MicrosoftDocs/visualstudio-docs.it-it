---
title: 'Idiaaddressmap:: Set_addressmap | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 681e0bae46497d9b581e89340069937370831777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Fornisce un mapping di indirizzi per supportare le traduzioni di layout di immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cbData`  
 [in] Il numero di elementi di `data` parametro.  
  
 `data[]`  
 [in] Matrice di [struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) strutture che definiscono il mapping per la conversione.  
  
 `imagetoSymbols`  
 [in] `TRUE` se il `data` parametro definisce una mappa dal layout dell'immagine di nuovo il layout originale (come descritto dai simboli di debug). `FALSE`Se `data` è una mappa per il nuovo layout dell'immagine ricavato il layout originale.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il DIA recupera in genere, le mappe di traduzione di indirizzo dal file di database (con estensione pdb) di programma. Se questi valori sono mancanti, il [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metodo viene chiamato due volte, una volta con il `imagetoSymbols` parametro impostato su `TRUE` e una volta con il `imagetoSymbols` parametro impostato su `FALSE`. Conversioni degli indirizzi della mappa non venga abilitate usando il [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metodo a meno che non vengono fornite entrambi mappe di traduzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)