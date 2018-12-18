---
title: 'Idiaaddressmap:: Set_imageheaders | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 74556e2e67478cef9b495d3740dc910b62cc8293
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Set di intestazioni per abilitare la conversione dell'indirizzo virtuale relativo di immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 cbData  
 [in] Numero di byte di dati di intestazione. Deve essere `n*sizeof(IMAGE_SECTION_HEADER)` dove `n` è il numero di intestazioni di sezione nel file eseguibile.  
  
 dati]  
 [in] Matrice di `IMAGE_SECTION_HEADER` strutture da utilizzare come intestazioni di immagine.  
  
 originalHeaders  
 [in] Impostare su `FALSE` se le intestazioni di immagine dalla nuova immagine, `TRUE` se riflettono l'immagine originale prima di un aggiornamento. In genere, questa verrebbe impostata su `TRUE` solo in combinazione con chiamate al [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il `IMAGE_SECTION_HEADER` struttura viene dichiarata in Winnt. h e rappresenta il formato di intestazione di sezione immagine del file eseguibile.  
  
 Calcoli di indirizzo virtuale relativo variano a seconda di `IMAGE_SECTION_HEADER` valori. Il DIA recupera in genere, questi dal file di database (con estensione pdb) di programma. Se questi valori sono mancanti, il DIA non è in grado di calcolare indirizzi virtuali relativi e [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) restituisce `FALSE`. Il client deve quindi chiamare il [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodo per consentire i calcoli di indirizzo virtuale relativo dopo aver specificato le intestazioni mancanti di immagine dall'immagine stessa.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)