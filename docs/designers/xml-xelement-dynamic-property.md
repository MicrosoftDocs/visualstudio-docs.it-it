---
title: Xml (proprietà dinamica XElement)
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36b2100218267587e2ea5d38ad62f7ed28dbc102
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="xml-xelement-dynamic-property"></a>Xml (proprietà dinamica XElement)

Ottiene il contenuto XML non formattato dell'elemento.

## <a name="syntax"></a>Sintassi

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito

Oggetto <xref:System.String> che rappresenta il contenuto XML non formattato dell'elemento.

## <a name="remarks"></a>Note

Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> della classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con il parametro `SaveOptions` impostato su <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Vedere anche

- [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Valore](../designers/value-xelement-dynamic-property.md)