---
title: ArrayType | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ArrayType symbol
ms.assetid: 1d973a3a-2bde-46df-8625-85d519bb3cc9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ff8cefbd08f578d161d546f60a554364f47bb3d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="arraytype"></a>ArrayType
Una matrice è identificata da un `SymTagArray` simbolo.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente mostra altre proprietà valide per questo tipo di simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|`IDiaSymbol*`|Simbolo per il tipo di indice di matrice.|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|`DWORD`|ID del simbolo di tipo di indice di matrice.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Se la matrice è contrassegnata come const.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|Numero di elementi nella matrice.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Dimensione, in byte, di questa matrice.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo di compilando il contenitore.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo lessicale padre.|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|`DWORD`|Numero di dimensioni di una matrice multidimensionale di FORTRAN.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagArray` (uno del [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) valori).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Simbolo per il tipo di elemento di matrice.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID del simbolo di tipo di elemento di matrice.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Se la matrice è allineata|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Se la matrice è contrassegnata come volatile.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Dimensione](../../debugger/debug-interface-access/dimension.md)