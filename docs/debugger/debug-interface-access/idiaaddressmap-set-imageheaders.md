---
title: 'Idiaaddressmap:: Set_imageheaders | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51b68475b9ef0374f95febabc2997524bfd61259
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
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
 [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)