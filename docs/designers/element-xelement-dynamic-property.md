---
title: Elemento (proprietà dinamica XElement)
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0bdcb6f4524f4f2db7f119319cbb38a09f83f201
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="element-xelement-dynamic-property"></a>Elemento (proprietà dinamica XElement)

Ottiene un indicizzatore usato per recuperare l'istanza dell'elemento figlio che corrisponde al nome espanso specificato.

## <a name="syntax"></a>Sintassi

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito

Indicizzatore del tipo `XElement Item(String expandedName)`. Questo indicizzatore accetta un parametro del nome espanso e restituisce l'oggetto <xref:System.Xml.Linq.XElement> corrispondente o `null` se non esiste nessun elemento con il nome specificato.

## <a name="remarks"></a>Note

Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Element%2A> della classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>Vedere anche

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Elementi](../designers/elements-xelement-dynamic-property.md)