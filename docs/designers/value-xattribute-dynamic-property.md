---
title: "Valore (proprietà dinamica XAttribute) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4807a84b9e1de5186e72cbe138f0f54e2f33525e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="value-xattribute-dynamic-property"></a>Valore (proprietà dinamica XAttribute)
Ottiene o imposta il valore dell'attributo XML.  
  
## <a name="syntax"></a>Sintassi  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Oggetto <xref:System.String> contenente il valore dell'attributo.  
  
## <a name="exceptions"></a>Eccezioni  
  
|Tipo di eccezione|Condizione|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|Durante l'impostazione, `value` è `null`.|  
  
## <a name="remarks"></a>Note  
 Questa proprietà dinamica è equivalente alla proprietà <xref:System.Xml.Linq.XAttribute.Value%2A> della classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ma supporta anche le notifiche delle modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Proprietà dinamiche della classe XAttribute](../designers/xattribute-class-dynamic-properties.md)   
 [Attributo](../designers/attribute-xelement-dynamic-property.md)