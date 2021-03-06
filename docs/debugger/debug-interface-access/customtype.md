---
title: CustomType | Microsoft Docs
description: Trovare informazioni di riferimento sul tipo di simbolo CustomType (SymTagCustomType) in Visual Studio Debug Interface Access SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CustomType symbol
ms.assetid: 1b66bc0a-7979-416f-bf7f-e5df91584c91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6912567ac7dedc6885d990dd96f21c41a1867292
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865482"
---
# <a name="customtype"></a>CustomType
I tipi definiti dal fornitore (tipi specifici del compilatore) sono identificati da un `SymTagCustomType` simbolo.

## <a name="properties"></a>Proprietà
 Nella tabella seguente vengono illustrate proprietà valide aggiuntive per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|`DWORD`|Identificatore dell'OEM.|
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|`DWORD`|ID interno dell'OEM.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCustomType` uno dei valori di [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Primo tipo a cui fa riferimento il simbolo di tipo personalizzato.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID del simbolo del tipo.|
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|`IDiaSymbol**`|Matrice di tutti i tipi a cui fa riferimento il simbolo di tipo personalizzato.|

## <a name="see-also"></a>Vedi anche
- [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)